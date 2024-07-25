# zk-DeFi

Preguntas:

- Cuando deposito y despues quiero retirar, tengo que retirar lo justo que deposite cuando genere la prueba, o puedo retirar por partes y generar un nuevo balance.

- Cuando hasheamos la llave privada y el nullifier quiere decir que ese hash va poder ser utilizado una sola vez
- El nulificador puede ser cualquier string o numero?
-

Ceremonia de inicio de prueba:

circom proveWithdrawal.circom --r1cs --wasm --sym
snarkjs powersoftau new bn128 12 pot12_0000.ptau -v
snarkjs powersoftau contribute pot12_0000.ptau pot12_0001.ptau --name="First contribution" -v
snarkjs powersoftau prepare phase2 pot12_0001.ptau pot12_final.ptau -v
snarkjs groth16 setup proveWithdrawal.r1cs pot12_final.ptau proveWithdrawal_0000.zkey
snarkjs zkey contribute proveWithdrawal_0000.zkey proveWithdrawal_0001.zkey --name="1st Contributor Name" -v
snarkjs zkey export verificationkey proveWithdrawal_0001.zkey verification_key.json

cast send --rpc-url https://1rpc.io/sepolia --private-key ff8694fe5532db274d749d7752278ea4f37c8df50fdbd9eeceb02747a07c885a --create $(cat poseidonBytecode)

RPC_URL=https://1rpc.io/sepolia HURACAN_ADDRESS=0xc010553F6Cf99E73E147f79c63850598511A4aD2 RELAYER_PRIVATE_KEY=ff8694fe5532db274d749d7752278ea4f37c8df50fdbd9eeceb02747a07c885a RELAYER_ADDRESS=0xe527275DA855C658de60EcA230800458f668194B node relayer.mjs
