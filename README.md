ccv15_dvn
=========

This is the full "CCV v1.5" project, plus a new add-on thath allows to establish 
a inter-process comunication, so the input video stream can be generated by a custom app.

The custom project solution file is ubicated on the folder "ccv15_dvn/apps/ccv15_dvn/ccv15_VS2008_dvn/"
there is the visual studio 2008 project that compiles the current project implementation.

This vertion of "CCV v1.5" runs in the same way and has the same characteristics as the original version.
To put the program to run in SOCKET_STREAM mode you need to  find the file "data/xml/app_settings.xml"
and edit the "<SOURCE>" property and put its value to "IN_SOCKET".

The port used for the streaming can be configured editing the property "\<IN_SOCKET_PORT\>" of the same file.
Note:	The connection is made via TCP

After the file edition run the program and the program will wait until the socket image streaming begin.

The image streaming must follow this format 

1)Heder:	'<<<'

2)packagesize:	int (4 chars) (image_Width+image_Height+image_data)

3)image_Width:	word (2 chars)

4)image_Height:	word (2 chars)

5)image_data:	(packagesize-4 chars)  (The image format must be 24 bit: rgb)


Example
		<<<sssswwhhdddddddddddddddd.....ddddd									
		|_||__|||||________________________|									
		 1   2 3 4             5



Note:
	Although this protocol allows a change the size of the image at any time wile the image are being streamed.
	The implementation of this program does not allow to change the size of the images.
	So the images size are defined on the streamer side but that size must remain fixed during the streaming.
	


