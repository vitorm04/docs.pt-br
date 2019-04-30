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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948931"
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="7e887-102">Função _AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="7e887-102">_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="7e887-103">Recupera o hash SHA-1 da chave pública associada à chave privada usada para assinar o certificado especificado.</span><span class="sxs-lookup"><span data-stu-id="7e887-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e887-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e887-104">Syntax</span></span>  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e887-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7e887-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="7e887-106">[in] O blob da chave pública CSP.</span><span class="sxs-lookup"><span data-stu-id="7e887-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="7e887-107">Consulte a [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) estrutura.</span><span class="sxs-lookup"><span data-stu-id="7e887-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="7e887-108">[out] Um ponteiro para WCHAR \* para receber o token de chave pública com codificação hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="7e887-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e887-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7e887-109">Return Value</span></span>  
 <span data-ttu-id="7e887-110">`S_OK` se a função for bem-sucedida; caso contrário, `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="7e887-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e887-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e887-111">See also</span></span>

- [<span data-ttu-id="7e887-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="7e887-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
