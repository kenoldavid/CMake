# CMake policy mechanisms saying "behave like CMake version X.Y.Z".
# It specifies the minimum version of CMake the project needs.
cmake_minimum_required(VERSION 3.15)

# CMake sets up a number of variables and properties which control 
# the build for teh enabled languages.
project(TxtMsg2File
		VERSION 0.0.2
		DESCRIPTION "This application creates a simple Hello World! string and writes it into a file using Unicode characters"
		LANGUAGES CXX
)

#======================= INCLUSION OF Qt =======================#

# In many cases, Qt won’t be installed in one of CMake’s default search locations. Developers will typically need to provide that information to CMake using the CMAKE_PREFIX_PATH cache variable.
set(CMAKE_PREFIX_PATH $ENV{QTDIR})

# Qt provides a number of command-line tools which process sources and generate other source files to be consumed by the build. The three most important and heavily used of these tools are moc, uic and rcc.
#
# Set the AUTOMOC, AUTOUIC, and AUTORCC target properties to true.
set(CMAKE_AUTOMOC YES)
set(CMAKE_AUTOUIC YES)
set(CMAKE_AUTORCC YES)

# Locates an installation of Qt or terminates with an error msg.
find_package(Qt5 5.9 REQUIRED
	COMPONENTS	Core Gui Widgets
	#OPTIONAL_COMPONENT 
)

#===========================#

# GLOBING -- NOT RECOMMENDED
# file(GLOB_RECURSE SOURCE_FILES 
	# src/*.cpp
	# )


#=================== SETUP EXECTUABLE ====================#
# Create executable
add_executable(TxtMsg2FileBinary)

# Target declaration - Option  1
# ------------------------------
# A target maps to a build artifact in the project. Any target has a collection of properties.	
#add_executable(TxtMsg2FileBinary main.cpp ${SOURCE_FILES})

# Target declaration - Option  2
# ------------------------------
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

# Target declaration - Option  3
# ------------------------------
target_sources(TxtMsg2FileBinary
	PRIVATE
		src/mainwindow.cpp
		src/dog.cpp
		main.cpp
)

# This cmd adds expected computer features to a target.
# (i.e., use C++20 to compile this binary and make it private
# because we don't expect anyone else to use this executable.)
target_compile_features(TxtMsg2FileBinary 
	PRIVATE 
		cxx_std_20
)

# This cmd lets cmake know which directories will contain the header files
target_include_directories(TxtMsg2FileBinary 
	PRIVATE 
		${CMAKE_CURRENT_SOURCE_DIR}/include
)

#If successful, the find_package() call will define an imported target for each component found. These imported targets will be named Qt5::<ModuleName>, such as Qt5::Gui, Qt5::Widgets, etc. When project targets link against these imported targets, they will automatically have the relevant compiler defines, header search paths and library dependencies added to them.

#==== LINKING Qt LIBRARIES ====#
target_link_libraries(TxtMsg2FileBinary 
	PRIVATE
		Qt5::Core
		Qt5::Gui
)
