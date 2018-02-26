cmake_minimum_required(VERSION 2.7)

SET(COMPILE_DEFINITIONS -Werror)

include_directories(${PROJECT_SOURCE_DIR}/host_applications/linux/libs/bcm_host/include)
include_directories(${PROJECT_SOURCE_DIR}/host_applications/linux/apps/raspicam/)
include_directories(${PROJECT_SOURCE_DIR}/host_applications/linux/libs/sm)
include_directories(/opt/vc/include)
include_directories(/usr/local/include)
link_directories(/opt/vc/lib)
link_directories(/usr/local/lib)

set (COMMON_SOURCES
   RaspiCamControl.c
   RaspiCLI.c
   RaspiPreview.c)
   
add_executable(raspivid   ${COMMON_SOURCES} RaspiVid.c)
add_executable(raspipublisher   ${COMMON_SOURCES} RaspiPublisher.c)

set (MMAL_LIBS mmal_core mmal_util mmal_vc_client pthread)
target_link_libraries(raspivid   ${MMAL_LIBS} vcos bcm_host)
target_link_libraries(raspipublisher   ${MMAL_LIBS} vcos bcm_host srsrtmp stdc++)
