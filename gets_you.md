## So... what does this get you?


### Readable build logs
---
<pre style="font-size: 0.25em;">
<span style="color: gray;">~ $</span> <span class="fragment fade-in">cd ~/amp
<span style="color: gray;">~/amp $</span></span><span class="fragment fade-in"> mkdir build
<span style="color: gray;">~/amp $</span></span><span class="fragment fade-in"> cd build
<span style="color: gray;">~/amp/build $</span></span><span class="fragment fade-in"> cmake .. </span>                                                 
<span class="fragment fade-in">-- The Fortran compiler identification is GNU 7.4.0
-- Check for working Fortran compiler: /usr/bin/gfortran
-- Check for working Fortran compiler: /usr/bin/gfortran  -- works
-- Detecting Fortran compiler ABI info
-- Detecting Fortran compiler ABI info - done
-- Checking whether /usr/bin/gfortran supports Fortran 90
-- Checking whether /usr/bin/gfortran supports Fortran 90 -- yes
-- Looking for Fortran sgemm
-- Looking for Fortran sgemm - found
-- A library with BLAS API found.
-- Looking for Fortran cheev
-- Looking for Fortran cheev - found
-- A library with LAPACK API found.
-- Configuring done
-- Generating done
-- Build files have been written to: /home/liam/amp/build
<span style="color: gray;">~/amp/build $</span></span><span class="fragment fade-in"> make </span>
<span class="fragment fade-in"><span style="color: purple;">Scanning dependencies of target bhmie</span>
[  5%] <span style="color: darkgreen;">Building Fortran object bhmie-f/CMakeFiles/bhmie.dir/bhmie_mod.f90.o</span>
[ 11%] <span style="color: darkgreen;">Building Fortran object bhmie-f/CMakeFiles/bhmie.dir/bhmie_smod.f.o</span>
[ 16%] <span style="color: limegreen;">Linking Fortran static library libbhmie.a</span>
[ 16%] Built target bhmie
<span style="color: purple;">Scanning dependencies of target amp</span>
[ 22%] <span style="color: darkgreen;">Building Fortran object CMakeFiles/amp.dir/amp_chemistry.f90.o</span>
[ 27%] <span style="color: darkgreen;">Building Fortran object CMakeFiles/amp.dir/amp_dynamics.f90.o</span>
[ 33%] <span style="color: darkgreen;">Building Fortran object CMakeFiles/amp.dir/amp_optical.f90.o</span>
[ 38%] <span style="color: darkgreen;">Building Fortran object CMakeFiles/amp.dir/amp_utils.f90.o</span>
[ 44%] <span style="color: limegreen;">Linking Fortran static library libamp.a</span>
[ 44%] Built target amp
<span style="color: purple;">Scanning dependencies of target kracken</span>
[ 50%] <span style="color: darkgreen;">Building Fortran object kracken/src/CMakeFiles/kracken.dir/M_kracken.f90.o</span>
[ 55%] <span style="color: limegreen;">Linking Fortran static library libkracken.a</span>
[ 55%] Built target kracken
<span style="color: purple;">Scanning dependencies of target cloud_parcel</span>
[ 61%] <span style="color: darkgreen;">Building Fortran object CMakeFiles/cloud_parcel.dir/cloud_parcel.f90.o</span>
[ 66%] <span style="color: limegreen;">Linking Fortran executable cloud_parcel</span>
[ 66%] Built target cloud_parcel
<span style="color: purple;">Scanning dependencies of target callbhmie</span>
[ 72%] <span style="color: darkgreen;">Building Fortran object bhmie-f/CMakeFiles/callbhmie.dir/callbhmie.f.o</span>
[ 77%] <span style="color: limegreen;">Linking Fortran executable callbhmie</span>
[ 77%] Built target callbhmie
<span style="color: purple;">Scanning dependencies of target kracken_test</span>
[ 83%] <span style="color: darkgreen;">Building Fortran object kracken/EXE/CMakeFiles/kracken_test.dir/krackentest.f90.o</span>
<strong>f951:</strong> <span style="color: purple;">Warning:</span> Nonexistent include directory <strong>'/home/liam/amp/build/src'</strong> [<span style="color: purple;">-Wmissing-include-dirs</span>]
[ 88%] <span style="color: limegreen;">Linking Fortran executable kracken_test</span>
[ 88%] Built target kracken_test
<span style="color: purple;">Scanning dependencies of target kracken_test2</span>
[ 94%] <span style="color: darkgreen;">Building Fortran object kracken/EXE/CMakeFiles/kracken_test2.dir/krackentest2.f90.o</span>
<strong>f951:</strong> <span style="color: purple;">Warning:</span> Nonexistent include directory <strong>'/home/liam/amp/build/src'</strong> [<span style="color: purple;">-Wmissing-include-dirs</span>]
[100%] <span style="color: limegreen;">Linking Fortran executable kracken_test2</span>
[100%] Built target kracken_test2
<span style="color: gray;">~/amp/build $</span></span>
</pre>


