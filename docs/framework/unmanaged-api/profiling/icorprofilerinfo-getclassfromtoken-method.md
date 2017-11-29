---
title: "Método ICorProfilerInfo::GetClassFromToken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetClassFromToken
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 761c537f0b3aba529a8a3a862a1a975ddd1c6303
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
