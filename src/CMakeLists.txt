## author: Ryotaro Onuki <kerikun11+github@gmail.com>
include_directories(${CMAKE_HOME_DIRECTORY}/include)
file(GLOB SRCS *.cpp)
add_library(mazelib STATIC ${SRCS})

## more warnnings
add_compile_options(-Wfatal-errors -Wall -Wextra)
add_compile_options(-Werror)
add_compile_options(-Wcast-align -Wcast-qual -Wchar-subscripts -Wcomment -Wdisabled-optimization -Wfloat-equal -Wformat -Wformat=2 -Wformat-nonliteral -Wformat-security -Wformat-y2k -Wimport -Winit-self -Winvalid-pch -Wmissing-braces -Wmissing-field-initializers -Wmissing-format-attribute -Wmissing-include-dirs -Wparentheses -Wpointer-arith -Wredundant-decls -Wreturn-type -Wsequence-point -Wsign-compare -Wstack-protector -Wstrict-aliasing -Wstrict-aliasing=2 -Wswitch -Wtrigraphs -Wuninitialized -Wunknown-pragmas -Wunreachable-code -Wunused -Wunused-function -Wunused-label -Wunused-parameter -Wunused-value -Wunused-variable -Wvariadic-macros -Wvolatile-register-var -Wwrite-strings)
add_compile_options(-Wconversion)
add_compile_options(-Weffc++)
add_compile_options(-pedantic -pedantic-errors)
add_compile_options(-Wunsafe-loop-optimizations)
add_compile_options(-Wlong-long)
add_compile_options(-Wswitch-default)
add_compile_options(-Wswitch-enum)
add_compile_options(-Wmissing-noreturn)
add_compile_options(-Winline)
