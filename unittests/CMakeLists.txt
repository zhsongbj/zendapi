add_custom_target(UnitTests)
set_target_properties(UnitTests PROPERTIES FOLDER "UnitTests")
add_subdirectory(lang)
zapi_add_unittest(UnitTests EmbedPhpTest EmbedPhpTest.cpp)