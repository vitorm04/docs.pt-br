---
title: "Método IValidator::FormatEventInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ddff0a640f37133bf5a44aea1e371d73d0fd2856
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="de8bd-102">Método IValidator::FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="de8bd-102">IValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="de8bd-103">Obtém a mensagem de erro correspondente para o erro de validação especificado.</span><span class="sxs-lookup"><span data-stu-id="de8bd-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de8bd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de8bd-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de8bd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="de8bd-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="de8bd-106">[in] O valor HRESULT que foi passado para o manipulador de erros de validação.</span><span class="sxs-lookup"><span data-stu-id="de8bd-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="de8bd-107">[in] Um `VEContext` instância que contém informações de contexto sobre o erro de validação.</span><span class="sxs-lookup"><span data-stu-id="de8bd-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="de8bd-108">[out no] Uma cadeia de caracteres que contém a mensagem de erro retornado.</span><span class="sxs-lookup"><span data-stu-id="de8bd-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="de8bd-109">[in] O comprimento máximo da mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="de8bd-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="de8bd-110">[in] Uma matriz de segurança que contém parâmetros adicionais que descreve o erro.</span><span class="sxs-lookup"><span data-stu-id="de8bd-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de8bd-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="de8bd-111">Requirements</span></span>  
 <span data-ttu-id="de8bd-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de8bd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de8bd-113">**Cabeçalho:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="de8bd-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="de8bd-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="de8bd-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de8bd-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de8bd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de8bd-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de8bd-116">See Also</span></span>  
 
