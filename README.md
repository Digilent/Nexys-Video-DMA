Nexys Video DMA Demo
====================

Description
-----------

This project demonstrates how to use the Nexys Video's Audio Codec and RAM to record samples of audio and play them back. Vivado is used to build the demo's hardware platform, and Vitis is used to program the bitstream onto the board and to build and deploy a C application.

To use this demo, the Nexys Video must be connected to a computer over MicroUSB, which must be running a serial terminal such as Tera Term or PuTTY.

The audio demo records a 5 second sample from microphone(J7) or line in (J8) and plays it back on headphone out(J5) or line out (J6). Recording and playback are controlled by the user push buttons, as in the table below.

|  Button  | Function             |
| -------- | -------------------- |
|  BTNL    |  play on line out    |
|  BTNU    |  record from mic in  |
|  BTND    |  play on hph out     |
|  BTNR    |  record from line in |


Requirements
------------
* **Nexys Video**
* **Vivado and Vitis 2020.1 Installations**
* **Serial Terminal Emulator**
* **MicroUSB Cable**
* **Audio Source and Sink, such as Audio Cables, a Microphone, and/or a Speaker**

Demo Setup
----------

1. Download the most recent release ZIP archives from the repo's [releases page](https://github.com/Digilent/Nexys-Video-DMA/releases). These files are called "Nexys-Video-DMA-hw.xpr.zip" and "Nexys-Video-DMA-sw.ide.zip". The -hw archive contains an exported XPR project file and associated sources for use with Vivado. The -sw archive contains exported project files for use with Vitis. Both of these files contain the build products of the associated tool.

  Note: Do not extract the downloaded -sw archive.
  
2. Open Vitis 2020.1. Choose an empty folder as the *Workspace* to launch into.
3. With Vitis opened, click the **Import Project** button, under **PROJECT** in the welcome screen.
4. Choose *Vitis project exported zip file* as the Import type, then click **Next**.
5. **Browse** for the downloaded -sw archive, and **Open** it.
6. Make sure that all boxes are checked in order to import each of the projects present in the archive will be imported, then click **Finish**.
7. Plug in an audio source and sink.
8. Open a serial terminal application (such as [TeraTerm](https://ttssh2.osdn.jp/index.html.en) and connect it to the Nexys Video's serial port, using a baud rate of 115200.
9. In the *Assistant* pane at the bottom left of the Vitis window, right click on the project marked `[System]`, and select **Run** -> **Launch Hardware**. When the demo is finished launching, messages will be able to be seen through the serial terminal, and the demo can be used as described in this document's *Description* section, above.

To later make changes to the Vivado project and update the hardware platform in Vitis:

1. Extract the downloaded -hw archive.
2. Open Vivado 2020.1.
3. Open the XPR project file, found at \<archive extracted location\>/hw/hw.xpr, included in the extracted hardware release, in Vivado 2020.1.
4. Make any desired modifications and regenerate the bitstream.
5. Use the File > Export > Export Hardware option to export a hardware platform (XSA) file to a memorable location. Specify the **Fixed** and **Include bitstream** options, as this is a baremetal project and will be used to program the board through Vitis.
6. In Vitis, right click on the *Platform* project, select **Update Hardware Specification**, then navigate to and select the exported XSA for import.
7. Rebuild and relaunch the application.

Next Steps
----------
This demo can be used as a basis for other projects by modifying the hardware platform in the Vivado project's block design or by modifying the application project in Vitis.

Check out the Nexys Video's [Resource Center](https://reference.digilentinc.com/reference/programmable-logic/nexys-video/start) to find more documentation, demos, and tutorials.

For technical support or questions, please post on the [Digilent Forum](forum.digilentinc.com).

Additional Notes
----------------
For more information on how this project is version controlled, refer to the [digilent-vivado-scripts](https://github.com/digilent/digilent-vivado-scripts) and [digilent-vitis-scripts](https://github.com/digilent/digilent-vitis-scripts) repositories.
