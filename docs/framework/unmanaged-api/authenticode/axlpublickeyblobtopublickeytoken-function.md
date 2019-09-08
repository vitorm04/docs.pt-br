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
ms.openlocfilehash: b4d720480e4c8b21b3aa56ce81634a26ac9c75de
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776678"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="0c8cc-102">\_Função AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="0c8cc-102">\_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="0c8cc-103">Computa o token de chave pública do nome forte de um formato CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="0c8cc-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c8cc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c8cc-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c8cc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0c8cc-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="0c8cc-106">[in] O blob da chave pública CSP.</span><span class="sxs-lookup"><span data-stu-id="0c8cc-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="0c8cc-107">[out] Um ponteiro para WCHAR \* para receber o hash da chave pública com codificação hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="0c8cc-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c8cc-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0c8cc-108">Return Value</span></span>  
 <span data-ttu-id="0c8cc-109">`S_OK` se a função for bem-sucedida; caso contrário, `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="0c8cc-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c8cc-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c8cc-110">See also</span></span>

- [<span data-ttu-id="0c8cc-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="0c8cc-111">Authenticode</span></span>](index.md)
