macos:
	cargo build --release --lib --target aarch64-apple-darwin
	cargo build --release --lib --target x86_64-apple-darwin
	lipo -create -output outputs/compiled-macos.a target/aarch64-apple-darwin/release/libcorerust.a target/x86_64-apple-darwin/release/libcorerust.a

ios:
	cargo build --release --lib --target aarch64-apple-ios
	cargo build --release --lib --target aarch64-apple-ios-sim
	cargo build --release --lib --target x86_64-apple-ios
	cp target/aarch64-apple-ios/release/libcorerust.a outputs/compiled-ios.a
	lipo -create -output outputs/compiled-ios-sim.a target/aarch64-apple-ios-sim/release/libcorerust.a target/x86_64-apple-ios/release/libcorerust.a

generatexcf:
	xcodebuild -create-xcframework \
	-library outputs/compiled-macos.a -headers ./include \
	-library outputs/compiled-ios.a -headers ./include \
	-library outputs/compiled-ios-sim.a -headers ./include \
	-output CoreRust.xcframework
