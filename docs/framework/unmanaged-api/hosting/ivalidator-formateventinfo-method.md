---
title: Método IValidator::FormatEventInfo
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ecbecec86d81357000679ab50e12f06d91c9f50d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217075"
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="6c87e-102">Método IValidator::FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="6c87e-102">IValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="6c87e-103">Obtém a mensagem de erro correspondente ao erro de validação especificado.</span><span class="sxs-lookup"><span data-stu-id="6c87e-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c87e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c87e-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c87e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6c87e-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="6c87e-106">[in] O valor HRESULT que foi passado para o manipulador de erro de validação.</span><span class="sxs-lookup"><span data-stu-id="6c87e-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="6c87e-107">[in] Um `VEContext` instância que contém informações de contexto sobre o erro de validação.</span><span class="sxs-lookup"><span data-stu-id="6c87e-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="6c87e-108">[no, out] Uma cadeia de caracteres que contém a mensagem de erro retornado.</span><span class="sxs-lookup"><span data-stu-id="6c87e-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="6c87e-109">[in] O comprimento máximo da mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="6c87e-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="6c87e-110">[in] Uma matriz segura que contém os parâmetros adicionais que descreve o erro.</span><span class="sxs-lookup"><span data-stu-id="6c87e-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c87e-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6c87e-111">Requirements</span></span>  
 <span data-ttu-id="6c87e-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c87e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c87e-113">**Cabeçalho:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="6c87e-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="6c87e-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6c87e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6c87e-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="6c87e-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
