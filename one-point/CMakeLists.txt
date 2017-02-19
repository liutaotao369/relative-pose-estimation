find_package( OpenCV REQUIRED )

add_library( one-point
    one-point.cpp precomp.cpp modelest.cpp )

target_link_libraries(one-point
    ${OpenCV_LIBS} )

# install library
install(TARGETS one-point
  PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib
)

# install header files
install(DIRECTORY . DESTINATION include/relative-pose-estimation/one-point/
          FILES_MATCHING PATTERN "*.h*" PATTERN ".svn" EXCLUDE)
