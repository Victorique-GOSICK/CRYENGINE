#START-FILE-LIST
# File List auto generated by waf2cmake.py, do not modify manually.

start_sources()
# -- stdenv.waf_files --
sources_platform(ALL)
add_sources("NoUberFile"
	SOURCE_GROUP "Impl"
		"StdAfx.cpp"
		"StdAfx.h"
)

add_sources("Schematyc_Uber_STDEnv_0.cpp"
	SOURCE_GROUP "Interface"
		"../Interface/Schematyc/ISTDEnv.h"
	SOURCE_GROUP "Interface\\\\Entity"
		"../Interface/Schematyc/Entity/EntityClasses.h"
		"../Interface/Schematyc/Entity/EntityUpdateFilters.h"
		"../Interface/Schematyc/Entity/EntityUserData.h"
		"../Interface/Schematyc/Entity/EntityUtils.h"
		"../Interface/Schematyc/Entity/IEntityObject.h"
	SOURCE_GROUP "Interface\\\\Types"
		"../Interface/Schematyc/Types/BasicTypes.h"
		"../Interface/Schematyc/Types/MathTypes.h"
		"../Interface/Schematyc/Types/ResourceTypes.h"
)

add_sources("Schematyc_Uber_STDEnv_1.cpp"
	SOURCE_GROUP "Impl"
		"AutoRegister.cpp"
		"AutoRegister.h"
		"STDEnv.cpp"
		"STDEnv.h"
		"STDModules.cpp"
		"STDModules.h"
	SOURCE_GROUP "Impl\\\\Entity"
		"Entity/EntityClassProperties.cpp"
		"Entity/EntityClassProperties.h"
		"Entity/EntityObjectClassRegistry.cpp"
		"Entity/EntityObjectClassRegistry.h"
		"Entity/EntityObjectComponent.cpp"
		"Entity/EntityObjectComponent.h"
		"Entity/EntityObjectDebugger.cpp"
		"Entity/EntityObjectDebugger.h"
		"Entity/EntityObjectMap.cpp"
		"Entity/EntityObjectMap.h"
		"Entity/EntityObjectPreviewer.cpp"
		"Entity/EntityObjectPreviewer.h"
	SOURCE_GROUP "Impl\\\\Entity\\\\Actions"
		
	SOURCE_GROUP "Impl\\\\Entity\\\\Components"
		"Entity/Components/EntityAudioComponent.cpp"
		"Entity/Components/EntityAudioComponent.h"
		"Entity/Components/EntityCameraControllerComponent.cpp"
		"Entity/Components/EntityCameraControllerComponent.h"
		"Entity/Components/EntityDebugComponent.cpp"
		"Entity/Components/EntityDebugComponent.h"
		"Entity/Components/EntityGeomComponent.cpp"
		"Entity/Components/EntityGeomComponent.h"
		"Entity/Components/EntityInputComponent.cpp"
		"Entity/Components/EntityInputComponent.h"
		"Entity/Components/EntityLightComponent.cpp"
		"Entity/Components/EntityLightComponent.h"
		"Entity/Components/EntityMovementComponent.cpp"
		"Entity/Components/EntityMovementComponent.h"
		"Entity/Components/EntityParticleEmitterComponent.cpp"
		"Entity/Components/EntityParticleEmitterComponent.h"
		"Entity/Components/EntityPhysicsComponent.cpp"
		"Entity/Components/EntityPhysicsComponent.h"
		"Entity/Components/EntityUtilsComponent.cpp"
		"Entity/Components/EntityUtilsComponent.h"
	SOURCE_GROUP "Impl\\\\Entity\\\\Functions"
		"Entity/Functions/EntityUtilFunctions.cpp"
	SOURCE_GROUP "Impl\\\\Functions"
		"Functions/BasicFunctions.cpp"
		"Functions/LogFunctions.cpp"
		"Functions/MathFunctions.cpp"
	SOURCE_GROUP "Impl\\\\Types"
		"Types/BasicTypes.cpp"
		"Types/MathTypes.cpp"
		"Types/ResourceTypes.cpp"
	SOURCE_GROUP "Impl\\\\Utils"
		"Utils/SystemStateMonitor.cpp"
		"Utils/SystemStateMonitor.h"
)

end_sources()
#END-FILE-LIST

if(PLUGIN_SCHEMATYC)
	CryEngineModule(CrySchematycSTDEnv PCH "StdAfx.cpp" SOLUTION_FOLDER "CryEngine/CrySchematyc")
	target_compile_definitions(${THIS_PROJECT}
	PRIVATE
		-DSCHEMATYC_EXPORTS INTERFACE
		-DUSE_SCHEMATYC_STD_ENV
	)
	target_link_libraries (${THIS_PROJECT} PRIVATE yasli)
	target_include_directories(${THIS_PROJECT}
	PRIVATE
		${CRYENGINE_DIR}/Code/CryEngine/CryAction
		${CRYENGINE_DIR}/Code/CryExtensions/CryLink/Interface
		${CRYENGINE_DIR}/Code/CryEngine/CrySchematyc/Core/Interface
	PUBLIC 
		../Interface
	)
	if(LINUX)
		target_compile_options(${THIS_PROJECT} PRIVATE -fPIC)
	endif()
endif()
