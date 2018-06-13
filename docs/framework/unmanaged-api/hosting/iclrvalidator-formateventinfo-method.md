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
ms.openlocfilehash: 30fca37887c17f5f0da7fd2faaba32f0e5edf235
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437359"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="fdb6a-102">Método ICLRValidator::FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="fdb6a-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="fdb6a-103">Obtém uma mensagem detalhada sobre o erro de validação especificada.</span><span class="sxs-lookup"><span data-stu-id="fdb6a-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdb6a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fdb6a-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fdb6a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fdb6a-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="fdb6a-106">[in] O valor HRESULT que foi passado para o manipulador de erros de validação.</span><span class="sxs-lookup"><span data-stu-id="fdb6a-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="fdb6a-107">[in] Um `VEContext` instância que contém informações de contexto sobre os erros de validação.</span><span class="sxs-lookup"><span data-stu-id="fdb6a-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="fdb6a-108">[out no] A mensagem de erro amigável.</span><span class="sxs-lookup"><span data-stu-id="fdb6a-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="fdb6a-109">[in] O comprimento máximo da mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="fdb6a-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="fdb6a-110">[in] Uma matriz segura de parâmetros adicionais a serem usados na mensagem.</span><span class="sxs-lookup"><span data-stu-id="fdb6a-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fdb6a-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fdb6a-111">Return Value</span></span>  
  
|<span data-ttu-id="fdb6a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fdb6a-112">HRESULT</span></span>|<span data-ttu-id="fdb6a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdb6a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fdb6a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="fdb6a-114">S_OK</span></span>|<span data-ttu-id="fdb6a-115">`FormatEventInfo` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="fdb6a-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="fdb6a-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fdb6a-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fdb6a-117">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="fdb6a-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fdb6a-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fdb6a-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fdb6a-119">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="fdb6a-119">The call timed out.</span></span>|  
|<span data-ttu-id="fdb6a-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fdb6a-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fdb6a-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="fdb6a-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fdb6a-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fdb6a-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fdb6a-123">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="fdb6a-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fdb6a-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fdb6a-124">E_FAIL</span></span>|<span data-ttu-id="fdb6a-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="fdb6a-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fdb6a-126">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="fdb6a-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fdb6a-127">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fdb6a-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fdb6a-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fdb6a-128">Requirements</span></span>  
 <span data-ttu-id="fdb6a-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdb6a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdb6a-130">**Cabeçalho:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="fdb6a-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="fdb6a-131">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="fdb6a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fdb6a-132">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdb6a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdb6a-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fdb6a-133">See Also</span></span>  
 [<span data-ttu-id="fdb6a-134">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="fdb6a-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="fdb6a-135">Interface ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="fdb6a-135">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
