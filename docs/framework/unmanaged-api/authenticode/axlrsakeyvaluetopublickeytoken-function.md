---
title: Função _AxlRSAKeyValueToPublicKeyToken
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ef73f0f7599fdff887437756a5995591fd8ec89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="728e1-102">Função _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="728e1-102">_AxlRSAKeyValueToPublicKeyToken Function</span></span>
<span data-ttu-id="728e1-103">Converte um Módulo e um Expoente em um token de chave pública com nome forte.</span><span class="sxs-lookup"><span data-stu-id="728e1-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="728e1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="728e1-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="728e1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="728e1-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="728e1-106">[in] O blob de módulo codificado na base64 (da \<módulo > elemento).</span><span class="sxs-lookup"><span data-stu-id="728e1-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="728e1-107">Consulte o [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) estrutura.</span><span class="sxs-lookup"><span data-stu-id="728e1-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="728e1-108">[in] O blob de expoente codificado na base64 (da \<expoente > elemento).</span><span class="sxs-lookup"><span data-stu-id="728e1-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="728e1-109">Consulte o [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) estrutura.</span><span class="sxs-lookup"><span data-stu-id="728e1-109">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="728e1-110">[out] Um ponteiro para WCHAR \* para receber o token de chave pública com codificação hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="728e1-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="728e1-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="728e1-111">Return Value</span></span>  
 <span data-ttu-id="728e1-112">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="728e1-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="728e1-113">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="728e1-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="728e1-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="728e1-114">See Also</span></span>  
 [<span data-ttu-id="728e1-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="728e1-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
