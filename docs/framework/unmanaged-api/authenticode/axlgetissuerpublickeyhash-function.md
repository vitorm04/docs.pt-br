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
ms.openlocfilehash: 1cfc2f5cde22bf63275dd4bdc65857ac1d51b3fe
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038427"
---
# <a name="_axlgetissuerpublickeyhash-function"></a><span data-ttu-id="a291e-102">\_Função AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="a291e-102">\_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="a291e-103">Recupera o hash SHA-1 da chave pública associada à chave privada usada para assinar o certificado especificado.</span><span class="sxs-lookup"><span data-stu-id="a291e-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a291e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a291e-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a291e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a291e-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="a291e-106">[in] O blob da chave pública CSP.</span><span class="sxs-lookup"><span data-stu-id="a291e-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="a291e-107">Consulte a estrutura [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="a291e-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="a291e-108">[out] Um ponteiro para WCHAR \* para receber o token de chave pública com codificação hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="a291e-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a291e-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a291e-109">Return Value</span></span>  
 <span data-ttu-id="a291e-110">`S_OK` se a função for bem-sucedida; caso contrário, `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="a291e-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a291e-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a291e-111">See also</span></span>

- [<span data-ttu-id="a291e-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="a291e-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
