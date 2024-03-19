* To install Haskell packages to your project using Cabal, you can follow these steps:


1.  **Add dependencies to your `.cabal` file**: You need to specify the packages your project depends on under the `build-depends` field in your `.cabal` file. This is where you declare the Haskell packages your project relies on. For example, if you want to add a package called `text`, you would modify the `build-depends` field like so:
    
    cabalCopy code
    
    ```cabal
        build-depends:    
        base ^>=4.17.2.1,
        text ^>=1.2.4.0
    ```
    
3.  **Update dependencies**: After modifying the `.cabal` file, you need to update your project's dependencies. Open a terminal, navigate to your project directory, and run:
    
    bashCopy code
    
    `cabal update` 
    
    This command updates the package index, ensuring you have the latest information about available packages.
    
4.  **Install dependencies**: Once you've updated the package index, you can install the dependencies specified in your `.cabal` file by running:
    
    bashCopy code
    
    `cabal install --only-dependencies` 
    
    This command installs the dependencies listed in your `.cabal` file, but it does not install the project itself. It's useful for fetching and installing the required packages.
    
5.  **Build your project**: After installing the dependencies, you can build your project by running:
    
    bashCopy code
    
    `cabal build` 
    
    This command compiles your project and generates the necessary executables.
    
6.  **Run your project**: If your project produces an executable, you can run it using:
    
    bashCopy code
    
    `cabal run <executable-name>` 
    
    Replace `<executable-name>` with the name of your executable as specified in your `.cabal` file.
    

Following these steps should allow you to install Haskell packages to your project using Cabal. Make sure to replace `text` with the actual package names you want to install.
