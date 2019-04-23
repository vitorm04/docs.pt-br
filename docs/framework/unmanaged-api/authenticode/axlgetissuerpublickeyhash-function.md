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
ms.openlocfilehash: 448712561f1531a055ac141db9825581525c779c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106698"
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="a3808-102">Função _AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="a3808-102">_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="a3808-103">Recupera o hash SHA-1 da chave pública associada à chave privada usada para assinar o certificado especificado.</span><span class="sxs-lookup"><span data-stu-id="a3808-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3808-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3808-104">Syntax</span></span>  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3808-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a3808-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="a3808-106">[in] O blob da chave pública CSP.</span><span class="sxs-lookup"><span data-stu-id="a3808-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="a3808-107">Consulte a [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) estrutura.</span><span class="sxs-lookup"><span data-stu-id="a3808-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="a3808-108">[out] Um ponteiro para WCHAR \* para receber o token de chave pública com codificação hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="a3808-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3808-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a3808-109">Return Value</span></span>  
 <span data-ttu-id="a3808-110">`S_OK` se a função for bem-sucedida; caso contrário, `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="a3808-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3808-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3808-111">See also</span></span>

- [<span data-ttu-id="a3808-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="a3808-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
