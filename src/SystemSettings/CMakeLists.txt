set(QML_SOURCES
    ItemPage.qml
    SettingsItemTitle.qml
    USSAdaptivePageLayout.qml
)

set(PLUG_DIR ${PLUGIN_QML_DIR}/SystemSettings)
install(FILES qmldir DESTINATION ${PLUG_DIR})
install(FILES ${QML_SOURCES} DESTINATION ${PLUG_DIR})

add_subdirectory(ListItems)
