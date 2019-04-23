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
ms.openlocfilehash: 49476a4417e5431842f8e2ba0371c53c5c9f03e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207819"
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="0ab62-102">\_Função AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="0ab62-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="0ab62-103">Converte um Módulo e um Expoente em um token de chave pública com nome forte.</span><span class="sxs-lookup"><span data-stu-id="0ab62-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ab62-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0ab62-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ab62-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ab62-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="0ab62-106">[in] O blob de módulo codificado na base64 (da \<Modulus > elemento).</span><span class="sxs-lookup"><span data-stu-id="0ab62-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="0ab62-107">Consulte a [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) estrutura.</span><span class="sxs-lookup"><span data-stu-id="0ab62-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="0ab62-108">[in] O blob de expoente codificado de base64 (da \<expoente > elemento).</span><span class="sxs-lookup"><span data-stu-id="0ab62-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="0ab62-109">Consulte a [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) estrutura.</span><span class="sxs-lookup"><span data-stu-id="0ab62-109">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="0ab62-110">[out] Um ponteiro para WCHAR \* para receber o token de chave pública com codificação hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="0ab62-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ab62-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0ab62-111">Return Value</span></span>  
 <span data-ttu-id="0ab62-112">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ab62-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="0ab62-113">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="0ab62-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ab62-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ab62-114">See also</span></span>

- [<span data-ttu-id="0ab62-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="0ab62-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
