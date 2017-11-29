---
title: "Método IGCHost::GetThreadStats"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost.GetThreadStats
api_location: mscoree.dll
api_type: COM
f1_keywords: GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7bfd6b89c3220e071a477e0c5b85e4ee57289762
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="igchostgetthreadstats-method"></a>Método IGCHost::GetThreadStats
Obtém as estatísticas por thread de coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pFiberCookie`  
 [in] Um ponteiro para um cookie de fibra que especifica o thread para o qual recuperar as estatísticas.  
  
 `pStats`  
 [out no] Um ponteiro para um [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) estrutura que contém as estatísticas de coleta de lixo para o segmento especificado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** GCHost.idl, GCHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IGCHost](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
