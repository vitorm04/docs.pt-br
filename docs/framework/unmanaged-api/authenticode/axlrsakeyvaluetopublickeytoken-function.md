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
ms.openlocfilehash: eca6c5fc61d4f7e80046102a560d228fc01e5292
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038409"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="55d23-102">\_Função AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="55d23-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="55d23-103">Converte um Módulo e um Expoente em um token de chave pública com nome forte.</span><span class="sxs-lookup"><span data-stu-id="55d23-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55d23-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55d23-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55d23-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="55d23-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="55d23-106">no O blob de módulo codificado em Base64 (no \<elemento > do módulo).</span><span class="sxs-lookup"><span data-stu-id="55d23-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="55d23-107">Consulte a estrutura [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="55d23-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="55d23-108">no O blob de expoente codificado em Base64 (do \<elemento > exponencial).</span><span class="sxs-lookup"><span data-stu-id="55d23-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="55d23-109">Consulte a estrutura [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="55d23-109">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="55d23-110">[out] Um ponteiro para WCHAR \* para receber o token de chave pública com codificação hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="55d23-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55d23-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="55d23-111">Return Value</span></span>  
 <span data-ttu-id="55d23-112">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="55d23-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="55d23-113">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="55d23-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55d23-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55d23-114">See also</span></span>

- [<span data-ttu-id="55d23-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="55d23-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
