---
title: Função _AxlPublicKeyBlobToPublicKeyToken
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b2535441da173ee13653c68f25039fd1431261a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147427"
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="c697c-102">Função _AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="c697c-102">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="c697c-103">Computa o token de chave pública do nome forte de um formato CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="c697c-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c697c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c697c-104">Syntax</span></span>  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c697c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c697c-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="c697c-106">[in] O blob da chave pública CSP.</span><span class="sxs-lookup"><span data-stu-id="c697c-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="c697c-107">[out] Um ponteiro para WCHAR \* para receber o hash da chave pública com codificação hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="c697c-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c697c-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c697c-108">Return Value</span></span>  
 <span data-ttu-id="c697c-109">`S_OK` se a função for bem-sucedida; caso contrário, `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="c697c-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c697c-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c697c-110">See also</span></span>

- [<span data-ttu-id="c697c-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="c697c-111">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
