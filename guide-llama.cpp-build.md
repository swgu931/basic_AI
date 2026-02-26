# llama.cpp 빌드 방법

git clone https://github.com/ggerganov/llama.cpp.git

cd llama.cpp

# 1. build 디렉토리를 생성하고 CMake 설정 진행
cmake -B build

# 2. 실제로 컴파일을 수행 (시간이 조금 걸릴 수 있습니다)
cmake --build build --config Release -j

# 1. CUDA 지원을 활성화하여 설정
cmake -B build -DGGML_CUDA=ON

# 2. 컴파일 수행
cmake --build build --config Release -j

