find_package( OpenCV REQUIRED )

add_library( four-point-numerical 
    four-point-numerical.cpp precomp.cpp modelest.cpp  )

target_link_libraries(four-point-numerical ${OpenCV_LIBS} gsl gslcblas m)

# install library
install(TARGETS four-point-numerical
  PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib
)

# install header files
install(DIRECTORY . DESTINATION include/relative-pose-estimation/four-point-numerical/
          FILES_MATCHING PATTERN "*.h*" PATTERN ".svn" EXCLUDE)
