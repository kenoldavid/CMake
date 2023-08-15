# CMake policy mechanisms saying "behave like CMake version X.Y.Z".
# It specifies the minimum version of CMake the project needs.
cmake_minimum_required(VERSION 3.15)

# CMake sets up a number of variables and properties which control 
# the build for teh enabled languages.
project(
		TxtMsg2File
		VERSION 0.0.1
		DESCRIPTION "This application creates a simple Hello World! string and writes it into a file using Unicode characters"
		LANGUAGES CXX
		)

# GLOBING
file(GLOB_RECURSE SOURCE_FILES 
	src/*.cpp
	)
	
add_executable(TxtMsg2FileBinary main.cpp ${SOURCE_FILES})


# This command tells CMake to create an executable from a set of 
# source implementation files and main.
# add_executable(
	# # name of the executable
	# TxtMsg2FileBinary 
	
	# # instructs CMake to build the executable as a Windows GUI application.
	# #WIN32 
	
	# # source files to build
	# src/mainwindow.cpp
	# main.cpp
# )

# This cmd adds expected computer features to a target.
# (i.e., use C++20 to compile this binary and make it private
# because we don't expect anyone else to use this executable.)
target_compile_features(TxtMsg2FileBinary PRIVATE cxx_std_20)

# This cmd lets cmake know where to find the header files
target_include_directories(TxtMsg2FileBinary PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/include)

