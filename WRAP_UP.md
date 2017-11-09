<table style="width:100%">
  <tr>
    <th width="100%" colspan="5"><h2>SC17 Xilinx Developer Lab</h2></th>
  </tr>
  <tr>
    <td width="20%" align="center"><a href="README.md">Introduction</a></td>
    <td width="20%" align="center"><a href="SETUP.md">1. Connecting to your F1 instance</a></td> 
    <td width="20%" align="center"><a href="FFMPEG_Lab.md">2. Experiencing F1 acceleration</a></td>
    <td width="20%" align="center"><a href="IDCT_Lab.md">3. Developing F1 applications</a></td>
    <td width="20%" align="center"><b>4. Wrapping-up</b></td>
  </tr>
</table>

---------------------------------------

## Wrap-Up and Next Steps

You have successfully completed the SC17 Xilinx Developer Lab. Congratulations!

Please now follow these steps to close your RDP session and stop your instance.

* Click the 'X' icon in your RDP client window.

It is important to always stop or terminate AWS EC2 instances when you are done using them. This is a recommended best practice to avoid unwanted charges.

* On your local machine, return to your browser and to the tab showing the **EC2 Console** and the details of your running instance.
   * If necessary, use the link which was emailed to you to return to the proper web page.
* In the **EC2 Console**, click the **Actions** button, then select **Instance State** and then **Stop**.

> Note: permission to **Terminate** instances was disabled for all user accounts of this Developer Lab to prevent accidental terminations.

## Next steps

To take your AWS F1 and SDAccel experience further, we recommend the following resources:

| Resource | Title                       | Description  |
| -------- |---------------------------- | ----- |
| F1 App | **Test-drive Xilinx GoogLeNet / ResNet on AWS F1** | See for yourself how Xilinx can accelerate machine learning image classification on AWS F1. [**Link**](https://www.xilinx.com/applications/megatrends/machine-learning/aws-f1-test-drive.html) |
| Video  | **Learn more about the SDAccel OpenCL application structure** | This video introduces the host code and kernel elements of an OpenCL application and explains how they map to FPGA accelerators. [**Link**](https://www.xilinx.com/video/hardware/opencl-application-structure.html) |
| Tutorial | **Get started on F1 with the SDAccel C/OpenCL flow** | This guide takes new users through all the steps required build a first working application on F1. [**Link**]() |
| Tutorial | **Get started on F1 with the SDAccel RTL flow** | This guide is targeted to developers with prior hardware design experience and legacy RTL designs. [**Link**](https://github.com/Xilinx/SDAccel_Examples/wiki/Getting-Started-on-AWS-F1-with-SDAccel-and-RTL-Kernels) |
| Examples | **Browse Github examples** | Explore a repository of more than 80 examples to learn more about the SDAccel OpenCL programming model. [**Link**](https://github.com/Xilinx/SDAccel_Examples) |






