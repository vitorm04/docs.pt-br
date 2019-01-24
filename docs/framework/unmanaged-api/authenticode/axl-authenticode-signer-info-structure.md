---
title: Estrutura AXL_AUTHENTICODE_SIGNER_INFO
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff50ee18dc3155bf784d6b752da8efc841aa6ce5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559431"
---
# <a name="axlauthenticodesignerinfo-structure"></a>Estrutura AXL_AUTHENTICODE_SIGNER_INFO
Define as informações sobre o signatário do Authenticode.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    LPCWSTR pwszHash  
    LPCWSTR pwszDescription;  
    LPCWSTR pwszDescriptionUrl;  
    PCCERT_CHAIN_CONTEXT pChainContext  
} AXL_AUTHENTICODE_SIGNER_INFO, * PAXL_AUTHENTICODE_SIGNER_INFO;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`cbSize`|O tamanho desta estrutura.|  
|`dwError`|O código de erro.|  
|`algHash`|O algoritmo hash.|  
|`pwszHash`|O hash.|  
|`pwszDescription`|A descrição.|  
|`pwszDescriptionUrl`|A URL da descrição.|  
|`pChainContext`|O contexto da cadeia do signatário. Consulte a [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) estrutura.|  
  
## <a name="see-also"></a>Consulte também
- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
