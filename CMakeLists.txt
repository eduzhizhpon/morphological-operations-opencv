cmake_minimum_required(VERSION 3.0.0)
project(mo-opencv VERSION 0.1.0)

set (CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE "../bin")
add_compile_definitions(
    _SILENCE_EXPERIMENTAL_FILESYSTEM_DEPRECATION_WARNING
)

include(CTest)
enable_testing()

find_package( OpenCV REQUIRED )
find_package( Threads REQUIRED )
find_package(Qt5 COMPONENTS Widgets REQUIRED)
include_directories( ${OpenCV_INCLUDE_DIRS} )

# Create a list with all .cpp source files
set( project_sources
   "source_files/main.cpp"
   "source_files/morphological-operation.cpp"
   "source_files/morphological-operation.cpp"
   "source_files/main-image-gui.cpp"
   "source_files/image.cpp"
)
 
# Create executable with all necessary source files
add_executable(${PROJECT_NAME}
  ${project_sources}
)

target_link_libraries(${PROJECT_NAME} Qt5::Widgets ${OpenCV_LIBS} ${CMAKE_THREAD_LIBS_INIT})

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)