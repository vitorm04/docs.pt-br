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
ms.openlocfilehash: 935d8e9fa3ed15be03c6cd05b1bc3c4919d0cc2b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127861"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="3e470-102">Método ICLRValidator::FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="3e470-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="3e470-103">Obtém uma mensagem detalhada sobre o erro de validação especificado.</span><span class="sxs-lookup"><span data-stu-id="3e470-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e470-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e470-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e470-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3e470-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="3e470-106">no O valor HRESULT que foi passado para o manipulador de erro de validação.</span><span class="sxs-lookup"><span data-stu-id="3e470-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="3e470-107">no Uma instância de `VEContext` que contém informações de contexto sobre os erros de validação.</span><span class="sxs-lookup"><span data-stu-id="3e470-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="3e470-108">[entrada, saída] A mensagem de erro amigável.</span><span class="sxs-lookup"><span data-stu-id="3e470-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="3e470-109">no O comprimento máximo da mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="3e470-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="3e470-110">no Uma matriz segura de parâmetros adicionais a serem usados na mensagem.</span><span class="sxs-lookup"><span data-stu-id="3e470-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e470-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3e470-111">Return Value</span></span>  
  
|<span data-ttu-id="3e470-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3e470-112">HRESULT</span></span>|<span data-ttu-id="3e470-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e470-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3e470-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="3e470-114">S_OK</span></span>|<span data-ttu-id="3e470-115">`FormatEventInfo` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="3e470-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="3e470-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3e470-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3e470-117">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="3e470-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3e470-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3e470-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3e470-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="3e470-119">The call timed out.</span></span>|  
|<span data-ttu-id="3e470-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3e470-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3e470-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="3e470-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3e470-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3e470-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3e470-123">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="3e470-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3e470-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3e470-124">E_FAIL</span></span>|<span data-ttu-id="3e470-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="3e470-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3e470-126">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="3e470-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3e470-127">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3e470-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3e470-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3e470-128">Requirements</span></span>  
 <span data-ttu-id="3e470-129">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e470-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e470-130">**Cabeçalho:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="3e470-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="3e470-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3e470-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e470-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e470-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e470-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e470-133">See also</span></span>

- [<span data-ttu-id="3e470-134">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="3e470-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="3e470-135">Interface ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="3e470-135">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
