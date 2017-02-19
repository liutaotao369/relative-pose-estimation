cmake_minimum_required(VERSION 2.8.3)
SET(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_LIST_DIR}/cmake/)

find_package( OpenCV REQUIRED )
# Uncomment all the following commented code to use SPQR instead of SparseQR
# find_package( Cholmod REQUIRED )
# find_package( SPQR REQUIRED )

include_directories( ../eigen/ )
# include_directories( /usr/include/suitesparse/ )

add_library( four-point-groebner
    four-point-groebner.cpp modelest.cpp precomp.cpp )

target_link_libraries(four-point-groebner 
    ${OpenCV_LIBS} 
    #    ${CHOLMOD_LIBRARIES} 
    #    ${AMD_LIBRARY} 
    #    ${COLAMD_LIBRARY} 
    #    ${SPQR_LIBRARIES}
    #    lapack
    #    csparse
    #    cxsparse  
    #    cholmod
    #    blas
    #    spqr
    )

# install library
install(TARGETS four-point-groebner
  PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib
)

# install header files
install(DIRECTORY . DESTINATION include/relative-pose-estimation/four-point-groebner/
          FILES_MATCHING PATTERN "*.h*" PATTERN ".svn" EXCLUDE)
