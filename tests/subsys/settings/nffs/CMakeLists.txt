include($ENV{ZEPHYR_BASE}/cmake/app/boilerplate.cmake NO_POLICY_SCOPE)
project(NONE)

FILE(GLOB app_sources src/*.c ../src/*c)
target_sources(app PRIVATE ${app_sources})
zephyr_include_directories(
	$ENV{ZEPHYR_BASE}/subsys/settings/include
	$ENV{ZEPHYR_BASE}/subsys/settings/src
	$ENV{ZEPHYR_BASE}/tests/subsys/settings/nffs/src
	)

if(TEST)
	target_compile_definitions(app PRIVATE
		-DTEST_${TEST}
		)
endif()
