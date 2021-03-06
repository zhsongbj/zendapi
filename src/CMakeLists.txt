set(ZAPI_SRC
    kernel/Global.cpp
    vm/Extension.cpp)

zapi_add_library(${ZAPI_PROJECT_NAME} SHARED ${ZAPI_SRC}
                 ${ZAPI_PUBLIC_HEADERS}
                 ${ZAPI_PRIVATE_HEADERS})

export(TARGETS ${ZAPI_PROJECT_NAME}
       FILE "${ZAPI_BINARY_DIR}/ZendApiTargets.cmake")
export(PACKAGE ${ZAPI_PROJECT_NAME})

file(RELATIVE_PATH
     REL_INCLUDE_DIR
     "${ZAPI_INSTALL_CMAKE_DIR}"
     "${ZAPI_INSTALL_INCLUDE_DIR}")

#
# Install targets
#
install(TARGETS ${ZAPI_PROJECT_NAME}
        EXPORT ZendApiTargets
        RUNTIME DESTINATION "${ZAPI_INSTALL_BIN_DIR}" COMPONENT bin
        LIBRARY DESTINATION "${ZAPI_INSTALL_LIB_DIR}" COMPONENT lib
        ARCHIVE DESTINATION "${ZAPI_INSTALL_LIB_DIR}" COMPONENT lib)

# Install exports for the install-tree.
install(EXPORT ZendApiTargets
        DESTINATION
        "${ZAPI_INSTALL_CMAKE_DIR}"
        COMPONENT dev)
