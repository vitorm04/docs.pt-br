---
title: "Método ICorProfilerInfo::GetInprocInspectionIThisThread"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetInprocInspectionIThisThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9a260143e36939f4201d7949f5783f80e5c20ba7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a>Método ICorProfilerInfo::GetInprocInspectionIThisThread
Obtém um objeto que pode ser consultado para a interface ICorDebugThread. Este método está obsoleto no .NET Framework versão 2.0.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppicd`  
 [out](/cpp/atl/iunknown) objeto que pode ser consultado para o `ICorDebugThread` interface.  
  
## <a name="remarks"></a>Comentários  
 O common language runtime (CLR) serviços de depuração tem suporte limitado em processo depuração do .NET Framework versão 1.0. No processo de depuração habilitado um criador de perfil usar as partes de inspeção da API de depuração. Como resultado de comentários do cliente, no processo de depuração foi removido do .NET Framework versão 2.0 e substituído por um conjunto de funcionalidades mais alinhados com a API de criação de perfil.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versão do .NET framework:** 1.0  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
