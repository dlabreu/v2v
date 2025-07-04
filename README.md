V2V Disk Conversion for Kubevirt/OpenShift Virtualization

This README.md file provides an overview of the Virtual-to-Virtual (V2V) Disk Conversion Project, designed to facilitate the migration of virtual machine disks from various hypervisor formats into a format compatible with Kubevirt and OpenShift Virtualization environments.
Introduction

Migrating existing virtual machines (VMs) to a cloud-native virtualization platform like Kubevirt or OpenShift Virtualization often requires converting their disk images into a compatible format. This project addresses this need by providing a streamlined solution for converting common VM disk types to QCOW2, the preferred disk image format for these container-native virtualization platforms.
Project Goal

The primary goal of this project is to enable seamless importation of virtual machine disks into Kubevirt/OpenShift Virtualization by converting them into the QCOW2 format, ensuring compatibility and optimal performance within the Kubernetes ecosystem.
Supported Source Disk Formats

This conversion tool supports a variety of widely used virtual machine disk formats as input:

    RAW: Raw disk images, which are direct byte-for-byte copies of a disk.

    VMDK (Virtual Machine Disk): The native disk format for VMware products (e.g., vSphere, Workstation, Fusion).

    VDI (Virtual Disk Image): The native disk format for Oracle VirtualBox.

    VHDX (Virtual Hard Disk v2): An updated virtual hard disk format used by Microsoft Hyper-V, offering larger capacities and resilience features compared to VHD.

Target Disk Format: QCOW2

The target format for all conversions is QCOW2 (QEMU Copy-On-Write Version 2).
Why QCOW2 for Kubevirt/OpenShift Virtualization?

QCOW2 is chosen as the target format for several key reasons:

    Efficiency: It supports copy-on-write, allowing for smaller initial disk images and efficient storage of snapshots.

    Features: It includes features like compression, encryption, and backing files, which are beneficial for managing VM images.

    Kubevirt Compatibility: QCOW2 is the native and most optimized disk format for QEMU/KVM, which forms the core of Kubevirt's virtualization capabilities. It integrates seamlessly with Kubevirt's DataVolume and CDI (Containerized Data Importer) components for efficient data transfer and management.

How It Works (High-Level)

The conversion process typically involves:

    Input: Providing the source VM disk image in one of the supported formats (RAW, VMDK, VDI, VHDX).

    Conversion Engine: Utilizing underlying tools (e.g., qemu-img) to perform the actual format transformation. This step handles the intricacies of each source format and converts it to the QCOW2 specification.

    Output: Generating a QCOW2 disk image file.

    Import Readiness: The resulting QCOW2 file is then ready to be imported into Kubevirt/OpenShift Virtualization using their respective data import mechanisms (e.g., creating a DataVolume with a source pointing to the converted image).

Key Features and Benefits

    Broad Compatibility: Supports major virtual disk formats, covering a wide range of existing VM environments.

    Kubevirt/OpenShift Virtualization Ready: Produces disk images directly consumable by these platforms.

    Simplified Migration: Reduces manual effort and potential errors during VM migration.

    Optimized Performance: QCOW2 ensures efficient disk operations within the Kubevirt environment.

Usage / Getting Started

(This section would typically include specific commands or steps for using the conversion tool. For a conceptual README, we describe the general flow.)

To use this project, you would generally:

    Obtain the source virtual disk file from your existing hypervisor.

    Execute the conversion utility, specifying the input file and desired output location for the QCOW2 image.

    Once converted, use Kubevirt's DataVolume or cdi-upload tools to upload the QCOW2 image into your Kubernetes cluster, making it available for new or existing VirtualMachine instances.

Contributing

We welcome contributions! Please refer to our CONTRIBUTING.md for guidelines on how to submit issues, features, or pull requests.
License

This project is licensed under the [Specify Your License Here, e.g., Apache 2.0, MIT License] - see the LICENSE file for details. "Still need to decided before push into main branch"
