# Tar-Cpp

A c++ / cpp library designed to wrap streambuf and istream similar to substrings.

Sample usage:


```c++
#include <estd/isubstream.hpp>
#include <fstream>

using namespace std;
using namespace estd; // library namespace

int main() {
	string filename = "./example.txt";
	ifstream file(filename);
	isubstream subFile1 = isubstream(file.rdbuf(), 3, 10);
	isubstream subFile2 = isubstream(file.rdbuf(), 16, 10);
	isubstream subFile3 = isubstream(file.rdbuf(), 29, 10);
	char c;
	while (subFile1 >> c) { cout << c; }
	cout << endl;

	cout << subFile3.rdbuf() << endl;

	char buffer[100] = {};
	int size = subFile2.read(buffer, 100).gcount();
	cout << buffer;
	cout << endl;
	cout << "size = " << size << endl;
	return 0;
}
```

The makefile will build and run the main file. (modify the main file to try out the library)


To use this project with a dependency manager install the cpp-dependency-manager project from https://github.com/TAR-ALEX/Cpp-Dependency-Manager.git

and create a vendor.txt file and add the following entries:

```
git "https://github.com/TAR-ALEX/substreams_cpp" main "./include" "./vendor/include",

```
