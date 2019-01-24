---
title: Função axlrsakeyvaluetopublickeytoken
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
ms.openlocfilehash: 2a340af9ba196dbcd8618afdd83bcf7e56124bf7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529902"
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="84b89-102">\_Função AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="84b89-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="84b89-103">Converte um Módulo e um Expoente em um token de chave pública com nome forte.</span><span class="sxs-lookup"><span data-stu-id="84b89-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84b89-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84b89-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
### <a name="parameters"></a><span data-ttu-id="84b89-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="84b89-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="84b89-106">[in] O blob de módulo codificado na base64 (da \<Modulus > elemento).</span><span class="sxs-lookup"><span data-stu-id="84b89-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="84b89-107">Consulte a [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) estrutura.</span><span class="sxs-lookup"><span data-stu-id="84b89-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="84b89-108">[in] O blob de expoente codificado de base64 (da \<expoente > elemento).</span><span class="sxs-lookup"><span data-stu-id="84b89-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="84b89-109">Consulte a [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) estrutura.</span><span class="sxs-lookup"><span data-stu-id="84b89-109">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="84b89-110">[out] Um ponteiro para WCHAR \* para receber o token de chave pública com codificação hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="84b89-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84b89-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="84b89-111">Return Value</span></span>  
 <span data-ttu-id="84b89-112">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="84b89-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="84b89-113">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="84b89-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b89-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84b89-114">See also</span></span>
- [<span data-ttu-id="84b89-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="84b89-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
