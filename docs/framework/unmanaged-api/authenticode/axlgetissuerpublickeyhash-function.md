---
title: Função _AxlGetIssuerPublicKeyHash
ms.date: 03/30/2017
api_name:
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 252a3153a49867faf67051be01eeb141fa3ab681
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490340"
---
# <a name="axlgetissuerpublickeyhash-function"></a>Função _AxlGetIssuerPublicKeyHash
Recupera o hash SHA-1 da chave pública associada à chave privada usada para assinar o certificado especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pChainContext`  
 [in] O blob da chave pública CSP. Consulte a [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) estrutura.  
  
 `ppwszPublicKeyHash`  
 [out] Um ponteiro para WCHAR * para receber o token de chave pública com codificação hexadecimal.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` se a função for bem-sucedida; caso contrário, `S_FALSE`.  
  
## <a name="see-also"></a>Consulte também
- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
