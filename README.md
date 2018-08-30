Error: 
In file included from /usr/local/cuda/include/channel_descriptor.h:62:0,
                 from /usr/local/cuda/include/cuda_runtime.h:90,
                 from /usr/include/cudnn.h:64,
                 from /home/devinda/libs/pytorch/aten/src/ATen/cudnn/cudnn-wrapper.h:3,
                 from /home/devinda/libs/pytorch/aten/src/ATen/native/cudnn/AffineGridGenerator.cpp:28:
/usr/local/cuda/include/cuda_runtime_api.h:1699:101: error: use of enum ‘cudaDeviceP2PAttr’ without previous declaration
 extern __host__ __cudart_builtin__ cudaError_t CUDARTAPI cudaDeviceGetP2PAttribute(int *value, enum cudaDeviceP2PAttr attr, int srcDevice, int dstDevice);
                                                                                                     ^~~~~~~~~~~~~~~~~
/usr/local/cuda/include/cuda_runtime_api.h:2947:102: error: use of enum ‘cudaFuncAttribute’ without previous declaration
 extern __host__ __cudart_builtin__ cudaError_t CUDARTAPI cudaFuncSetAttribute(const void *func, enum cudaFuncAttribute attr, int value);
                                                                                                      ^~~~~~~~~~~~~~~~~
In file included from /usr/local/cuda/include/channel_descriptor.h:62:0,
                 from /usr/local/cuda/include/cuda_runtime.h:90,
                 from /usr/include/cudnn.h:64,
                 from /home/devinda/libs/pytorch/aten/src/ATen/cudnn/cudnn-wrapper.h:3,
                 from /home/devinda/libs/pytorch/aten/src/ATen/native/cudnn/AffineGridGenerator.cpp:28:
/usr/local/cuda/include/cuda_runtime_api.h:5816:92: error: use of enum ‘cudaMemoryAdvise’ without previous declaration
 extern __host__ cudaError_t CUDARTAPI cudaMemAdvise(const void *devPtr, size_t count, enum cudaMemoryAdvise advice, int device);
                                                                                            ^~~~~~~~~~~~~~~~
/usr/local/cuda/include/cuda_runtime_api.h:5873:98: error: use of enum ‘cudaMemRangeAttribute’ without previous declaration
 extern __host__ cudaError_t CUDARTAPI cudaMemRangeGetAttribute(void *data, size_t dataSize, enum cudaMemRangeAttribute attribute, const void *devPtr, size_t count);
                                                                                                  ^~~~~~~~~~~~~~~~~~~~~
/usr/local/cuda/include/cuda_runtime_api.h:5910:102: error: use of enum ‘cudaMemRangeAttribute’ without previous declaration
 extern __host__ cudaError_t CUDARTAPI cudaMemRangeGetAttributes(void **data, size_t *dataSizes, enum cudaMemRangeAttribute *attributes, size_t numAttributes, const void *devPtr, size_t count);
                                                                                                      ^~~~~~~~~~~~~~~~~~~~~
caffe2/CMakeFiles/caffe2_gpu.dir/build.make:1499: recipe for target 'caffe2/CMakeFiles/caffe2_gpu.dir/__/aten/src/ATen/native/cudnn/AffineGridGenerator.cpp.o' failed
make[2]: *** [caffe2/CMakeFiles/caffe2_gpu.dir/__/aten/src/ATen/native/cudnn/AffineGridGenerator.cpp.o] Error 1
make[2]: *** Waiting for unfinished jobs....
CMakeFiles/Makefile2:1393: recipe for target 'caffe2/CMakeFiles/caffe2_gpu.dir/all' failed
make[1]: *** [caffe2/CMakeFiles/caffe2_gpu.dir/all] Error 2
Makefile:140: recipe for target 'all' failed
make: *** [all] Error 2
Failed to run 'bash ../tools/build_pytorch_libs.sh --use-cuda --use-nnpack nccl caffe2 libshm gloo THD c10d'

solution:
copied from: https://devtalk.nvidia.com/default/topic/1025801/cudnn-test-did-not-pass/

 open the file:
/usr/include/cudnn.h

And I changed the line:
#include "driver_types.h"

to:
#include <driver_types.h>
