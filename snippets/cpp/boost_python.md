# Boost Python

## STEP 0: setup

sudo apt-get install -y g++
sudo apt-get install -y libboost-dev-all


## STEP 1: create cpp

	 // v2.cpp
	 #include <iostream>
	 #include <boost/python.hpp>
	 
	 void sayHello()
	 {
	   std::cout << "Hello, Python!\n";
	 }
	 
	 BOOST_PYTHON_MODULE(v2)  // Name here must match the name of the final shared library, i.e. mantid.dll or mantid.so
	 {
	    boost::python::def("sayHello", &sayHello);
	 }


## STEP 2: build

	g++ -Wall -Wextra -fPIC -shared -I/usr/include/python2.7 -lboost_python v2.cpp -o v2.so


## STEP 3: use

	python
	import v2
	v2.sayHello()
