cmake_minimum_required(VERSION 3.8)
project(robot_interfaces)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

set(interface_files
  # Messages
  "msg/Num.msg"
  "msg/Token.msg"
  "msg/InforSevt.msg"
  "msg/LocationStock.msg"
  "msg/LocationSent.msg"
  "msg/MissionTransport.msg"
  "msg/MissionCurrent.msg"
  "msg/CollisionPresent.msg"
  "srv/AddThreeInts.srv"
  "srv/CreatMission.srv"
  "srv/SearchStock.srv"
  "srv/ExcuteMission.srv"
  "srv/CommandApi.srv"
  "srv/GetInformation.srv"
  "srv/Collision.srv"
  "srv/CommonRequest.srv"
)

rosidl_generate_interfaces(${PROJECT_NAME}
  ${interface_files}
  DEPENDENCIES
  geometry_msgs
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
