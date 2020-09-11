# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)

# 设置当前Project的名字
set(ENGINE_PROJECT_NAME FundamentaOfComputerGraphics)
project(${ENGINE_PROJECT_NAME})

#设置Include文件夹
include_directories(${CMAKE_CURRENT_LIST_DIR}/3rdParty/GLEW/include)
include_directories(${CMAKE_CURRENT_LIST_DIR}/3rdParty/GLFW/include)
include_directories(${CMAKE_CURRENT_LIST_DIR}/3rdParty/GLM/glm)
include_directories(${CMAKE_CURRENT_LIST_DIR}/3rdParty/SOIL2/include)
include_directories(${CMAKE_CURRENT_LIST_DIR}/3rdParty/glad/include)
#定义源文件目录
# 设置代码夹子
set(SRC_Path ${CMAKE_CURRENT_LIST_DIR})


#宏，实现visio studio的目录分组（过滤器）功能
#
file(
    GLOB
    ALL_CODES
	"${SRC_Path}/FundamentaOfComputerGraphics/*.c"
	"${SRC_Path}/FundamentaOfComputerGraphics/*.cpp"
)

link_directories(${CMAKE_CURRENT_LIST_DIR}/3rdParty/GLEW/lib)
link_libraries(glew32s.lib) 
link_directories(${CMAKE_CURRENT_LIST_DIR}/3rdParty/GLFW/lib-vc2017)
link_libraries(glfw3.lib) 
link_directories(${CMAKE_CURRENT_LIST_DIR}/3rdParty/SOIL2/lib)
link_libraries(soil2.lib) 

#设置lib库文件夹
add_executable(${ENGINE_PROJECT_NAME} ${ALL_CODES})

#设置输出
set(LIBRARY_OUTPUT_PATH ${CMAKE_CURRENT_LIST_DIR}/WorkSpace)
set_target_properties(${THIS_PROJECT} PROPERTIES RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_CURRENT_LIST_DIR}/../WorkSpace)
set_target_properties(${THIS_PROJECT} PROPERTIES RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_CURRENT_LIST_DIR}/../WorkSpace)

set(REG_EXT "[^/]*([.]cpp|[.]c|[.]h|[.]hpp|[.]inl|[.]vs|[.]fs)$")

source_group("FundamentaOfComputerGraphics" REGULAR_EXPRESSION "${SRC_Path}/FundamentaOfComputerGraphics/${REG_EXT}")