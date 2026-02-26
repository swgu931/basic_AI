# howto make importance matrix and quantized model

- https://github.com/ggml-org/llama.cpp/tree/master/examples/imatrix


```bash
# generate importance matrix (imatrix.dat)
./llama-imatrix -m ggml-model-f16.gguf -f train-data.txt -ngl 99

# use the imatrix to perform a Q4_K_M quantization
./llama-quantize --imatrix imatrix.dat ggml-model-f16.gguf ./ggml-model-q4_k_m.gguf q4_k_m
```






