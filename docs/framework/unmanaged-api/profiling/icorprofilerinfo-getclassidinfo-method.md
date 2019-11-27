---
title: Método ICorProfilerInfo::GetClassIDInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassIDInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassIDInfo
helpviewer_keywords:
- GetClassIDInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetClassIDInfo method [.NET Framework profiling]
ms.assetid: 9e93b99e-5aca-415c-8e37-7f33753b612d
topic_type:
- apiref
ms.openlocfilehash: c3b1bdac8ccd37cf2f6aac5073def313f04acf28
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439240"
---
# <a name="icorprofilerinfogetclassidinfo-method"></a>Método ICorProfilerInfo::GetClassIDInfo
Obtém o módulo pai e o token de metadados para a classe especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `classId`  
 no A ID da classe para a qual obter as informações.  
  
 `pModuleId`  
 fora Um ponteiro para a ID do módulo pai da classe.  
  
 `pTypeDefToken`  
 fora Um ponteiro para o token de metadados para a classe.  
  
## <a name="remarks"></a>Comentários  
 O código do criador de perfil pode chamar [ICorProfilerInfo:: GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) para obter uma interface de metadados para um determinado módulo. O token de metadados que é retornado para o local referenciado por `pTypeDefToken` pode ser usado para acessar os metadados da classe.  
  
 Para obter mais informações sobre tipos genéricos, use [ICorProfilerInfo2:: GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
