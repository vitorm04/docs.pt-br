---
title: "Função _AxlRSAKeyValueToPublicKeyToken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _AxlRSAKeyValueToPublicKeyToken
api_location: clr.dll
api_type: DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4af27a2abf1a0bcf4d79eda389c5f79f0ecb1eef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="06da9-102">Função _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="06da9-102">_AxlRSAKeyValueToPublicKeyToken Function</span></span>
<span data-ttu-id="06da9-103">Converte um Módulo e um Expoente em um token de chave pública com nome forte.</span><span class="sxs-lookup"><span data-stu-id="06da9-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06da9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06da9-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06da9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="06da9-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="06da9-106">[in] O blob de módulo codificado na base64 (da \<módulo > elemento).</span><span class="sxs-lookup"><span data-stu-id="06da9-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="06da9-107">Consulte o [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) estrutura.</span><span class="sxs-lookup"><span data-stu-id="06da9-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="06da9-108">[in] O blob de expoente codificado na base64 (da \<expoente > elemento).</span><span class="sxs-lookup"><span data-stu-id="06da9-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="06da9-109">Consulte o [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) estrutura.</span><span class="sxs-lookup"><span data-stu-id="06da9-109">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="06da9-110">[out] Um ponteiro para WCHAR * para receber o token de chave pública com codificação hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="06da9-110">[out] A pointer to WCHAR * to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06da9-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="06da9-111">Return Value</span></span>  
 <span data-ttu-id="06da9-112">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="06da9-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="06da9-113">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="06da9-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06da9-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06da9-114">See Also</span></span>  
 [<span data-ttu-id="06da9-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="06da9-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
