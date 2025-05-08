# Add a library called MathFunctions with sources MathFunctions.cxx and mysqrt.cxx
add_library(MathFunctions MathFunctions.cxx)

# create a variable USE_MYMATH using option and set default to ON
option(USE_MYMATH "Use tutorial provided math implementation" ON)

# if USE_MYMATH is ON, pass USE_MYMATH as a precompiled definition to our source files
if(USE_MYMATH)
    target_compile_definitions(MathFunctions PRIVATE "USE_MYMATH")
    # add a library for SqrtLibrary
    add_library(SqrtLibrary STATIC mysqrt.cxx)
    # link SqrtLibrary to the MathFunctions Library
    target_link_libraries(MathFunctions PRIVATE SqrtLibrary)
endif()
