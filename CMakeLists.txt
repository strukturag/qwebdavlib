cmake_minimum_required(VERSION 3.10)

project(qwebdavlib)

set(CMAKE_CXX_STANDARD 17)

# Instruct CMake to run moc automatically when needed
set(CMAKE_AUTOMOC ON)
# Create code from a list of Qt designer ui files
set(CMAKE_AUTOUIC ON)
# Resource compiler
set(CMAKE_AUTORCC ON)

# for windows build
ADD_DEFINITIONS(-DQWEBDAV_LIBRARY)

add_library(${PROJECT_NAME} STATIC
    qwebdavlib/qnaturalsort.cpp
    qwebdavlib/qnaturalsort.h
    qwebdavlib/qwebdav.cpp
    qwebdavlib/qwebdavdirparser.cpp
    qwebdavlib/qwebdavdirparser.h
    qwebdavlib/qwebdav_global.h
    qwebdavlib/qwebdav.h
    qwebdavlib/qwebdavitem.cpp
    qwebdavlib/qwebdavitem.h
)
#set(CMAKE_VERBOSE_MAKEFILE ON)

# for the SingleApplication class
set(QAPPLICATION_CLASS QApplication CACHE STRING "Inheritance class for SingleApplication")

include_directories(
    qwebdavlib/
)

find_package(Qt5Gui CONFIG REQUIRED)
find_package(Qt5Core CONFIG REQUIRED)
find_package(Qt5Network CONFIG REQUIRED)
find_package(Qt5Widgets CONFIG REQUIRED)
find_package(Qt5Xml CONFIG REQUIRED)

include_directories(${Qt5Widgets_INCLUDE_DIRS})

target_link_libraries(${PROJECT_NAME} ${Qt5Gui_LIBRARIES})
target_link_libraries(${PROJECT_NAME} ${Qt5Core_LIBRARIES})
target_link_libraries(${PROJECT_NAME} ${Qt5Network_LIBRARIES})
target_link_libraries(${PROJECT_NAME} ${Qt5Widgets_LIBRARIES})
target_link_libraries(${PROJECT_NAME} ${Qt5Xml_LIBRARIES})
