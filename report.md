# Report: Analysis of Multi-Stream YOLO Inference Architectures Using Nvidia's Triton Inference Server

This report provides a comparison of Nvidia's DeepStream Service Maker (Python Alpha) and the Roboflow Inference Pipeline for multi-stream YOLO inference.

## Nvidia DeepStream Service Maker (Python Alpha)

### https://docs.nvidia.com/metropolis/deepstream/dev-guide/text/DS_service_maker_python.html

- **Focus**: Designed to simplify video analytics and object detection pipelines using Nvidia's DeepStream SDK, built on top of Gstreamer a C++ library for multiple stream management.
- **Features**:
  - **Multi-Stream Support**: Built natively for handling multiple input streams with high throughput.
  - **Triton Integration**: First Class integration with Nvidia Triton for model inference.

## Roboflow Inference Pipeline

### https://inference.roboflow.com/enterprise/stream_management_api/

- **Focus**: Built in python, Primarily tailored for developers deploying computer vision models, with a focus on usability and abstraction.
- **Features**:
  - **Model Deployment**: Streamlines the deployment of pre-trained models, including YOLO variants.
  - **Ease of Use**: Abstracts away lower-level configuration.

## Key Differences

1. **Global Differences**:

   - DeepStream Service Maker is geared towards advanced users and developers familiar with deepstream sdk primitives with a focus on optimizing multi-stream video analytics workflows.
   - DeepStream Service Maker for python is still in alpha, and while it's free it's not open source.
   - with 100% focus on python Inference Pipeline caters to users seeking good abstractions and quick deployment of computer vision models, offers the best performance available for pure python implementation.
   - Inference Pipeline (full open source) offers basic multi stream functionality, but for robust streaming operations (start, stop...) and dynamic stream addition requires a multi-process approach for the best performance and scalability.

2. **Performance**:

   - Built in C++, DeepStream is optimized for multi-stream performance on Nvidia GPUs, leveraging low-level optimizations.
   - Inference Pipeline offers great performance for python, but requires additional custom logic for leveraging multi-stream operations as sited in Developer Notes on the link provided earlier.

3. **Customization**:
   - DeepStream offers customization through Python APIs but requires in a lot of times config files, not 100% config via code
   - Roboflow offers great customizatoins for our computer vision needs.

In summary, Nvidia DeepStream Service Maker is ideal for high-performance but requires a steap learning curve and yml based configs (not 100% python config), and it's not open source, the python sdk layer is still in alpha, with very few documentations available. All this make it less ideal for our usecase. On the other hand Roboflow Inference Pipeline is open source offering the basis for implementing your own custom stream management on top, with great documentation and a 100% python approach, which make it the selected approach for this report.