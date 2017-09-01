cmake_minimum_required(VERSION 3.5)
project(GLES_Test)

include_directories( External/Include )
include_directories( Common/Include )
include_directories(ParticleSystemTransformFeedback)

#find_library( OPENGLES3_LIBRARY GLESv2 "OpenGL ES v3.0 library")
#find_library( EGL_LIBRARY EGL "EGL 1.4 library" )
#find_library(X11 X11 "linux window library")

#set(EGL_LIBRARY "/opt/Imagination/PowerVR_Graphics/PowerVR_SDK/SDK_2017_R1/Builds/Linux/x86_64/Lib/libEGL.so")
set(EGL_LIBRARY "/opt/Imagination/PowerVR_Graphics/PowerVR_Tools/PVRVFrame/Library/Linux_x86_64/libEGL.so")
set(OPENGLES3_LIBRARY "/opt/Imagination/PowerVR_Graphics/PowerVR_SDK/SDK_2017_R1/Builds/Linux/x86_64/Lib/libGLESv2.so")
#set(OPENGLES3_LIBRARY "/opt/Imagination/PowerVR_Graphics/PowerVR_Tools/PVRVFrame/Library/Linux_x86_64/libGLESv2.so")

#set(LD_LIBRARY_PATH "/opt/Imagination/PowerVR_Graphics/PowerVR_Tools/PVRVFrame/Library/Linux_x86_64")

add_subdirectory(Common)
set(SRC_FILES Hello_Triangle Example_6_3 Example_6_6 MapBuffers VertexArrayObjects VertexBufferObjects Instancing
        Simple_VertexShader MipMap2D Simple_Texture2D Simple_TextureCubemap TextureWrap MultiTexture
        MRTs Noise3D ParticleSystem Shadows TerrainRendering)

foreach(SourceFile ${SRC_FILES})
    add_executable(${SourceFile} ${SourceFile}.c)
    target_link_libraries(${SourceFile} Common)
#    target_link_libraries(HelloTest "/opt/Imagination/PowerVR_Graphics/PowerVR_Tools/PVRVFrame/Library/Linux_x86_64/libEGL.so")
#    target_link_libraries(HelloTest "/opt/Imagination/PowerVR_Graphics/PowerVR_SDK/SDK_2017_R1/Builds/Linux/x86_64/Lib/libGLESv2.so")
#    target_link_libraries(HelloTest X11)
endforeach()

add_executable(PSTF ParticleSystemTransformFeedback/ParticleSystemTransformFeedback.c ParticleSystemTransformFeedback/Noise3D.c)
target_link_libraries(PSTF Common)










