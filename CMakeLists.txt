IF(BIICODE)
	ADD_BIICODE_TARGETS()

	add_definitions( -DFREEGLUT_EXPORTS -DFREEGLUT_STATIC -D_CRT_SECURE_NO_WARNINGS )

	if(APPLE)
		include_directories( /usr/X11/include )
	endif(APPLE)

	IF (UNIX)
     	IF(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/Box2D/Testbed")
  			add_definitions( -D__unix__ -DHAVE_FCNTL_H -DHAVE_GETTIMEOFDAY )
        	TARGET_LINK_LIBRARIES(${BII_BLOCK_TARGET} INTERFACE pthread X11)
        	find_package(OpenGL REQUIRED)
    	ENDIF()
  	ENDIF(UNIX)
	RETURN()
ENDIF(BIICODE)
