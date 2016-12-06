aux_source_directory (. SRC_LIST)

message(${SRC_LIST})

# add external libraries
find_package(OpenCV REQUIRED)

enable_testing ()
foreach (f ${SRC_LIST})
  link_directories(../../../FaceDetection/) 
  link_directories(../../../FaceAlignment/) 
  string(REGEX REPLACE "[.]cpp" ".bin" BIN ${f})
  add_executable(${BIN} ${f})
  target_link_libraries(${BIN} viplnet ${OpenCV_LIBS} seeta_fa_lib seeta_facedet_lib)
endforeach ()

