---
title: "Função _AxlGetIssuerPublicKeyHash"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _AxlGetIssuerPublicKeyHash
api_location: clr.dll
api_type: DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 38be1f621425797e27fc41cb3192a628ebbfdb0c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="ed887-102">Função _AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="ed887-102">_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="ed887-103">Recupera o hash SHA-1 da chave pública associada à chave privada usada para assinar o certificado especificado.</span><span class="sxs-lookup"><span data-stu-id="ed887-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed887-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed887-104">Syntax</span></span>  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed887-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ed887-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="ed887-106">[in] O blob da chave pública CSP.</span><span class="sxs-lookup"><span data-stu-id="ed887-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="ed887-107">Consulte o [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) estrutura.</span><span class="sxs-lookup"><span data-stu-id="ed887-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="ed887-108">[out] Um ponteiro para WCHAR * para receber o token de chave pública com codificação hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="ed887-108">[out] A pointer to WCHAR * to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed887-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ed887-109">Return Value</span></span>  
 <span data-ttu-id="ed887-110">`S_OK` se a função for bem-sucedida; caso contrário, `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="ed887-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed887-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed887-111">See Also</span></span>  
 [<span data-ttu-id="ed887-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="ed887-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
