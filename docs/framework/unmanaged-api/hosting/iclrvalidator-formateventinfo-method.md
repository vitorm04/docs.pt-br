---
title: "Método ICLRValidator::FormatEventInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRValidator.FormatEventInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRValidator::FormatEventInfo
helpviewer_keywords:
- FormatEventInfo method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::FormatEventInfo method [.NET Framework hosting]
ms.assetid: 808e1f1d-52f4-47c4-83cc-dcf47d075219
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d03864ac8e4e0423e45ac084e01af98e3eab13a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="1c19c-102">Método ICLRValidator::FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="1c19c-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="1c19c-103">Obtém uma mensagem detalhada sobre o erro de validação especificada.</span><span class="sxs-lookup"><span data-stu-id="1c19c-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c19c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c19c-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c19c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c19c-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="1c19c-106">[in] O valor HRESULT que foi passado para o manipulador de erros de validação.</span><span class="sxs-lookup"><span data-stu-id="1c19c-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="1c19c-107">[in] Um `VEContext` instância que contém informações de contexto sobre os erros de validação.</span><span class="sxs-lookup"><span data-stu-id="1c19c-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="1c19c-108">[out no] A mensagem de erro amigável.</span><span class="sxs-lookup"><span data-stu-id="1c19c-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="1c19c-109">[in] O comprimento máximo da mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="1c19c-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="1c19c-110">[in] Uma matriz segura de parâmetros adicionais a serem usados na mensagem.</span><span class="sxs-lookup"><span data-stu-id="1c19c-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c19c-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1c19c-111">Return Value</span></span>  
  
|<span data-ttu-id="1c19c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1c19c-112">HRESULT</span></span>|<span data-ttu-id="1c19c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c19c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1c19c-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="1c19c-114">S_OK</span></span>|<span data-ttu-id="1c19c-115">`FormatEventInfo`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="1c19c-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="1c19c-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1c19c-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1c19c-117">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="1c19c-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1c19c-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1c19c-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1c19c-119">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="1c19c-119">The call timed out.</span></span>|  
|<span data-ttu-id="1c19c-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1c19c-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1c19c-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="1c19c-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1c19c-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1c19c-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1c19c-123">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="1c19c-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1c19c-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1c19c-124">E_FAIL</span></span>|<span data-ttu-id="1c19c-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="1c19c-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1c19c-126">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="1c19c-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1c19c-127">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1c19c-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1c19c-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1c19c-128">Requirements</span></span>  
 <span data-ttu-id="1c19c-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c19c-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c19c-130">**Cabeçalho:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="1c19c-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="1c19c-131">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="1c19c-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1c19c-132">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c19c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c19c-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c19c-133">See Also</span></span>  
 [<span data-ttu-id="1c19c-134">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="1c19c-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="1c19c-135">Interface ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="1c19c-135">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
