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
ms.openlocfilehash: 6d5ad995b55a3cde6363b297df6b8faf72689468
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132484"
---
# <a name="_axlgetissuerpublickeyhash-function"></a><span data-ttu-id="97d15-102">\_função AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="97d15-102">\_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="97d15-103">Recupera o hash SHA-1 da chave pública associada à chave privada usada para assinar o certificado especificado.</span><span class="sxs-lookup"><span data-stu-id="97d15-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97d15-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="97d15-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97d15-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="97d15-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="97d15-106">[in] O blob da chave pública CSP.</span><span class="sxs-lookup"><span data-stu-id="97d15-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="97d15-107">Consulte a estrutura [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="97d15-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="97d15-108">[out] Um ponteiro para WCHAR \* para receber o token de chave pública com codificação hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="97d15-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97d15-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="97d15-109">Return Value</span></span>  
 <span data-ttu-id="97d15-110">`S_OK` se a função for bem-sucedida; caso contrário, `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="97d15-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d15-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97d15-111">See also</span></span>

- [<span data-ttu-id="97d15-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="97d15-112">Authenticode</span></span>](index.md)
