---
title: Método ICorProfilerInfo::GetModuleInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
ms.openlocfilehash: aae6d33166a7685e07c4d82f654f803600e37eec
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438896"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a>Método ICorProfilerInfo::GetModuleInfo
Given a module ID, returns the file name of the module and the ID of the module's parent assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `moduleId`  
 [in] The ID of the module for which information will be retrieved.  
  
 `ppBaseLoadAddress`  
 [out] The base address at which the module is loaded.  
  
 `cchName`  
 [in] The length, in characters, of the `szName` return buffer.  
  
 `pcchName`  
 [out] A pointer to the total character length of the module's file name that is returned.  
  
 `szName`  
 [out] A caller-provided wide character buffer. When the method returns, this buffer contains the file name of the module.  
  
 `pAssemblyId`  
 [out] A pointer to the ID of the module's parent assembly.  
  
## <a name="remarks"></a>Comentários  
 For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).  
  
 Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.  
  
 When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module. To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter. If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.  
  
 Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size. You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
- [Método GetModuleInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
