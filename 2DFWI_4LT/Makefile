#! bin/sh

#MPICH2_HOME=/u/geoeast/geoeast3.0_ora_as62_dev/support/mpi
#CUDA_HOME=/u/geoeast/geoeast3.0_ora_as62_dev/support/cuda

MPICH2_HOME=/usr/local/mpich
#CUDA_HOME=/usr/local/cuda-7.5
CUDA_HOME=/home/fjw/Softwares/cuda_10.0

NVCC = $(CUDA_HOME)/bin/nvcc
MPICC = $(MPICH2_HOME)/bin/mpicc

INC = -I$(CUDA_HOME)/include -I$(MPICH2_HOME)/include

LDFLAGS = -L$(CUDA_HOME)/lib64 -L$(MPICH2_HOME)/lib
LIB = -lm -lmpich -lopa -lmpl -lrt -lpthread -lcudart -lcurand -lcufft

CFILES = elastic_fdtd_2d_cpml_GPU_HLMPIFWI_Vigh.cpp
CUFILES = elastic_fdtd_2d_cpml_GPU_HLMPIFWILc_Vigh.cu
OBJECTS = elastic_fdtd_2d_cpml_GPU_HLMPIFWI_Vigh.o elastic_fdtd_2d_cpml_GPU_HLMPIFWILc_Vigh.o 
EXECNAME = mpifwimar

all:
	$(MPICC) -w -c $(CFILES) $(INC) $(LDFLAGS) $(LIB)
	$(NVCC) -w -c $(CUFILES) $(INC) $(LDFLAGS) -Xcompiler $(LIB)
	$(MPICC) -o $(EXECNAME) $(OBJECTS) $(INC) $(LDFLAGS) $(LIB)
	rm -f *.o 
#cp $(EXECNAME) /d0/data/migration/extgzb/marmousi/new/

#CC=nvcc
#CFLAGS=-I. -I/u/geoeast/geoeast3.0_ora_as62_dev/support/mpi/include -I/u/geoeast/geoeast3.0_ora_as62_dev/support/cuda/include
#LDFLAGS=-L/u/geoeast/geoeast3.0_ora_as62_dev/support/mpi/lib -L/u/geoeast/geoeast3.0_ora_as62_dev/support/cuda/lib64
#LIB= -lcudart -lm -lmpich -lpthread -lmpl -lfmpich -lcufft
#MPICH_FLAG= -DMPICH_IGNORE_CXX_SEEK  -DMPICH_SKIP_MPICXX
#SOURCES=elastic_fdtd_2d_cpml_GPU_MPIFWI2C.cu elastic_fdtd_2d_cpml_GPU_MPIFWI2C.cpp
#EXECNAME=mpifwimarmousi
#all:
#	$(CC) -v -o $(EXECNAME) $(SOURCES) $(LIB)  $(LDFLAGS) $(CFLAGS) $(MPICH_FLAG)
#	mpirun -machinefile hosts -np 61 ./$(EXECNAME)  
#clean:
#	rm -f *.o 


#nohup mpirun -machinefile hosts -np 12 $(EXECNAME) 
#mpicc -o tst getdevice.cpp getdevice.o -lcudart -L /u/geoeast/geoeast3.0_ora_as62_dev/support/cuda/lib -I /u/geoeast/geoeast3.0_ora_as62_dev/support/cuda/include/

#! /bin/sh

#INC=/home/program/cuda/include
#LIK=/home/program/cuda/lib64
#
#LIB=-lcufft
#
#2dhlFWI:elastic_fdtd_2d_cpml_GPU_border_2LFWI.cu
#	nvcc -o 2dhlFWI elastic_fdtd_2d_cpml_GPU_border_2LFWI.cu  -I$(INC) -L$(LIK) $(LIB)
#	./2dhlFWI
#
#clean:
#	rm 2dhlFWI


