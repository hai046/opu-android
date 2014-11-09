opu-android
===========

使用opus 编码音频


步骤

1，下载opus 源码 当前是1.1 版本 http://www.opus-codec.org/downloads/

2,编写Android.mk

LOCAL_PATH := $(call my-dir)
#// opus version=1.1  http://www.opus-codec.org/downloads/
include $(CLEAR_VARS)

LOCAL_MODULE        := libopus

LOCAL_C_INCLUDES    := \
    opus/include \
	opus/silk \
	opus/silk/fixed \
	opus/celt
	
LOCAL_SRC_FILES     := \
	$(wildcard opus/silk/*.c) \
	$(wildcard opus/silk/fixed/*.c) \
	$(wildcard opus/celt/*.c) \
	$(wildcard opus/src/*.c) \
	opusLib.c
    
    
LOCAL_LDLIBS        := -lm -llog

LOCAL_CFLAGS        := -DNULL=0 -DSOCKLEN_T=socklen_t -DLOCALE_NOT_USED -D_LARGEFILE_SOURCE=1 -D_FILE_OFFSET_BITS=64
LOCAL_CFLAGS    += -Drestrict='' -D__EMX__ -DOPUS_BUILD -DFIXED_POINT -DUSE_ALLOCA -DHAVE_LRINT -DHAVE_LRINTF -O3 -fno-math-errno
LOCAL_CPPFLAGS      := -DBSD=1 
LOCAL_CPPFLAGS          += -ffast-math -O3 -funroll-loops

include $(BUILD_SHARED_LIBRARY)


3,可以根据opus_demo.c编写对应编码和节目函数


4，调用jni

