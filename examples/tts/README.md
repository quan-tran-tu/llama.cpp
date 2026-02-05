# Adding Qwen3 TTS to llama.cpp

## Flow

### 1. Final usage

```bash
./build/bin/llama-tts-qwen3 \
    -m <qwen3_tts_model_path> \
    -mv <qwen3_tokenizer_model_path> \
    -p "text" -o <output_path>
```

### 2. Development space
- Create `examples/tts/` with `CMakeLists.txt` and `README.txt`
- Update `examples/CMakeLists.txt`
- Add model files for qwen3-tts and qwen3-tokenizer to `src/models`
- Update:
    - `llama-arch.h`, `llama-arch.cpp`
    - `llama-model.h`, `llama-model.cpp`
- Need to convert qwen3-tts and qwen3-tokenizer huggingface files to gguf too, which needs to udpate `convert_hf_to_gguf.py` too

## Plan
### 0. Analyse `convert_hf_to_gguf.py`

### 1. Analyse existing usage
- Map model configurations (from huggingface files) with implementation in `src/models` for `qwen3`, `wav-tokenizer` and `oute-tts`
- Analyse the existing inference file (`tools/tts/tts.cpp`), figure out high-level flow, inputs and outputs

### 2. Implement
#### a) Add qwen3-tts and qwen3-tokenizer related classes support to `convert_hf_to_gguf.py`
#### b) `examples/tts/CMakeLists.txt`, `examples/tts/README.txt` and update `examples/CMakeLists.txt`
#### c) `models/qwen3-tokenizer.cpp`, `examples/tts/tts.cpp` to test the tokenizer and update files in `src/`
#### d) `models/qwen3-tts.cpp`, update `examples/tts/tts.cpp` to integrate with the tokenizer
