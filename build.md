@ubuntu 24.04.2 LTS

安装好ROCm 7.2.0 并拷贝gfx906的支持文件

sudo apt install cmake

cmake -DCMAKE_PREFIX_PATH=/opt/rocm -B build  # 构建输出目录
cmake --preset "ROCm 7"  # 使用ollama项目根目录下的CMakePresets.json中的"ROCm 7"预设配置来初始化CMake项目。没有这行构建出来的项目只能支持cpu
cmake --build build --parallel 16  # --build表示执行构建任务 build表示构建输出目录 --parallel 16 表示并行16个构建

vi ~/.profile
export OLLAMA_MODELS="/usr/share/ollama/.ollama/models"
export OLLAMA_HOST="0.0.0.0"

go run . serve  # 运行服务端

go run . run qwen3:14b # 运行


源码构建的项目，默认配置文件目录为~/.ollama
二进制安装的，默认配置文件目录为 /usr/share/ollama/.ollama
