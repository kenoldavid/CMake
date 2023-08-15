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

# This command tells CMake to create an executable from a set of 
# source files.
add_executable(
	# name of the executable
	TxtMsg2FileBinary 
	
	# instructs CMake to build the executable as a Windows GUI application.
	#WIN32 
	
	# source files to build
	mainwindow.h
	mainwindow.cpp
	main.cpp
)

# This cmd add expected computer features to a target.
# (i.e., use C++20 to compile this binary and make it private
# because we don't expect anyone else to use this executable.)
target_compile_features(TxtMsg2FileBinary PRIVATE cxx_std_20)


