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
ms.openlocfilehash: 823cc5638ff3e0955aca0bd9ba5795f6b369c6b0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863602"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a>Método ICorProfilerInfo::GetFunctionInfo
Obtém a classe pai e o token de metadados para a função especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 no A ID da função para a qual obter a classe pai e o token de metadados.  
  
 `pClassId`  
 fora Um ponteiro para a classe pai da função.  
  
 `pModuleId`  
 fora Um ponteiro para o módulo no qual a classe pai da função é definida.  
  
 `pToken`  
 fora Um ponteiro para o token de metadados para a função.  
  
## <a name="remarks"></a>Comentários  
 O código do criador de perfil pode chamar [ICorProfilerInfo:: GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) para obter uma interface de metadados para um determinado módulo. O token de metadados que é retornado para o local referenciado por `pToken` pode ser usado para acessar os metadados para a função.  
  
 A `ClassID` de uma função em uma classe genérica talvez não possa ser obtida sem mais informações contextuais sobre o uso da função. Nesse caso, `pClassId` será 0. O código do criador de perfil deve usar [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) com um valor COR_PRF_FRAME_INFO para fornecer mais contexto.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo](icorprofilerinfo-interface.md)
