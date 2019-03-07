---
title: Método ICLRValidator::FormatEventInfo
ms.date: 03/30/2017
api_name:
- ICLRValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::FormatEventInfo
helpviewer_keywords:
- FormatEventInfo method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::FormatEventInfo method [.NET Framework hosting]
ms.assetid: 808e1f1d-52f4-47c4-83cc-dcf47d075219
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40a60bb79c4b1e250ec2d363816d9837c6b51c91
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474196"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="43dcb-102">Método ICLRValidator::FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="43dcb-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="43dcb-103">Obtém uma mensagem detalhada sobre o erro de validação especificado.</span><span class="sxs-lookup"><span data-stu-id="43dcb-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43dcb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43dcb-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43dcb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="43dcb-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="43dcb-106">[in] O valor HRESULT que foi passado para o manipulador de erro de validação.</span><span class="sxs-lookup"><span data-stu-id="43dcb-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="43dcb-107">[in] Um `VEContext` instância que contém informações de contexto sobre os erros de validação.</span><span class="sxs-lookup"><span data-stu-id="43dcb-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="43dcb-108">[no, out] A mensagem de erro amigável.</span><span class="sxs-lookup"><span data-stu-id="43dcb-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="43dcb-109">[in] O comprimento máximo da mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="43dcb-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="43dcb-110">[in] Uma matriz segura de parâmetros adicionais a serem usados na mensagem.</span><span class="sxs-lookup"><span data-stu-id="43dcb-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43dcb-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="43dcb-111">Return Value</span></span>  
  
|<span data-ttu-id="43dcb-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="43dcb-112">HRESULT</span></span>|<span data-ttu-id="43dcb-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="43dcb-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43dcb-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="43dcb-114">S_OK</span></span>|<span data-ttu-id="43dcb-115">`FormatEventInfo` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="43dcb-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="43dcb-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="43dcb-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="43dcb-117">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="43dcb-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="43dcb-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="43dcb-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="43dcb-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="43dcb-119">The call timed out.</span></span>|  
|<span data-ttu-id="43dcb-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="43dcb-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="43dcb-121">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="43dcb-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="43dcb-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="43dcb-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="43dcb-123">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="43dcb-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="43dcb-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="43dcb-124">E_FAIL</span></span>|<span data-ttu-id="43dcb-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="43dcb-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="43dcb-126">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="43dcb-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="43dcb-127">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="43dcb-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="43dcb-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="43dcb-128">Requirements</span></span>  
 <span data-ttu-id="43dcb-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43dcb-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43dcb-130">**Cabeçalho:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="43dcb-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="43dcb-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="43dcb-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43dcb-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43dcb-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43dcb-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43dcb-133">See also</span></span>
- [<span data-ttu-id="43dcb-134">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="43dcb-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="43dcb-135">Interface ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="43dcb-135">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
