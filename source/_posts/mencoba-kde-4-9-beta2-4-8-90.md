---
title: Mencoba KDE 4.9 Beta2 (4.8.90)
date: 2012-06-18 07:44:01
categories:
    - linux
    - KDE
tags:
    - archlinux
    - KDE
keywords:
    - linux
    - archlinux
    - KDE
thumbnailImage: ./snapshot50.png
thumbnailImagePosition: right
---

Gara-gara komentar di [status](https://www.facebook.com/walesa/posts/4007252307182) Facebooknya om Walesa jadi kepengin menjajal [KDE 4.9 Beta2](http://www.kde.org/announcements/announce-4.9-beta2.php). Setelah semalaman ketiduran menunggu upgrade KDE, baru pagi ini saya punya kesempatan menjajalnya.
<!-- more -->

Ritual upgrade dengan `pacman -Syu` berjalan *lantjar djaja*. Namun, ketika saya masuk ke desktop ada hal yang tidak biasa. Hal yang saya temui adalah kwin tidak berjalan sebagaimana mestinya. Iseng-iseng saya jalankan ulang kwin dengan perintah `kwin --replace` ternyata ada masalah dengan kwin decoration. Kwin decoration yang saya pakai ternyata bukan **Oxygen** tetapi **Oxygen Transparent** dan itu biang keladinya. 😂

{% codeblock %}
┌─[archlinux]─[~/Documents]
└─[$] kwin --replace
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
kwin(3655) KWin::Extensions::init: Extensions: shape: 0x "11"  composite: 0x "4"  render: 0x "b"  fixes: 0x "50"  non_native_pixmaps:  true
kwin(3655) KDecorationPlugins::loadPlugin: kwin : path  "/usr/lib/kde4/kwin3_oxygen_transparent.so"  for  "kwin3_oxygen_transparent"
kwin(3655) KDecorationPlugins::loadPlugin: "******
 
The library /usr/lib/kde4/kwin3_oxygen_transparent.so has no API version
Please use the KWIN_DECORATION or future versions of kwin will no longer load this decoration!
*******"
kwin(3655) KWin::Workspace::updateClientArea: screens:  1 desktops:  2
kwin(3655) KWin::Workspace::updateClientArea: Done.
kwin(3655) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 440440
kwin(3655) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 31457766 ;WMCLASS: "plasma" : "plasma" ;Caption: "plasma-desktop" ' : 440440
kwin(3655) KWin::Workspace::allowClientActivation: Activation: No client active, allowing
kwin(3655) KWin::Workspace::updateClientArea: screens:  1 desktops:  2
kwin(3655) KWin::Workspace::updateClientArea: Done.
kwin(3655) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 4294967295
kwin(3655) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 31457775 ;WMCLASS: "plasma" : "plasma" ;Caption: "plasma-desktop" ' : 435517
kwin(3655) KWin::Workspace::allowClientActivation: Activation: No client active, allowing
kwin(3655) KWin::Workspace::updateClientArea: screens:  1 desktops:  2
kwin(3655) KWin::Workspace::updateClientArea: Done.
kwin(3655) KWin::Client::checkActivities: no activities!?!?
kwin(3655) KWin::Client::readUserTimeMapTimestamp: User timestamp, ASN: 455422
kwin(3655) KWin::Client::readUserTimeMapTimestamp: User timestamp, final: 'ID: 29360146 ;WMCLASS: "konsole" : "konsole" ;Caption: "~/Documents : kwin – Konsole" ' : 455422
kwin(3655) KWin::Workspace::allowClientActivation: Activation: No client active, allowing
kwin(3655) KWin::Workspace::updateClientArea: screens:  1 desktops:  2
kwin(3655) KWin::Workspace::updateClientArea: Done.
kwin(3655) KWin::Workspace::updateClientArea: screens:  1 desktops:  2
kwin(3655) KWin::Workspace::updateClientArea: Done.
kwin(3655) KWin::Workspace::slotCompositingOptionsInitialized: Initializing OpenGL compositing
kwin(3655) KWin::SceneOpenGL::initBufferConfigs: Drawable visual (depth  24 ): 0x "71"
kwin(3655) KWin::SceneOpenGL::initBufferConfigs: Drawable visual (depth  32 ): 0x "b4"
kwin(3655) KWin::SceneOpenGL::initBuffer: Buffer visual (depth  24 ): 0x "6f"
OpenGL vendor string:                   NVIDIA Corporation
OpenGL renderer string:                 GeForce 310M/PCIe/SSE2
OpenGL version string:                  3.3.0 NVIDIA 302.17
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
Driver:                                 NVIDIA
Driver version:                         302.17
GPU class:                              G80/G90
OpenGL version:                         3.3
GLSL version:                           3.30
X server version:                       1.12.2
Linux kernel version:                   3.4.2
Direct rendering:                       yes
Requires strict binding:                no
GLSL shaders:                           yes
Texture NPOT support:                   yes
kwin(3655) KWin::ShaderManager::initShaders: Ortho Shader is valid
kwin(3655) KWin::ShaderManager::initShaders: Generic Shader is valid
kwin(3655) KWin::ShaderManager::initShaders: Color Shader is valid
kwin(3655) KWin::SceneOpenGL::SceneOpenGL: DB: true , Direct: true
kwin(3655) KWin::currentRefreshRate: Vertical Refresh Rate (as detected by XF86VM):  59 Hz
kwin(3655) KWin::currentRefreshRate: Vertical Refresh rate  59 Hz
kwin(3655) KWin::EffectsHandlerImpl::loadEffect: Trying to load  "kwin4_effect_slidingpopups"
kwin(3655) KWin::EffectsHandlerImpl::loadEffect: Trying to load  "kwin4_effect_magiclamp"
kwin(3655) KWin::EffectsHandlerImpl::loadEffect: Trying to load  "kwin4_effect_blur"
kwin(3655) KWin::EffectsHandlerImpl::loadEffect: Trying to load  "kwin4_effect_desktopgrid"
kwin(3655) KWin::EffectsHandlerImpl::loadEffect: Trying to load  "kwin4_effect_fade"
kwin(3655) KWin::EffectsHandlerImpl::loadEffect: Trying to load  "kwin4_effect_slide"
kwin(3655) KWin::EffectsHandlerImpl::loadEffect: Trying to load  "kwin4_effect_presentwindows"
kwin(3655) KWin::EffectsHandlerImpl::loadEffect: Trying to load  "kwin4_effect_dashboard"
kwin(3655) KWin::EffectsHandlerImpl::loadEffect: Trying to load  "kwin4_effect_login"
kwin(3655) KWin::EffectsHandlerImpl::loadEffect: Trying to load  "kwin4_effect_startupfeedback"
kwin(3655) KWin::EffectsHandlerImpl::loadEffect: Trying to load  "kwin4_effect_outline"
kwin(3655) KWin::EffectsHandlerImpl::loadEffect: Trying to load  "kwin4_effect_boxswitch"
kwin(3655) KWin::EffectsHandlerImpl::loadEffect: Trying to load  "kwin4_effect_taskbarthumbnail"
kwin(3655) KWin::EffectsHandlerImpl::loadEffect: Trying to load  "kwin4_effect_screenshot"
kwin(3655) KWin::EffectsHandlerImpl::loadEffect: Trying to load  "kwin4_effect_translucency"
kwin(3655) KWin::EffectsHandlerImpl::loadEffect: Trying to load  "kwin4_effect_highlightwindow"
kwin(3655) KWin::EffectsHandlerImpl::loadEffect: Trying to load  "kwin4_effect_zoom"
kwin(3655) KWin::EffectsHandlerImpl::loadEffect: Trying to load  "kwin4_effect_dialogparent"
kwin: symbol lookup error: /usr/lib/kde4/kwin3_oxygen_transparent.so: undefined symbol: _ZNK25KCommonDecorationUnstable16clientGroupItemsEv
{% endcodeblock %}

Setelah menghapus berkas `kwinrc` di `$HOME/.kde4/share/config`, baru saya bisa masuk ke desktop KDE 4.9 Beta2 dengan sukses! 😀

{% image fancybox fig-100 ./snapshot52.png %}
{% image fancybox fig-50 ./snapshot51.png %}
{% image fancybox fig-50 clear ./snapshot50.png %}

Satu hal yang membuat saya cukup terkesan dengan KDE 4.9 Beta2  ini adalah loading yang super cepat dibanding dengan KDE seri 4.8.x. 👍🏽
