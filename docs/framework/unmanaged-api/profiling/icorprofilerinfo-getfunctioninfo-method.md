---
title: Método ICorProfilerInfo::GetFunctionInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19736d177639b00c9563462f10e33e4c122297c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a>Método ICorProfilerInfo::GetFunctionInfo
Obtém a classe pai e os metadados de token para a função especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função para a qual obter a classe pai e os metadados de token.  
  
 `pClassId`  
 [out] Um ponteiro para a classe pai da função.  
  
 `pModuleId`  
 [out] Um ponteiro para o módulo no qual a classe do pai da função é definido.  
  
 `pToken`  
 [out] Um ponteiro para o token de metadados para a função.  
  
## <a name="remarks"></a>Comentários  
 O criador de perfil código pode chamar [Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) para obter uma interface de metadados para um determinado módulo. O token de metadados que é retornado para o local referenciado pelo `pToken` , em seguida, pode ser usado para acessar os metadados para a função.  
  
 O `ClassID` de uma função em uma classe genérica pode não ser obtido sem mais informações contextuais sobre o uso da função. Nesse caso, `pClassId` será 0. Criador de perfil código deve usar [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) com um valor COR_PRF_FRAME_INFO para fornecer mais contexto.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
