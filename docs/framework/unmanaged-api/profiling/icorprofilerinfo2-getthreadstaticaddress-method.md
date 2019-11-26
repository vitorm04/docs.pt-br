---
title: Método ICorProfilerInfo2::GetThreadStaticAddress
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type:
- apiref
ms.openlocfilehash: d44eae4da70418e2d4f398b2bacee1fb53d55b60
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443060"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a>Método ICorProfilerInfo2::GetThreadStaticAddress
Gets the address of the specified thread-static field that is in the scope of the specified thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `classId`  
 [in] The ID of the class that contains the requested thread-static field.  
  
 `fieldToken`  
 [in] The metadata token for the requested thread-static field.  
  
 `threadId`  
 [in] The ID of the thread that is the scope for the requested static field.  
  
 `ppAddress`  
 [out] A pointer to the address of the static field that is within the specified thread.  
  
## <a name="remarks"></a>Comentários  
 The `GetThreadStaticAddress` method may return one of the following:  
  
- A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.  
  
- The addresses of objects that may be in the garbage collection heap. These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.  
  
 Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
