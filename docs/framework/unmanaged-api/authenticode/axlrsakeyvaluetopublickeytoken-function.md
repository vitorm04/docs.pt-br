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
ms.workload: dotnet
ms.openlocfilehash: b1380f658d9c154d9ea41228cace5f9a3eed39b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="a7aa6-102">Função _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="a7aa6-102">_AxlRSAKeyValueToPublicKeyToken Function</span></span>
<span data-ttu-id="a7aa6-103">Converte um Módulo e um Expoente em um token de chave pública com nome forte.</span><span class="sxs-lookup"><span data-stu-id="a7aa6-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7aa6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7aa6-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7aa6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a7aa6-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="a7aa6-106">[in] O blob de módulo codificado na base64 (da \<módulo > elemento).</span><span class="sxs-lookup"><span data-stu-id="a7aa6-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="a7aa6-107">Consulte o [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) estrutura.</span><span class="sxs-lookup"><span data-stu-id="a7aa6-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="a7aa6-108">[in] O blob de expoente codificado na base64 (da \<expoente > elemento).</span><span class="sxs-lookup"><span data-stu-id="a7aa6-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="a7aa6-109">Consulte o [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) estrutura.</span><span class="sxs-lookup"><span data-stu-id="a7aa6-109">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="a7aa6-110">[out] Um ponteiro para WCHAR * para receber o token de chave pública com codificação hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="a7aa6-110">[out] A pointer to WCHAR * to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7aa6-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a7aa6-111">Return Value</span></span>  
 <span data-ttu-id="a7aa6-112">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="a7aa6-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="a7aa6-113">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="a7aa6-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7aa6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7aa6-114">See Also</span></span>  
 [<span data-ttu-id="a7aa6-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="a7aa6-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
