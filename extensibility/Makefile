.PHONY build-all-plugins: build-uppercase build-obfuscate build-reverse

.PHONY build-reverse:
build-reverse:
	pushd plugins; \
	pushd reverse-js; \
	jco componentize reverse.js --wit ./wit/wasmio.wit -o reverse-js.wasm; \
	mv reverse-js.wasm ../../

.PHONY build-uppercase:
build-uppercase: 
	pushd plugins; \
	pushd uppercase-py; \
    . venv/bin/activate; \
	componentize-py -d wasmio.wit -w plugin componentize app -o uppercase-py.wasm; \
	mv uppercase-py.wasm ../../

.PHONY build-obfuscate:
build-obfuscate: 
	pushd plugins; \
	pushd obfuscate-rust; \
	cargo component build --target wasm32-unknown-unknown --release; \
	mv ./target/wasm32-unknown-unknown/release/obfuscate.wasm ../../

.PHONY build-host:
build-host:
	pushd transformer; \
	cargo build --release

.PHONY run:
run:
	pushd transformer; \
	cargo run --release

.PHONY activate-all-plugins:
activate-all-plugins:
	cp *.wasm ./active/

.PHONY deactivate-all-plugins:
deactivate-all-plugins:
	rm ./active/*.wasm
