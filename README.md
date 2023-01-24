# How to get started (from scratch)

- Always compare these steps with the original zero to production repo's readme
- Always work on your computer as a local non-admin user

1. clone the zero 2 prod repo ( https://github.com/LukeMathWalker/zero-to-production )
2. install rust via rustup (through cmd if on windows)
3. install postgres
4. add psql to system PATH variable
5. install cargo-binutils and llvm-tools-preview
```sh
cargo install cargo-binutils
rustup component add llvm-tools-preview
```
6. install sqlx ( https://crates.io/crates/sqlx-cli )
```sh
cargo install --version="~0.6" sqlx-cli --no-default-features --features rustls,postgres
```
7. install docker desktop
8. Restart
9. Add current non-admin user to docker-users group
Note: 
- Ideally you'd want to be able to access docker-daemon without needing to run programs as admin.
- Windows 10 Computer Management has Local Users and Groups section
- Windows 11 does not, but you can use powershell to handle this instead.
10. POWERSHELL:
```ps
Get-LocalGroup
Get-LocalUser
Add-LocalGroupMember -Group docker-users -Member YOUR_WINDOWS_ACCOUNT
```
11. Log out and back in
12. Run Docker desktop (accept user agreement)

## How to test
```sh
# How to test
./scripts/init_db.sh
./scripts/init_redis.sh
cargo test
```

## How to build
``sh
./scripts/init_db.sh
./scripts/init_redis.sh
cargo build
``

You can now try with opening a browser on http://127.0.0.1:8000/login after having launch the web server with `cargo run`.
There is a default `admin` account with password `everythinghastostartsomewhere`. The available entrypoints are listed in src/startup.rs


