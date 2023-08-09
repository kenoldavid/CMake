# CMake policy mechanisms saying "behave like CMake version X.Y.Z".
# It specifies the minimum version of CMake the project needs.
cmake_minimum_required(VERSION 3.15)

# CMake sets up a number of variables and properties which control 
# the build for teh enabled languages.
project(TxtMsg2File)

# This command tells CMake to create an executable from a set of 
# source files.
add_executable(
	# name of the executable
	TxtMsg2File 
	
	# instructs CMake to build the executable as a Windows GUI application.
	WIN32 
	
	# source files to be build
	mainwindow.h
	mainwindow.cpp
	main.cpp
)

