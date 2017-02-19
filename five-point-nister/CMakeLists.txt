find_package( OpenCV REQUIRED )

add_library( five-point-nister
    five-point.cpp precomp.cpp modelest.cpp )

target_link_libraries(five-point-nister 
    ${OpenCV_LIBS} )

# install library
install(TARGETS five-point-nister
  PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib
)

# install header files
install(DIRECTORY . DESTINATION include/relative-pose-estimation/five-point-nister/
          FILES_MATCHING PATTERN "*.h*" PATTERN ".svn" EXCLUDE)
