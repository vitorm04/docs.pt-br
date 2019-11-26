---
title: Interface ICorProfilerInfo2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2
helpviewer_keywords:
- ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: 91bd49b6-4d12-494f-a8f1-2f251e8c65e3
topic_type:
- apiref
ms.openlocfilehash: fdac9eedb0ae442d6dd2646859cab13398020a87
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449779"
---
# <a name="icorprofilerinfo2-interface"></a>Interface ICorProfilerInfo2
Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information. The `ICorProfilerInfo2` interface is an extension of the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface. That is, it provides new methods supported in the .NET Framework version 2.0 and later versions.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)|Walks the stack of the specified thread to report managed call frames to the profiler.|  
|[Método EnumModuleFrozenObjects](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)|Gets an enumerator that allows iteration over the frozen objects in the specified module.|  
|[Método GetAppDomainStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getappdomainstaticaddress-method.md)|Gets the address of the specified application domain-static field that is in the scope of the specified application domain.|  
|[Método GetArrayObjectInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getarrayobjectinfo-method.md)|Gets detailed information about an array object.|  
|[Método GetBoxClassLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getboxclasslayout-method.md)|Gets information about the class layout for a specified value type that is boxed.|  
|[Método GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.|  
|[Método GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)|Gets the parent module of the specified generic class, the metadata token for the class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.|  
|[Método GetClassLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclasslayout-method.md)|Gets information about the layout, in memory, of the fields defined by the specified class. That is, this method gets the offsets of the class's fields.|  
|[Método GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)|Gets the extents of native code associated with the specified `FunctionID`.|  
|[Método GetContextStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcontextstaticaddress-method.md)|Gets the address of the specified context-static field that is in the scope of the specified context.|  
|[Método GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.|  
|[Método GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)|Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.|  
|[Método GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md)|Gets the memory regions (the segments of the heap) that make up the generations of the garbage-collected heap.|  
|[Método GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.|  
|[Método GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md)|Gets the segment of the heap that contains the specified object.|  
|[Método GetRVAStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getrvastaticaddress-method.md)|Gets the address of the specified relative virtual address (RVA)-static field.|  
|[Método GetStaticFieldInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstaticfieldinfo-method.md)|Gets the scope in which the specified field is static.|  
|[Método GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)|Gets information about the layout of a string object.|  
|[Método GetThreadAppDomain](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)|Gets the ID of the application domain in which the specified thread is currently executing code.|  
|[Método GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)|Gets the address of the specified thread-static field that is in the scope of the specified thread.|  
|[Método SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.|  
  
## <a name="remarks"></a>Comentários  
 A profiler calls a method in the `ICorProfilerInfo2` interface to communicate with the CLR to control event monitoring and request information.  
  
 The methods of the `ICorProfilerInfo2` interface are implemented by the CLR using the free-threaded model. Each method returns an HRESULT to indicate success or failure. For a list of possible return codes, see the CorError.h file.  
  
 The CLR passes an `ICorProfilerInfo2` interface to each code profiler during initialization, using the profiler's implementation of [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). A code profiler can then call methods of the `ICorProfilerInfo2` interface to get information about managed code being executed under the control of the CLR.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
