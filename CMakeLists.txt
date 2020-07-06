cmake_minimum_required(VERSION 3.11)

project(LiquidFun)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

if (MSVC)
	set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /O2 /DNDEBUG")
else()
	set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fno-rtti")
	set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -g -ggdb" )
	set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} -O3 -march=native -DNDEBUG -flto")
endif()

set(LIQUIDFUN_Collision_SRCS
	src/Collision/b2BroadPhase.cpp
	src/Collision/b2CollideCircle.cpp
	src/Collision/b2CollideEdge.cpp
	src/Collision/b2CollidePolygon.cpp
	src/Collision/b2Collision.cpp
	src/Collision/b2Distance.cpp
	src/Collision/b2DynamicTree.cpp
	src/Collision/b2TimeOfImpact.cpp
)
set(LIQUIDFUN_Collision_HDRS
	include/liquidfun/Collision/b2BroadPhase.h
	include/liquidfun/Collision/b2Collision.h
	include/liquidfun/Collision/b2Distance.h
	include/liquidfun/Collision/b2DynamicTree.h
	include/liquidfun/Collision/b2TimeOfImpact.h
)
set(LIQUIDFUN_Shapes_SRCS
	src/Collision/Shapes/b2CircleShape.cpp
	src/Collision/Shapes/b2EdgeShape.cpp
	src/Collision/Shapes/b2ChainShape.cpp
	src/Collision/Shapes/b2PolygonShape.cpp
)
set(LIQUIDFUN_Shapes_HDRS
	include/liquidfun/Collision/Shapes/b2CircleShape.h
	include/liquidfun/Collision/Shapes/b2EdgeShape.h
	include/liquidfun/Collision/Shapes/b2ChainShape.h
	include/liquidfun/Collision/Shapes/b2PolygonShape.h
	include/liquidfun/Collision/Shapes/b2Shape.h
)
set(LIQUIDFUN_Common_SRCS
	src/Common/b2BlockAllocator.cpp
	src/Common/b2Draw.cpp
	src/Common/b2FreeList.cpp
	src/Common/b2Math.cpp
	src/Common/b2Settings.cpp
	src/Common/b2StackAllocator.cpp
	src/Common/b2Stat.cpp
	src/Common/b2Timer.cpp
	src/Common/b2TrackedBlock.cpp
)
set(LIQUIDFUN_Common_HDRS
	include/liquidfun/Common/b2BlockAllocator.h
	include/liquidfun/Common/b2Draw.h
	include/liquidfun/Common/b2FreeList.h
	include/liquidfun/Common/b2GrowableStack.h
	include/liquidfun/Common/b2GrowableBuffer.h
	include/liquidfun/Common/b2IntrusiveList.h
	include/liquidfun/Common/b2Math.h
	include/liquidfun/Common/b2Settings.h
	include/liquidfun/Common/b2SlabAllocator.h
	include/liquidfun/Common/b2StackAllocator.h
	include/liquidfun/Common/b2Stat.h
	include/liquidfun/Common/b2Timer.h
	include/liquidfun/Common/b2TrackedBlock.h
)
set(LIQUIDFUN_Dynamics_SRCS
	src/Dynamics/b2Body.cpp
	src/Dynamics/b2ContactManager.cpp
	src/Dynamics/b2Fixture.cpp
	src/Dynamics/b2Island.cpp
	src/Dynamics/b2World.cpp
	src/Dynamics/b2WorldCallbacks.cpp
)
set(LIQUIDFUN_Dynamics_HDRS
	include/liquidfun/Dynamics/b2Body.h
	include/liquidfun/Dynamics/b2ContactManager.h
	include/liquidfun/Dynamics/b2Fixture.h
	include/liquidfun/Dynamics/b2Island.h
	include/liquidfun/Dynamics/b2TimeStep.h
	include/liquidfun/Dynamics/b2World.h
	include/liquidfun/Dynamics/b2WorldCallbacks.h
)
set(LIQUIDFUN_Contacts_SRCS
	src/Dynamics/Contacts/b2CircleContact.cpp
	src/Dynamics/Contacts/b2Contact.cpp
	src/Dynamics/Contacts/b2ContactSolver.cpp
	src/Dynamics/Contacts/b2PolygonAndCircleContact.cpp
	src/Dynamics/Contacts/b2EdgeAndCircleContact.cpp
	src/Dynamics/Contacts/b2EdgeAndPolygonContact.cpp
	src/Dynamics/Contacts/b2ChainAndCircleContact.cpp
	src/Dynamics/Contacts/b2ChainAndPolygonContact.cpp
	src/Dynamics/Contacts/b2PolygonContact.cpp
)
set(LIQUIDFUN_Contacts_HDRS
	include/liquidfun/Dynamics/Contacts/b2CircleContact.h
	include/liquidfun/Dynamics/Contacts/b2Contact.h
	include/liquidfun/Dynamics/Contacts/b2ContactSolver.h
	include/liquidfun/Dynamics/Contacts/b2PolygonAndCircleContact.h
	include/liquidfun/Dynamics/Contacts/b2EdgeAndCircleContact.h
	include/liquidfun/Dynamics/Contacts/b2EdgeAndPolygonContact.h
	include/liquidfun/Dynamics/Contacts/b2ChainAndCircleContact.h
	include/liquidfun/Dynamics/Contacts/b2ChainAndPolygonContact.h
	include/liquidfun/Dynamics/Contacts/b2PolygonContact.h
)
set(LIQUIDFUN_Joints_SRCS
	src/Dynamics/Joints/b2DistanceJoint.cpp
	src/Dynamics/Joints/b2FrictionJoint.cpp
	src/Dynamics/Joints/b2GearJoint.cpp
	src/Dynamics/Joints/b2Joint.cpp
	src/Dynamics/Joints/b2MouseJoint.cpp
	src/Dynamics/Joints/b2MotorJoint.cpp
	src/Dynamics/Joints/b2PrismaticJoint.cpp
	src/Dynamics/Joints/b2PulleyJoint.cpp
	src/Dynamics/Joints/b2RevoluteJoint.cpp
	src/Dynamics/Joints/b2RopeJoint.cpp
	src/Dynamics/Joints/b2WeldJoint.cpp
	src/Dynamics/Joints/b2WheelJoint.cpp
)
set(LIQUIDFUN_Joints_HDRS
	include/liquidfun/Dynamics/Joints/b2DistanceJoint.h
	include/liquidfun/Dynamics/Joints/b2FrictionJoint.h
	include/liquidfun/Dynamics/Joints/b2GearJoint.h
	include/liquidfun/Dynamics/Joints/b2Joint.h
	include/liquidfun/Dynamics/Joints/b2MotorJoint.h
	include/liquidfun/Dynamics/Joints/b2MouseJoint.h
	include/liquidfun/Dynamics/Joints/b2PrismaticJoint.h
	include/liquidfun/Dynamics/Joints/b2PulleyJoint.h
	include/liquidfun/Dynamics/Joints/b2RevoluteJoint.h
	include/liquidfun/Dynamics/Joints/b2RopeJoint.h
	include/liquidfun/Dynamics/Joints/b2WeldJoint.h
	include/liquidfun/Dynamics/Joints/b2WheelJoint.h
)
set(LIQUIDFUN_Particle_SRCS
	src/Particle/b2Particle.cpp
	src/Particle/b2ParticleAssembly.cpp
	src/Particle/b2ParticleGroup.cpp
	src/Particle/b2ParticleSystem.cpp
	src/Particle/b2VoronoiDiagram.cpp
)
set(LIQUIDFUN_Particle_HDRS
	include/liquidfun/Particle/b2Particle.h
	include/liquidfun/Particle/b2ParticleGroup.h
	include/liquidfun/Particle/b2ParticleSystem.h
	include/liquidfun/Particle/b2StackQueue.h
	include/liquidfun/Particle/b2VoronoiDiagram.h
)
set(LIQUIDFUN_Rope_SRCS
	src/Rope/b2Rope.cpp
)
set(LIQUIDFUN_Rope_HDRS
	include/liquidfun/Rope/b2Rope.h
)
set(LIQUIDFUN_General_HDRS
	include/liquidfun/LiquidFun.h
)

