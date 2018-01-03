---
title: Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46c0646cfff79888db2b6b37184dd97da21e71e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="axlauthenticodetimestamperinfo-structure"></a>Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO
Define as informações sobre o carimbo de data/hora do Authenticode.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`cbSize`|O tamanho desta estrutura.|  
|`dwError`|O código de erro.|  
|`algHash`|O algoritmo hash.|  
|`ftTimestamp`|A hora do carimbo de data/hora.|  
|`pChainContext`|Contexto da cadeia do carimbo de hora.  Consulte o [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) estrutura.|  
  
## <a name="see-also"></a>Consulte também  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
