#### analysis programs for HP10L LED calibration
* DatReader
  * is a class for reading binary of HP10L
  * binary data format is shown in pp.156 in this [URL](https://www-he.scphys.kyoto-u.ac.jp/member/kiseki/html/AXEL/e-log/e-log_nakamura-AXEL_anal002_20141212-20151224.pdf)
  * You can use this class in macro and CINT. Look at an example in `./example/mcr_DatReader.cc`
  * Useful functions of DatReader
    * `showFileHeader()`: show file header list
    * `getMaxEventNum()`: return max event num
    * `getMaxModuleNum()`: return max module num
    * `getEvent(int event_num, int read_module_num)` 
    * `getCurrentEventNum()`: return current event num
    * `getCurrentModuleNum()`: return current module num
    * `getAdc(int read_ch)`: return a pointer of a signal array
    * `getClock()`: return a pointer of a clock array
    * `getCurrentClockLength()`: return clock length of a current module
    * `getCurrentMaxchNum()`: return max ch of a current module
    * `getCurrentBitNum()`: return adc bit num of a current module

* BaselineAnalizer
  * is a class for analysing baseline
  * Useful functions of BaselineAnalizer
    * `BaselineAnalizer(double *wave, int clock_length, int bit_num, const bool is_debug=false, const int module=0, const int ch=0, const int event=0)`: constructor with analysis
    * `anaBaseline(double *wave, int bit_num, int baseline_min, int baseline_max, const int module=0, const int ch=0, const int event=0)`: you should use this function with a default constructor.
    * `getBaselinePeakBin()`: return a peak bin value of baseline histogram
    * `getBaseline()`: return a baseline
    * `getBaselineSigma()`: return a baseline sigma      

* MyCanvas
  * is a class for making canvas of HP10L
  * Useful functions of MyCanvas
    * `MyCanvas(std::string canvas_name, double position_x=100.0, double position_y=100.0)`: constructor of MyCanvas
    * `cloneCanvas()`: return TCanvas for square MPPC arrays of HP10L.


#### Installation of this sample
  * `$ git clone <URL>`
  * `$ make`
    * `$ ./example/dummy.cc` is compiled.
    * `$ ./bin/dummy` will be created.
  * `$ make TARGET=draw_waveforms`
    * `$ ./example/draw_waveforms.cc` is compiled.
    * `$ ./bin/draw_waveforms` will be created.

  
#### How to use mcr_DatReader.cc
  * `$ cd <your working dir>`
  * `$ ln -s ~/[source dir]/HP10L_anal/example/mcr_DatReader.cc`
  * `$ root 'mcr_DatReader.cc("[path to dat file]")'`