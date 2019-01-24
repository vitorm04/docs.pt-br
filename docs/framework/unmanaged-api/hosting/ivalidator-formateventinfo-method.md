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
ms.openlocfilehash: 17217146d8e5ed53feb8305ca4ac16c8f96ddeb7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653847"
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="7bfab-102">Método IValidator::FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="7bfab-102">IValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="7bfab-103">Obtém a mensagem de erro correspondente ao erro de validação especificado.</span><span class="sxs-lookup"><span data-stu-id="7bfab-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bfab-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7bfab-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7bfab-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7bfab-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="7bfab-106">[in] O valor HRESULT que foi passado para o manipulador de erro de validação.</span><span class="sxs-lookup"><span data-stu-id="7bfab-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="7bfab-107">[in] Um `VEContext` instância que contém informações de contexto sobre o erro de validação.</span><span class="sxs-lookup"><span data-stu-id="7bfab-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="7bfab-108">[no, out] Uma cadeia de caracteres que contém a mensagem de erro retornado.</span><span class="sxs-lookup"><span data-stu-id="7bfab-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="7bfab-109">[in] O comprimento máximo da mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="7bfab-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="7bfab-110">[in] Uma matriz segura que contém os parâmetros adicionais que descreve o erro.</span><span class="sxs-lookup"><span data-stu-id="7bfab-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bfab-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7bfab-111">Requirements</span></span>  
 <span data-ttu-id="7bfab-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bfab-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bfab-113">**Cabeçalho:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="7bfab-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="7bfab-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7bfab-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7bfab-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bfab-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bfab-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7bfab-116">See also</span></span>

