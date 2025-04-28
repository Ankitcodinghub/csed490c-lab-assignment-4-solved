# csed490c-lab-assignment-4-solved
**TO GET THIS SOLUTION VISIT:** [CSED490C Lab Assignment 4 Solved](https://www.ankitcodinghub.com/product/csed490c-solved-3/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;115719&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CSED490C Lab Assignment 4 Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
1 Objective

The lab’s objective is to implement a tiled image convolution using both shared and constant memory. We will have a constant 5×5 convolution mask but an arbitrarily sized image (assume the image dimensions are greater than 5×5 for this Lab).

2 Instructions

To use the constant memory for the convolution mask, you can first transfer the mask data to the device. Consider the case where the pointer to the device array for the mask is named M. You can use const float * restrict M as one of the parameters during your kernel launch. This informs the compiler that the contents of the mask array are constants and will only be accessed through pointer variable M. This will enable the compiler to place the data into constant memory and allow the SM hardware to aggressively cache the mask data at runtime.

Convolution is used in many fields, such as image processing for image filtering. A standard image convolution formula for a 5×5 convolution filter M with an Image I is:

where Pi,j,c is the output pixel at position i,j in channel c, Ii,j,c is the input pixel at i,j in channel c (the number of channels will always be 3 for this MP corresponding to the RGB values), and Mx,y is the mask at position x,y.

Please use the “output tiling” algorithm discussed in the class for this assignment. You need to keep the thread block size the same as the tile size in your output matrix. All threads will equally participate in computing output matrix elements, but a subset of threads will load more elements into the shared memory than the others.

The code template in template.cu provides a starting point and handles the import and export as well as the checking of the solution. Students are expected to insert their code demarcated with //@@.

Students are expected to leave the other code unchanged. Edit the skeleton code to perform the following:

• Allocate device memory

• Copy host memory to device

• Initialize grid and thread blocks

• Launch the kernel

• Copy results from device to host

• Free device memory

• Write the CUDA kernel

Compile the template with the provided Makefile. The executable generated as a result of compilation can be run using the following code:

./ConvolutionTemplate -e &lt;expected.ppm&gt; -i &lt;input0.ppm&gt;,&lt;input1.raw&gt; -o &lt;output.ppm&gt; -t image

where &lt;expected.ppm&gt; is the expected output, &lt;input.ppm&gt; is the input dataset, and &lt;output.ppm&gt; is an optional path to store the results. The datasets can be generated using the dataset generator built as part of the compilation process.

The images are stored in PPM (P6) format, this means that you can (if you want) create your own input images. The easiest way to create image is via external tools such as ‘bmptoppm‘. The masks are stored in a CSV format. Since the input is small, it is best to edit it by hand.

README.md has details on how to build libgputk, template.cpp and the dataset generator.

3 Input Data

The input is an interleaved image of height × width × channels. By interleaved, we mean that the element I[y][x] contains three values representing the RGB channels. This means that to index a particular element’s value, you will have to do something like:

index = (yIndex*width + xIndex)*channels + channelIndex;

For this assignment, the channel index is 0 for R, 1 for G, and 2 for B. So, to access the G value of I[y][x], you should use the linearized expression I[(yIndex ∗ width + xIndex) ∗ channels + 1]. For simplicity, you can assume that channels is always set to 3.

4 What to Turn in

Submit a report that includes the following:

1. How many floating operations are being performed by your convolution kernel?

2. How many global memory reads are being performed by your convolution kernel?

3. How many global memory writes are being performed by your convolution kernel?

4. How much time is spent as an overhead cost for using the GPU for computation? Consider all codeexecuted within your host function with the exception of the kernel itself, as overhead. How does the overhead scale with the size of the input?

5. What do you think happens as you increase the mask size (say to 1024) while you set the blockdimensions to 16×16? What do you end up spending most of your time doing? Does that put other constraints on the way you’d write your algorithm?

6. Your version of template.cu.

7. The result as a table/graph of kernel execution times for different input data, with the systeminformation where you performed your evaluation. Run your implementation with the input generated by the provided dataset generator. For time measurement, use gpuTKTime start and gpuTKTime stop functions (You can find details in libgputk/README.md).
