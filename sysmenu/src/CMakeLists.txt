add_definitions(-DTRANSLATION_DOMAIN=\"plasma_applet_org.airyx.plasma.AiryxMenu\")

set(sysmenu_SRCS
    sysmenu.mm
)
add_library(plasma_applet_AiryxMenu MODULE ${sysmenu_SRCS})

kcoreaddons_desktop_to_json(plasma_applet_AiryxMenu package/metadata.desktop SERVICE_TYPES plasma-applet.desktop)

target_link_libraries(plasma_applet_AiryxMenu
    Qt5::DBus
    Qt5::Widgets
    KF5::Plasma
    KF5::I18n
    KF5::KIOCore KF5::KIOFileWidgets KF5::KIOWidgets KF5::KIONTLM
    "-framework LaunchServices"
    "-framework Foundation"
    "-framework CoreFoundation"
    "-framework CFNetwork"
    "-lobjc"
    "-lSystem"
    )


install(TARGETS plasma_applet_AiryxMenu DESTINATION ${KDE_INSTALL_PLUGINDIR}/plasma/applets)

plasma_install_package(package org.airyx.plasma.AiryxMenu)
