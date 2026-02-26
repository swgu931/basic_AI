# RPC Clustering : RPC Vector Embedding


## 각 GPU PC 에서 llama.cpp를 빌드하고 RPC 서버를 실행
```bash
./llama-cli --rpc --model ...  --host <server ip> --port <port_no>
```

## 메인 호스트에서 RPC 클라이언트 실행
```bash
./llama-cli --rpc <server ip>:<port_no> --model ...









