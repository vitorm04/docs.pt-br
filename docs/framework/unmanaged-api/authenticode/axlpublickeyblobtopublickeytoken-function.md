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
ms.openlocfilehash: 56333165d179abd79e82f1416342a2700029eb12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401668"
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="39136-102">Função _AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="39136-102">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="39136-103">Computa o token de chave pública do nome forte de um formato CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="39136-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39136-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39136-104">Syntax</span></span>  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39136-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="39136-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="39136-106">[in] O blob da chave pública CSP.</span><span class="sxs-lookup"><span data-stu-id="39136-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="39136-107">[out] Um ponteiro para WCHAR \* para receber o hash da chave pública com codificação hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="39136-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39136-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="39136-108">Return Value</span></span>  
 <span data-ttu-id="39136-109">`S_OK` se a função for bem-sucedida; caso contrário, `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="39136-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39136-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39136-110">See Also</span></span>  
 [<span data-ttu-id="39136-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="39136-111">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