add_library(liquidfun STATIC
		${LIQUIDFUN_General_HDRS}
		${LIQUIDFUN_Joints_SRCS}
		${LIQUIDFUN_Joints_HDRS}
		${LIQUIDFUN_Contacts_SRCS}
		${LIQUIDFUN_Contacts_HDRS}
		${LIQUIDFUN_Dynamics_SRCS}
		${LIQUIDFUN_Dynamics_HDRS}
		${LIQUIDFUN_Common_SRCS}
		${LIQUIDFUN_Common_HDRS}
		${LIQUIDFUN_Shapes_SRCS}
		${LIQUIDFUN_Shapes_HDRS}
		${LIQUIDFUN_Collision_SRCS}
		${LIQUIDFUN_Collision_HDRS}
		${LIQUIDFUN_Particle_SRCS}
		${LIQUIDFUN_Particle_HDRS}
		${LIQUIDFUN_Rope_SRCS}
		${LIQUIDFUN_Rope_HDRS}
	)

if(UNIX AND NOT APPLE)
	target_link_libraries(liquidfun rt)
endif(UNIX AND NOT APPLE)
	
target_include_directories(liquidfun PUBLIC ${CMAKE_CURRENT_LIST_DIR}/include)

# These are used to create visual studio folders.
source_group(Collision FILES ${LIQUIDFUN_Collision_SRCS} ${LIQUIDFUN_Collision_HDRS})
source_group(Collision\\Shapes FILES ${LIQUIDFUN_Shapes_SRCS} ${LIQUIDFUN_Shapes_HDRS})
source_group(Common FILES ${LIQUIDFUN_Common_SRCS} ${LIQUIDFUN_Common_HDRS})
source_group(Dynamics FILES ${LIQUIDFUN_Dynamics_SRCS} ${LIQUIDFUN_Dynamics_HDRS})
source_group(Dynamics\\Contacts FILES ${LIQUIDFUN_Contacts_SRCS} ${LIQUIDFUN_Contacts_HDRS})
source_group(Dynamics\\Joints FILES ${LIQUIDFUN_Joints_SRCS} ${LIQUIDFUN_Joints_HDRS})
source_group(Include FILES ${LIQUIDFUN_General_HDRS})
source_group(Particle FILES ${LIQUIDFUN_Particle_SRCS} ${LIQUIDFUN_Particle_HDRS})
source_group(Rope FILES ${LIQUIDFUN_Rope_SRCS} ${LIQUIDFUN_Rope_HDRS})
