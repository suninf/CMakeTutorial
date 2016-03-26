cmake_minimum_required (VERSION 2.6)

project (Tutorial)

# The version number.
set (Tutorial_VERSION_MAJOR 1)
set (Tutorial_VERSION_MINOR 0)

configure_file (
  "${PROJECT_SOURCE_DIR}/Tutorial/TutorialConfig.h.in"
  "${PROJECT_BINARY_DIR}/Tutorial/include/TutorialConfig.h"
  )

include_directories("${PROJECT_BINARY_DIR}/Tutorial/include")
include_directories ("${PROJECT_SOURCE_DIR}")		

option (USE_MYMATH 
        "Use tutorial provided math implementation" ON) 

if (USE_MYMATH)        
# MathFunctions
	add_subdirectory (MathFunctions) 
	set (EXTRA_LIBS ${EXTRA_LIBS} MathFunctions)
endif (USE_MYMATH)
 
add_executable(Tutorial Tutorial/tutorial.cxx)
target_link_libraries (Tutorial ${EXTRA_LIBS})