### You only build what needs to be built
---
<pre style="font-size: 0.4em;">
<span style="color: gray;">~/amp/build $</span></span><span class="fragment fade-in"> make</span>
<span class="fragment fade-in">[ 16%] Built target bhmie
[ 44%] Built target amp
[ 55%] Built target kracken
[ 66%] Built target cloud_parcel
[ 77%] Built target callbhmie
[ 88%] Built target kracken_test
[100%] Built target kracken_test2
<span style="color: gray;">~/amp/build $</span></span><span class="fragment fade-in">
<span style="color: gray;">~/amp/build $</span></span><span class="fragment fade-in"> touch ../amp_chemistry.f90
<span style="color: gray;">~/amp/build $</span></span><span class="fragment fade-in"> make </span>
<span class="fragment fade-in">[ 16%] Built target bhmie
<span style="color: purple;">Scanning dependencies of target amp</span>
[ 22%] <span style="color: darkgreen;">Building Fortran object CMakeFiles/amp.dir/amp_chemistry.f90.o</span>
[ 27%] <span style="color: darkgreen;">Building Fortran object CMakeFiles/amp.dir/amp_optical.f90.o</span>
[ 33%] <span style="color: limegreen;">Linking Fortran static library libamp.a</span>
[ 44%] Built target amp
[ 55%] Built target kracken
[ 61%] <span style="color: limegreen;">Linking Fortran executable cloud_parcel</span>
[ 66%] Built target cloud_parcel
[ 77%] Built target callbhmie
[ 88%] Built target kracken_test
[100%] Built target kracken_test2
<span style="color: gray;">~/amp/build $</span></span>
</pre>


### Readable error messages
---
<pre style="font-size: 0.4em;">
<span style="color: gray;">~/amp/build $</span><span class="fragment fade-in"> echo "this is garbage" >> ../amp_chemistry.f90
<span style="color: gray;">~/amp/build $</span></span><span class="fragment fade-in"> make </span><span class="fragment fade-in">
[ 16%] Built target bhmie
Scanning dependencies of target amp
[ 22%] <span style="color: darkgreen;">Building Fortran object CMakeFiles/amp.dir/amp_chemistry.f90.o</span>
<strong>/home/liam/amp/amp_chemistry.f90:3:10:</strong>

 end modulethis is garbage
          1
<span style="color: red;">Error:</span> Expected terminating name at (1)
f951: <span style="color: red;">Error:</span> Unexpected end of file in <strong>'/home/liam/amp/amp_chemistry.f90'</strong>
CMakeFiles/amp.dir/build.make:62: recipe for target 'CMakeFiles/amp.dir/amp_chemistry.f90.o' failed
make[2]: *** [CMakeFiles/amp.dir/amp_chemistry.f90.o] Error 1
CMakeFiles/Makefile2:67: recipe for target 'CMakeFiles/amp.dir/all' failed
make[1]: *** [CMakeFiles/amp.dir/all] Error 2
Makefile:83: recipe for target 'all' failed
make: *** [all] Error 2
<span style="color: gray;">~/amp/build $</span></span><span class="fragment fade-in"> git checkout ..
<span style="color: gray;">~/amp/build $</span></span><span class="fragment fade-in"> make</span>
<span class="fragment fade-in">[ 16%] Built target bhmie
<span style="color: purple;">Scanning dependencies of target amp</span>
[ 22%] <span style="color: darkgreen;">Building Fortran object CMakeFiles/amp.dir/amp_chemistry.f90.o</span>
[ 27%] <span style="color: darkgreen;">Building Fortran object CMakeFiles/amp.dir/amp_optical.f90.o</span>
[ 33%] <span style="color: limegreen;">Linking Fortran static library libamp.a</span>
[ 44%] Built target amp
[ 55%] Built target kracken
[ 61%] <span style="color: limegreen;">Linking Fortran executable cloud_parcel</span>
[ 66%] Built target cloud_parcel
[ 77%] Built target callbhmie
[ 88%] Built target kracken_test
[100%] Built target kracken_test2
<span style="color: gray;">~/amp/build $</span></span>
</span>
</pre>


<div style="text-align: left">

### Some other things...
- Cross-platform and cross-compiler support
- Different build types: `Release`, `Debug`, and `RelWithDebInfo`
- `make` targets that are consistent with all other CMake projects:
    - `make all`: builds the project
    - `make clean`: cleans everything built by `make all`
    - `make <target name>`: builds `<target name>` (and dependencies)
- It's easy to nest `amp` in other CMake projects
</div>