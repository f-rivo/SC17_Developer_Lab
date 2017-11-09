
<table style="width:100%">
  <tr>
    <th width="100%" colspan="5"><h2>SC17 Xilinx Developer Lab</h2></th>
  </tr>
  <tr>
    <td width="20%" align="center"><a href="README.md">Introduction</a></td>
    <td width="20%" align="center"><a href="SETUP.md">Connecting to your F1 instance</a></td> 
    <td width="20%" align="center"><a href="FFMPEG_Lab.md"><b>Experiencing F1 acceleration</b></a></td>
    <td width="20%" align="center"><a href="IDCT_Lab.md">Developing F1 applications</a></td>
    <td width="20%" align="center"><a href="WRAP_UP.md">Wrapping-up</td>
  </tr>
</table>

---------------------------------------

## Experiencing F1 Acceleration

In this module you will experience the acceleration potential of AWS F1 instances by using ```ffmpeg``` to encode 20 seconds of raw YUV 1920x1080 video, first using the libx265 codec and then a HEVC encoder optimized for F1 FPGAs. 

```ffmpeg``` is a very popular framework providing very fast video and audio converters. The ```ffmpeg``` code is open-source and allows for the addition of custom plugins. For this lab, a custom plugin has been created to transparently use the NGCodec HEVC encoder running on AWS F1.  

![](images/ffmpeg_lab/ffmpeg_lab.png)

Users can switch between the libx265 software codec and the F1-accelerated implementation by simply changing a parameter on the ```ffmpeg``` command line. The plugin uses OpenCL API calls to write video frames to the FPGA, execute the encoder and read back the compressed video.

The HEVC encoder is provided courtesy of **NGCodec** [(www.ngcodec.com)](www.ngcodec.com).

## Running the lab

* Open a new terminal by right-clicking anywhere in the Desktop area and selecting **Open Terminal**.
* Navigate to the FFmpeg lab directory.
```bash
cd ~/SC17_Developer_Lab/ffmpeg
```

* Source the FFmpeg and SDAccel runtime environments.
```bash
sudo sh
source ./ffsetup.sh
source /opt/Xilinx/SDx/2017.1.rte/setup.sh
```

* Encode using the libx265 software codec running on the CPU.
```bash
./ffmpeg -f rawvideo -pix_fmt yuv420p -s:v 1920x1080 -i /home/centos/vectors/crowd8_420_1920x1080_50.yuv -an -frames 1000 -c:v libx265 -preset medium -g 30 -q 40 -f hevc -y ./crowd8_420_1920x1080_50_libx265_out0_qp40.hevc
```

The encoder will finish with a message similar to this one: \
*frame=500 **fps=9.0** q=-0.0 **Lsize=19933kB** time=00:00:19.92 bitrate=8197.4kbits/s **speed=0.358x*** 

> **fps** measures the performance of the encoder measured in processed frames per second. \
**size** measures the size the compressed output file. \
**speed** measures the ratio of video time to encoding time.
 
* Load the HEVC encoder FPGA binary in the F1 instance. 
```bash
fpga-load-local-image -S 0 -I agfi-0015437e933b3e725
```

* Encode using the NGCodec HEVC encoder running on the F1 FPGA.
```bash
./ffmpeg -f rawvideo -pix_fmt yuv420p -s:v 1920x1080 -i /home/centos/vectors/crowd8_420_1920x1080_50.yuv -an -frames 1000 -c:v xlnx_hevc_enc -psnr -g 30 -global_quality 40 -f hevc -y ./crowd8_420_1920x1080_50_NGcodec_out0_g30_gq40.hevc 
```

The encoder will finish with a message similar to this one: \
*frame=500 **fps=52** q=-0.0 LPSNR=Y:inf U:inf V:inf \*:inf **size=17580kB** time=00:00:20.00 bitrate=7200.9kbits/s **speed=2.08x*** 

<br>

* The table below summarizes the performance of both encoders:

|                           | HEVC encoding on CPU | HEVC encoding on F1  |
| :------------------------ |-------------:| -------:|
| performance               | 9 fps        | 52 fps  |
| speed vs real-time        | 0.358 x      | 2.08 x  |
| duration                  | 55.6 sec     | 9.6 sec |
| compressed file size      | 19.9 Mb      | 17.5 Mb |



## Conclusion

AWS F1 instances with Xilinx FPGAs can provide significant performance improvements over CPUs. The HEVC encoder running on F1 is **5.7x** faster than the libx265 codec running on the CPU. It also provides better compression without sacrificing quality.

Multiple instances of the NGCodec encoder could be loaded in the FPGA, allowing parallel processing of multiple video streams and easily delivering more than a 10x increase in performance/$ over a CPU-based solution. 

It is possible to use F1 to accelerate popular frameworks such as ```ffmpeg```. This is a very powerful proposition at it allows end-users to keep working with their preferred tools and APIs while transparently benefiting from acceleration.

In addition to video transcoding, F1 instances are very well suited to accelerate compute intensive workloads such as: genomics, financial analytics, big data analytics, security or machine learning.

Now that you have experienced the performance potential of AWS F1 instances, the next lab will introduce you to the SDAccel IDE and how to develop, profile and optimize an F1 application.

---------------------------------------

<p align="center"><b>
Start the next module: <a href="IDCT_Lab.md">1. Developing, profiling and optimizing F1 applications with SDAccel</a>
</b></p>

