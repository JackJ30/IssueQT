cmake_minimum_required(VERSION 3.16)
project(QTTest)

# Set directories
set(SOURCE_DIR "${CMAKE_SOURCE_DIR}/src")
set(FORMS_DIR "${CMAKE_SOURCE_DIR}/src")

# Set Qt moc and uic
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOUIC_SEARCH_PATHS ${FORMS_DIR})

# Initialize QT
find_package(Qt6 REQUIRED COMPONENTS Core Gui Widgets)

# Find source files
set(SOURCE_FILES)
file(GLOB_RECURSE SOURCE_FILES
        "${FORMS_DIR}/*.ui"
        "${FORMS_DIR}/*.qrc"
        "${SOURCE_DIR}/*.cpp"
)

# Add executable
add_executable(${PROJECT_NAME} ${SOURCE_FILES})
target_include_directories(${PROJECT_NAME} PRIVATE ${SOURCE_DIR} ${FORMS_DIR} )
target_link_libraries(${PROJECT_NAME} PRIVATE Qt6::Core Qt6::Gui Qt6::Widgets)