all: build

build: pi matrix pipe1 pipe2

pi: pi.cpp
	g++ pi.cpp -fopenmp -o pi.exe 
	
matrix: matrixproduct.cpp
	g++ matrixproduct.cpp -fopenmp -o matrix.exe 

pipe1: pipeline1.cpp
	g++ pipeline1.cpp -fopenmp -o pipe1.exe 

pipe2: pipeline2.cpp
	g++ pipeline2.cpp -fopenmp -o pipe2.exe 


