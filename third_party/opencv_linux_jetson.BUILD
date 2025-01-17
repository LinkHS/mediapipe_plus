# Description:
#   OpenCV libraries for video/image processing on Linux

licenses(["notice"])  # BSD license

exports_files(["LICENSE"])

config_setting(
    name = "jetson-l4t-aarch64",
    values = {
        "cpu": "aarch64",
    },
    visibility = ["//visibility:public"],
)

# The following build rule assumes that OpenCV is installed by
# 'apt-get install libopencv-core-dev libopencv-highgui-dev \'
# '                libopencv-calib3d-dev libopencv-features2d-dev \'
# '                libopencv-imgproc-dev libopencv-video-dev'
# on Debian buster/Ubuntu 18.04.
# If you install OpenCV separately, please modify the build rule accordingly.
cc_library(
    name = "opencv",
    srcs = select({
        ":jetson-l4t-aarch64":  glob( 
            [
                "lib/jetson-l4t-aarch64/libopencv_core.so",
                "lib/jetson-l4t-aarch64/libopencv_dnn.so",
                "lib/jetson-l4t-aarch64/libopencv_calib3d.so",
                "lib/jetson-l4t-aarch64/libopencv_features2d.so",
                "lib/jetson-l4t-aarch64/libopencv_flann.so",
                "lib/jetson-l4t-aarch64/libopencv_highgui.so",
                "lib/jetson-l4t-aarch64/libopencv_imgcodecs.so",
                "lib/jetson-l4t-aarch64/libopencv_imgproc.so",
                "lib/jetson-l4t-aarch64/libopencv_ml.so",
                "lib/jetson-l4t-aarch64/libopencv_objdetect.so",
                "lib/jetson-l4t-aarch64/libopencv_photo.so",
                "lib/jetson-l4t-aarch64/libopencv_shape.so",
                "lib/jetson-l4t-aarch64/libopencv_stitching.so",
                "lib/jetson-l4t-aarch64/libopencv_superres.so",
                "lib/jetson-l4t-aarch64/libopencv_videoio.so",
                "lib/jetson-l4t-aarch64/libopencv_video.so",
                "lib/jetson-l4t-aarch64/libopencv_videostab.so",
            ]
        ),
         "//conditions:default": glob(
            [
                "lib/x86_64-linux-gnu/libopencv_core.so",
                "lib/x86_64-linux-gnu/libopencv_calib3d.so",
                "lib/x86_64-linux-gnu/libopencv_features2d.so",
                "lib/x86_64-linux-gnu/libopencv_highgui.so",
                "lib/x86_64-linux-gnu/libopencv_imgcodecs.so",
                "lib/x86_64-linux-gnu/libopencv_imgproc.so",
                "lib/x86_64-linux-gnu/libopencv_video.so",
                "lib/x86_64-linux-gnu/libopencv_videoio.so",
            ],
         )
    }),  
    hdrs = glob([
        # For OpenCV 3.x
        "include/opencv2/**/*.h*",
        "include/opencv2/*.h*",
        # For OpenCV 4.x
        # "include/opencv4/opencv2/**/*.h*",
    ]),
    includes = [
        # For OpenCV 3.x
        "include/",
        # For OpenCV 4.x
        # "include/opencv4/",
    ],
    linkstatic = 1,
    visibility = ["//visibility:public"],
)

