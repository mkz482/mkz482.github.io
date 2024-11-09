HEY THIS IS MY GAME SPOT COME JOIN DOWN HERE
name: .NET Core

on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Setup .NET Core
      uses: actions/setup-dotnet@v1
      with:
        dotnet-version: 3.1.101
    - name: Install dependencies
      run: dotnet restore ./Source/BrawlStars/
    - name: Build
      run: dotnet build ./Source/BrawlStars/ --configuration Release --no-restore
    - name: Test
      run: dotnet test ./Source/BrawlStars/ --no-restore --verbosity normal
