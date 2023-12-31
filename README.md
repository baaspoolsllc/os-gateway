<div align="center">
<img src="https://github.com/baaspoolsllc/os-gateway/assets/99137075/ced8035d-87da-4fd3-a51b-6c336fadc14c" width="500" alt="POKT Gateway Stack">
</div>

# POKT Gateway Stack

This project is currently in the alpha stage and actively under development. Before contributing, please reach out to [@nodiesBlade](https://github.com/nodiesBlade).

## What is POKT Gateway Stack?

The [POKT Gateway Stack](https://docs.nodies.app/pokt-integration-wip/nodies-gateway-stack) is a comprehensive solution designed to simplify the integration of applications with the POKT Network. Our goal is to reduce the complexities associated with directly interfacing with the protocol, making it accessible to a wide range of users, including application developers, existing centralized RPC platforms, and future gateway operators.

Learn more about the vision and overall architecture [here](https://docs.nodies.app/pokt-integration-wip/nodies-gateway-stack).

## Project Structure

- **cmd:** Contains the entry point of the binaries
    - **gateway_server:** HTTP Server for serving requests
- **internal:** Shared internal folder for all binaries
- **pkg:** Distributable dependencies

## Core Project Dependencies
- [FastHTTP](https://github.com/valyala/fasthttp) for both HTTP Client/Server
- [FastJSON](https://github.com/pquerna/ffjson) for performant JSON Serialization and Deserialization

## Lightweight Pocket Client

We have implemented our own lightweight Pocket client to enhance speed and efficiency. Leveraging the power of [FastHTTP](https://github.com/valyala/fasthttp) and [FastJSON](https://github.com/pquerna/ffjson), our custom client achieves remarkable performance gains. Additionally, it has the capability to properly parse node runner's POKT errors properly given that the network runs diverse POKT clients (geomesh, leanpokt, their own custom client).

### Why It's More Efficient/Faster
1. **FastHTTP:** This library is designed for high-performance scenarios, providing a faster alternative to standard HTTP clients. Its concurrency-focused design allows our Pocket client to handle multiple requests concurrently, improving overall responsiveness.
2. **FastJSON:** The use of FastJSON ensures swift and efficient JSON serialization and deserialization. This directly contributes to reduced processing times, making our Pocket client an excellent choice for high-scale web traffic.

## Local Development:
  1. In order to operate the gateway server, build the project
      ```sh
      go build cmd/gateway_server/main.go
      ```
  2. Copy `.env.sample` over to `.env` and fill out the details
     ```sh
     cp .env.sample .env
      ```
  3. Run the binary `./main`

## Running Tests
Before running any tests make sure to have the mock files in placed at `./mocks` folder.
You can generate the mock files through:
```sh
./scripts/mockgen.sh
```
By running this command, it will generate the mock files in `./mocks` folder.
Reference for creating a mock implementation https://vektra.github.io/mockery/latest/

Run this command to run some tests:
```sh
go test
```

## Contributing Guidelines
1. Create a Github Issue on the feature/issue you're working on.
2. Fork the project
3. Create new branch with `git checkout -b "branch_name"` where branch name describes the feature.
    - All branches should be based off `main`
3. Write your code
4. Make sure your code lints with `go fmt ./...` (This will Lint and Prettify)
5. Commit code to your branch and issue a pull request and wait for at least one review.
    - Always ensure changes are rebased on top of main branch.
