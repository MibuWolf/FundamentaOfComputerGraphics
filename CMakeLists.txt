# CMake ��Ͱ汾��Ҫ��
cmake_minimum_required (VERSION 2.8)

# ���õ�ǰProject������
set(ENGINE_PROJECT_NAME FundamentaOfComputerGraphics)
project(${ENGINE_PROJECT_NAME})

#����Include�ļ���
include_directories(${CMAKE_CURRENT_LIST_DIR}/3rdParty/GLEW/include)
include_directories(${CMAKE_CURRENT_LIST_DIR}/3rdParty/GLFW/include)
include_directories(${CMAKE_CURRENT_LIST_DIR}/3rdParty/GLM/glm)
include_directories(${CMAKE_CURRENT_LIST_DIR}/3rdParty/SOIL2/include)
include_directories(${CMAKE_CURRENT_LIST_DIR}/3rdParty/glad/include)
#����Դ�ļ�Ŀ¼
# ���ô������
set(SRC_Path ${CMAKE_CURRENT_LIST_DIR})


#�꣬ʵ��visio studio��Ŀ¼���飨������������
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

#����lib���ļ���
add_executable(${ENGINE_PROJECT_NAME} ${ALL_CODES})

#�������
set(LIBRARY_OUTPUT_PATH ${CMAKE_CURRENT_LIST_DIR}/WorkSpace)
set_target_properties(${THIS_PROJECT} PROPERTIES RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_CURRENT_LIST_DIR}/../WorkSpace)
set_target_properties(${THIS_PROJECT} PROPERTIES RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_CURRENT_LIST_DIR}/../WorkSpace)

set(REG_EXT "[^/]*([.]cpp|[.]c|[.]h|[.]hpp|[.]inl|[.]vs|[.]fs)$")

source_group("FundamentaOfComputerGraphics" REGULAR_EXPRESSION "${SRC_Path}/FundamentaOfComputerGraphics/${REG_EXT}")