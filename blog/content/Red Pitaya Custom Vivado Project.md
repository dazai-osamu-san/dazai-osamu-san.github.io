---
date: '2025-12-27T23:48:25+05:30'
draft: false
title: "Red Pitaya Custom Vivado Project Creation"
---

This probably will end up a series of posts on the road blocks I hit while working on the Red Pitaya. I am using the STEM-Lab 125-14 variant. 

I also want to mention that Pavel Demin has done an amazing job at simplifying this whole process, I like taking on challenges so I went my own way.

The motivation behind this post being I couldn't find a minimal way to write quick custom FPGA bitstreams without the extra baggage presented by the default vivado project.
In many of the cases you also do end up needing the PS for some reason like setting coefficients etc.
Just to utilize the PL part to do simple tasks like ADC -> DAC loopbacks, testing out filters on hardware for response verification, turned out a bit more annoying.  
Opening the default project on different Vivado version causes the first issue. It's mentioned in the official documentation that you require linux and a specific Vivado version, but you can pretty easily get everything running on windows with a little bit of TCL scripting and editing the right TCL files by changing the versions. Just make sure to update IPs to latest version.

Second issue I faced is that this default project is not intuitively arranged, the Top file does not correlate to the bd as it generally would in a typical Vivado project. It is only used to instantiate the zynq PS and the XADC IP.
I tried to reverse engineering the project and came up with this.

Now trying to only remove certain parts to remove the extra stuff did not end well for me. So I went on a journey to strip it down of everything till only the Zynq IP, that also did not end well due to the default project structure.

Finally I tried downloading the board files and start a project from scratch in Vivado and selecting the board in the wizard.
It somehow does not instantiate the Zynq IP in the same way the original project does and many of the essentials were not enabled and I tried too long to find the right memory (RAM) part in the list. While messing around in the ZYNQ PS wizard I found that it allows you to save configuration to a TCL file.
So I opened a clean original project and exported the ZYNQ PS configuration and started a new Vivado project but still select the red Pitaya board in the new project wizard and when you create the ZYNQ PS IP there is an option to import a configuration aswell, just select the file you saved before to apply the same configuration and disable and enable what you want now.
So you have a clean project in the typical Vivado structure. Nice!

The people at Red Pitaya have a good job at unifying their entire family into one repo but for the one who wants full program control it becomes a bit of a puzzle.

Finally for the board constraints for these configurations you need to look around a bit aswell. They are split across two files, you need to pick out the main constraints that you need.

To those who are going to work with the main ADCs you have to do some clock magic which I aim to cover once I fully figure that out. 

That's it for this post I hope you find it helpful.
