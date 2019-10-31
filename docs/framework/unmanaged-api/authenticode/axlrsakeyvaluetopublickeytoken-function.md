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
ms.openlocfilehash: 1f53df33a65d3f75b7574eda3507e370c2e086ac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099829"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="2054f-102">\_função AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="2054f-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="2054f-103">Converte um Módulo e um Expoente em um token de chave pública com nome forte.</span><span class="sxs-lookup"><span data-stu-id="2054f-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2054f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2054f-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2054f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2054f-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="2054f-106">no O blob de módulo codificado em Base64 (do elemento \<> do módulo).</span><span class="sxs-lookup"><span data-stu-id="2054f-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="2054f-107">Consulte a estrutura [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="2054f-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="2054f-108">no O blob de expoente codificado em Base64 (do elemento \<expoente >).</span><span class="sxs-lookup"><span data-stu-id="2054f-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="2054f-109">Consulte a estrutura [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="2054f-109">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="2054f-110">[out] Um ponteiro para WCHAR \* para receber o token de chave pública com codificação hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="2054f-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2054f-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2054f-111">Return Value</span></span>  
 <span data-ttu-id="2054f-112">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="2054f-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="2054f-113">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="2054f-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2054f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2054f-114">See also</span></span>

- [<span data-ttu-id="2054f-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="2054f-115">Authenticode</span></span>](index.md)
