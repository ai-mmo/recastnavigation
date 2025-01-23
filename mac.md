compile problem:
编译Recastnavigation

首先下载GitHub - recastnavigation/recastnavigation: Industry-standard navigation-mesh toolset for gamesma

mkdir Build
cd Build
cmake .. -D CMAKE_BUILD_TYPE=True
make
-D CMAKE_BUILD_TYPE=True 为开启debug模式

会出现报错

recastnavigation/RecastDemo/Source/ConvexVolumeTool.cpp:23:10: fatal error: 'SDL.h' file not found

需要下载SDL2库

brew install SDL2
查看安装位置

brew --prefix sdl2
输出

/opt/homebrew/opt/sdl2
然后找到/recastnavigation/RecastDemo/CMakeLists.txt


set(SDL2_ROOT_DIR "/opt/homebrew/Cellar/sdl2/你的版本号")

include_directories(${SDL2_ROOT_DIR}/include/SDL2)

run problem:

RecastNavigation 的测试和示例程序依赖于 OpenGL 和 GLFW 进行渲染

I see this message in the console: Could not init GUI renderer.


	if (!imguiRenderGLInit("DroidSans.ttf"))
	{
		printf("Could not init GUI renderer.\n");
		SDL_Quit();
		return -1;
	}


