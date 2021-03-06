include_directories(${GLIB_INCLUDE_DIRS} ${GEONAMES_INCLUDE_DIRS})

add_definitions(-DQT_NO_KEYWORDS)

set(QML_SOURCES ChooseTimeZone.qml PageComponent.qml Scroller.qml TimePicker.qml)

add_library(UbuntuTimeDatePanel MODULE plugin.h
  timedate.h
  timezonelocationmodel.h
  plugin.cpp
  timedate.cpp
  timezonelocationmodel.cpp
  ${QML_SOURCES}
)
qt5_use_modules(UbuntuTimeDatePanel Qml Quick DBus Concurrent)
target_link_libraries(UbuntuTimeDatePanel ${GLIB_LDFLAGS} ${GEONAMES_LDFLAGS})


set(PLUG_DIR ${PLUGIN_PRIVATE_MODULE_DIR}/Ubuntu/SystemSettings/TimeDate)
install(TARGETS UbuntuTimeDatePanel DESTINATION ${PLUG_DIR})
install(FILES qmldir DESTINATION ${PLUG_DIR})
install(FILES ${QML_SOURCES} DESTINATION ${PLUGIN_QML_DIR}/time-date)

install(FILES time-date.settings DESTINATION ${PLUGIN_MANIFEST_DIR})
install(FILES settings-time-date.svg DESTINATION ${PLUGIN_MANIFEST_DIR}/icons)
