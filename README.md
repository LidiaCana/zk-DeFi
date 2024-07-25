# zk-DeFi

Preguntas:

- Cuando deposito y despues quiero retirar, tengo que retirar lo justo que deposite cuando genere la prueba, o puedo retirar por partes y generar un nuevo balance.

- Cuando hasheamos la llave privada y el nullifier quiere decir que ese hash va poder ser utilizado una sola vez
- El nulificador puede ser cualquier string o numero?
-

Ceremonia de inicio de prueba:
```
circom proveWithdrawal.circom --r1cs --wasm --sym
snarkjs powersoftau new bn128 12 pot12_0000.ptau -v
snarkjs powersoftau contribute pot12_0000.ptau pot12_0001.ptau --name="First contribution" -v
snarkjs powersoftau prepare phase2 pot12_0001.ptau pot12_final.ptau -v
snarkjs groth16 setup proveWithdrawal.r1cs pot12_final.ptau proveWithdrawal_0000.zkey
snarkjs zkey contribute proveWithdrawal_0000.zkey proveWithdrawal_0001.zkey --name="1st Contributor Name" -v
snarkjs zkey export verificationkey proveWithdrawal_0001.zkey verification_key.json```


