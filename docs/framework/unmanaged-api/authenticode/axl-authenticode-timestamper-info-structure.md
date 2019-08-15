---
title: Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9eef89c9e560da65d670ffe59649b44a64f8da6a
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039604"
---
# <a name="axl_authenticode_timestamper_info-structure"></a>Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO
Define as informações sobre o carimbo de data/hora do Authenticode.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
|`pChainContext`|Contexto da cadeia do carimbo de hora.  Consulte a estrutura [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) .|  
  
## <a name="see-also"></a>Consulte também

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
