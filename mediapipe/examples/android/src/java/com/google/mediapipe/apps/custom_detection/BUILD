
licenses(["notice"])

package(default_visibility = ["//visibility:private"])

cc_binary(
    name = "libmediapipe_jni.so",
    linkshared = 1,
    linkstatic = 1,
    deps = [
        "//mediapipe/graphs/facemesh_and_iris_tracking:gpu_tracking_calculator",
        "//mediapipe/java/com/google/mediapipe/framework/jni:mediapipe_framework_jni",
    ],
)

cc_library(
    name = "mediapipe_jni_lib",
    srcs = [":libmediapipe_jni.so"],
    alwayslink = 1,
)

android_binary(
    name = "customtrackinggpu",
    srcs = glob(["*.java"]),
    assets = [
        "//mediapipe/graphs/facemesh_and_iris_tracking:face_mesh_and_iris_mobile.binarypb",
        "//mediapipe/modules/face_landmark:face_landmark.tflite",
        "//mediapipe/modules/iris_landmark:iris_landmark.tflite",
        "//mediapipe/modules/face_detection:face_detection_short_range.tflite",
        "//mediapipe/modules/face_geometry/data:geometry_pipeline_metadata_landmarks.binarypb",
    ],
    assets_dir = "",
    manifest = "//mediapipe/examples/android/src/java/com/google/mediapipe/apps/basic:AndroidManifest.xml",
    manifest_values = {
        "applicationId": "com.google.mediapipe.apps.customtrackinggpu",
        "appName": "Custom Tracking",
        "mainActivity": ".MainActivity",
        "cameraFacingFront": "True",
        "binaryGraphName": "face_mesh_and_iris_mobile.binarypb",
        "inputVideoStreamName": "input_video",
        "outputVideoStreamName": "output_video",
        "flipFramesVertically": "True",
        "converterNumBuffers": "2",
    },
    multidex = "native",
    deps = [
        ":mediapipe_jni_lib",
        "//mediapipe/examples/android/src/java/com/google/mediapipe/apps/basic:basic_lib",
        "//mediapipe/framework/formats:landmark_java_proto_lite",
        "//mediapipe/framework/formats:matrix_data_java_proto_lite",
        "//mediapipe/java/com/google/mediapipe/framework:android_framework",
        "//mediapipe/modules/face_geometry/protos:face_geometry_java_proto_lite",
        "@com_google_protobuf//:protobuf_javalite",
    ],
)

# load("//mediapipe/java/com/google/mediapipe:mediapipe_aar.bzl", "mediapipe_aar")

# mediapipe_aar(
#     name = "custom_detection",
#     calculators = [
#       "//mediapipe/graphs/facemesh_and_iris_tracking:gpu_tracking_calculator",
#     ],
# )
