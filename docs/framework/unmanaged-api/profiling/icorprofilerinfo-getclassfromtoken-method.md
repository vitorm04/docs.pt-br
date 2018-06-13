---
title: Método ICorProfilerInfo::GetClassFromToken
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b4b6b7b7b0dbb36724ff5eee2f3f78a3a7422cb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453327"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a>Método ICorProfilerInfo::GetClassFromToken
Obtém a ID da classe, recebe o token de metadados. Este método está obsoleto no .NET Framework versão 2.0. Use [Icorprofilerinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `moduleID`  
 [in] A ID do módulo que contém a classe.  
  
 `typeDef`  
 [in] Um `mdTypeDef` token de metadados que faz referência à classe.  
  
 `cTypeArgs`  
 [out] Um ponteiro para a ID de classe.  
  
## <a name="remarks"></a>Comentários  
 Este método é obsoleto; em vez disso, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` para todos os tipos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
