* To install Haskell packages to your project using Cabal, you can follow these steps:


1.  **Add dependencies to your `.cabal` file**: You need to specify the packages your project depends on under the `build-depends` field in your `.cabal` file. This is where you declare the Haskell packages your project relies on. For example, if you want to add a package called `text`, you would modify the `build-depends` field like so:
    
    ```cabal
        build-depends:    
        base ^>=4.17.2.1,
        text ^>=1.2.4.0
    ```
    
3.  **Update dependencies**: After modifying the `.cabal` file, you need to update your project's dependencies. Open a terminal, navigate to your project directory, and run:
    
    `cabal update` 
    
    This command updates the package index, ensuring you have the latest information about available packages.
    
4.  **Install dependencies**: Once you've updated the package index, you can install the dependencies specified in your `.cabal` file by running:
    

    
    `cabal install --only-dependencies` 
    
    This command installs the dependencies listed in your `.cabal` file, but it does not install the project itself. It's useful for fetching and installing the required packages.
    
5.  **Build your project**: After installing the dependencies, you can build your project by running:
  
    
    `cabal build` 
    
    This command compiles your project and generates the necessary executables.
    
6.  **Run your project**: If your project produces an executable, you can run it using:
    

    
    `cabal run <executable-name>` 
    
    Replace `<executable-name>` with the name of your executable as specified in your `.cabal` file.
    

Following these steps should allow you to install Haskell packages to your project using Cabal. Make sure to replace `text` with the actual package names you want to install.






# In case there are any missing dependencies

You may encounter an error while trying to install the `zlib` package, which is a dependency of `scotty`. The error message indicates that `cabal` is unable to find the necessary header file (`zlib.h`) and C library (`z`) for `zlib`.

Here are a few steps you can take to resolve this issue:

1.  **Install the zlib Development Package**: You'll need to install the development package for zlib, which usually includes the necessary header files and libraries required for development. On most Linux distributions, this package is typically named something like `zlib-devel` or `zlib1g-dev`. You can install it using your package manager. For example, on Ubuntu, you can run:
    
    
    `sudo apt-get install zlib1g-dev` 
    
    On CentOS/RHEL:
   
    
    `sudo yum install zlib-devel` 
    
    On macOS with Homebrew:
   
    
    `brew install zlib` 
    
2.  **Specify Include and Library Directories**: If you have installed zlib in a non-standard location, you may need to specify the include and library directories using the `--extra-include-dirs` and `--extra-lib-dirs` flags when running `cabal install`. For example:
    
    
    `cabal install scotty --extra-include-dirs=/path/to/zlib/include --extra-lib-dirs=/path/to/zlib/lib` 
    
3.  **Verify zlib Installation**: After installing the zlib development package, make sure that the `zlib.h` header file and the `z` library are accessible in the standard locations.
    
4.  **Check Build Logs**: If the issue persists, you can try re-running `cabal` with increased verbosity (`-v3`) to get more detailed error messages. This might help pinpoint the exact problem.
    

Once you've resolved the issue with `zlib`, you should be able to successfully install `scotty` using `cabal`.

# Verifying dependency installation

You can use the `dpkg` command to query information about installed packages on Debian-based systems like Debian itself or Ubuntu. Here's how you can check for the path of zlib using `dpkg`:

```bash
dpkg -L zlib1g-dev
``` 

This command lists all the files installed by the `zlib1g-dev` package, including the location of header files like `zlib.h`.

If you want to check for the path of the zlib library itself (libz), you can use:

```bash
dpkg -L zlib1g
``` 

This will show you the location of the library file (`libz.so`) and any other files installed by the `zlib1g` package.

If `zlib1g-dev` is not installed, you might want to install it using `apt`:


```bash
sudo apt update
sudo apt install zlib1g-dev
```

Once you have `zlib1g-dev` installed, you can use `dpkg -L` to find its path as described above.
