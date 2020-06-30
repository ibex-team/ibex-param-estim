################################################################################
# First example: compiling a library that depends on libibex
################################################################################
# source files of libibex-param-estim
list (APPEND SRC ${CMAKE_CURRENT_SOURCE_DIR}/ibex_CtcQInter2.cpp
                 ${CMAKE_CURRENT_SOURCE_DIR}/ibex_CtcQInter2.h
                 ${CMAKE_CURRENT_SOURCE_DIR}/ibex_KCoreGraph.cpp
                 ${CMAKE_CURRENT_SOURCE_DIR}/ibex_KCoreGraph.h
                 ${CMAKE_CURRENT_SOURCE_DIR}/ibex_QInter2.cpp
                 ${CMAKE_CURRENT_SOURCE_DIR}/ibex_QInter2.h
                 ${CMAKE_CURRENT_SOURCE_DIR}/ibex_QInter_coreF.cpp
                 ${CMAKE_CURRENT_SOURCE_DIR}/ibex_QInterEx_Cliquer.cpp
                 ${CMAKE_CURRENT_SOURCE_DIR}/ibex_QInter_projF.cpp
                 
                 # ============== cliquer ==================
                 ${CMAKE_CURRENT_SOURCE_DIR}/cliquer/cl.cpp
                 ${CMAKE_CURRENT_SOURCE_DIR}/cliquer/cliquerconf.h
                 ${CMAKE_CURRENT_SOURCE_DIR}/cliquer/cliquer.cpp
                 ${CMAKE_CURRENT_SOURCE_DIR}/cliquer/cliquer.h
                 ${CMAKE_CURRENT_SOURCE_DIR}/cliquer/graph.cpp
                 ${CMAKE_CURRENT_SOURCE_DIR}/cliquer/graph.h
                 ${CMAKE_CURRENT_SOURCE_DIR}/cliquer/misc.h
                 ${CMAKE_CURRENT_SOURCE_DIR}/cliquer/reorder.cpp
                 ${CMAKE_CURRENT_SOURCE_DIR}/cliquer/reorder.h
                 ${CMAKE_CURRENT_SOURCE_DIR}/cliquer/set.h

                 # Add more source files here.
                 # For most plugins, the rest can be left as is.
                 )

list (APPEND HDR ${CMAKE_CURRENT_SOURCE_DIR}/ibex_CtcQInter2.h
                 ${CMAKE_CURRENT_SOURCE_DIR}/ibex_KCoreGraph.h
                 ${CMAKE_CURRENT_SOURCE_DIR}/ibex_QInter2.h
                 )


# Create the target for libibex-param-estim
add_library (ibex-param-estim ${SRC})
# TODO BUILD_INTERFACE and INSTALL_INTERFACE for inc dirs
target_include_directories (ibex-param-estim PUBLIC ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/cliquer)
target_link_libraries (ibex-param-estim PUBLIC Ibex::ibex)

# installation of libibex-param-estim files
list_filter_header (HDR ${SRC}) # Ibex should have installed this function
install (TARGETS ibex-param-estim DESTINATION ${CMAKE_INSTALL_LIBDIR})
message("headers" ${HDR})
install (FILES ${HDR} DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/ibex-param-estim)


