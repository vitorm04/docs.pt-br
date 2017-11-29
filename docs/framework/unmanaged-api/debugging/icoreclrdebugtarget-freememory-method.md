---
title: "Método ICoreClrDebugTarget::FreeMemory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreDebugTarget.FreeMemory
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget::FreeMemory
helpviewer_keywords:
- remote debugging API [Silverlight]
- FreeMemory method, ICoreClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::FreeMemory method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 98f2a0db-a6ec-4f9b-861d-f82485237d08
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7b199d3a3406a1a1dd21a560424ef342b03ce6c2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icoreclrdebugtargetfreememory-method"></a>Método ICoreClrDebugTarget::FreeMemory
Libera a memória alocada pelo [Icoreclrdebugtarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) e [: Enumruntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) métodos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pMemory`  
 [in] Um ponteiro para a matriz que é retornado pelo [Icoreclrdebugtarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) ou [: Enumruntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Biblioteca:** mscordbi_macx86.dll  
  
 **Versões do .NET framework:** 3.5 SP1  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
