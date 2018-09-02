---
title: Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7f4fff4f2c2b3dd04625f4cf50b8b19a0ef6f39
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43415891"
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
|`pChainContext`|Contexto da cadeia do carimbo de hora.  Consulte a [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) estrutura.|  
  
## <a name="see-also"></a>Consulte também  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
