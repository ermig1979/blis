cmake_minimum_required(VERSION 2.8)

set(BLIS_DIR "./")


if(AVX512)
	#set(BLIS_CFG "x86_64")
	set(BLIS_CFG "skx")
else()
	set(BLIS_CFG "haswell")
endif()

include(ExternalProject)
ExternalProject_Add(make_blis 
	SOURCE_DIR ${BLIS_DIR}
	CONFIGURE_COMMAND ${CMAKE_CURRENT_SOURCE_DIR}/configure --prefix=${CMAKE_BINARY_DIR}/blis --enable-threading=pthreads ${BLIS_CFG}
	BUILD_COMMAND ${MAKE}
)
