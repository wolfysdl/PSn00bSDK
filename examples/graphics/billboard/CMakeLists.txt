# PSn00bSDK example CMake script
# (C) 2021 spicyjpeg - MPL licensed

cmake_minimum_required(VERSION 3.20)

project(
	billboard
	LANGUAGES    C ASM
	VERSION      1.0.0
	DESCRIPTION  "PSn00bSDK billboard sprite example"
	HOMEPAGE_URL "http://lameguy64.net/?page=psn00bsdk"
)

configure_file(tim.s.template tim.s)

file(GLOB _sources *.c)
psn00bsdk_add_executable(
	billboard STATIC
	${_sources}
	${PROJECT_BINARY_DIR}/tim.s
)
#psn00bsdk_add_cd_image(billboard_iso billboard iso.xml DEPENDS billboard)

install(FILES ${PROJECT_BINARY_DIR}/billboard.exe TYPE BIN)
