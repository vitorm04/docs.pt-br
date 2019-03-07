---
title: Método ICorProfilerInfo::GetInprocInspectionIThisThread
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1bcf52a3745b22df58e67e892bf3a2b77c542d43
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478993"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a>Método ICorProfilerInfo::GetInprocInspectionIThisThread
Obtém um objeto que pode ser consultado para a interface ICorDebugThread. Este método é obsoleto no .NET Framework versão 2.0.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppicd`  
 [-out](/cpp/atl/iunknown) objeto que pode ser consultado para o `ICorDebugThread` interface.  
  
## <a name="remarks"></a>Comentários  
 O common language runtime (CLR) depurando serviços de suporte para depuração em andamento limitados no .NET Framework versão 1.0. No processo de depuração habilitado um criador de perfil usar as partes de inspeção da API de depuração. Como resultado de comentários do cliente, no processo de depuração foi removido do .NET Framework versão 2.0 e substituída por um conjunto de funcionalidade que é mais alinhada com a API de criação de perfil.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versão do .NET framework:** 1.0  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
