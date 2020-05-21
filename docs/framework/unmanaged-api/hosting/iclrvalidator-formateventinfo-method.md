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
ms.openlocfilehash: 164a8c15a501af44aabb95852400621f05bbe873
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762775"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="7f8ff-102">Método ICLRValidator::FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="7f8ff-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="7f8ff-103">Obtém uma mensagem detalhada sobre o erro de validação especificado.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f8ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f8ff-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f8ff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7f8ff-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="7f8ff-106">no O valor HRESULT que foi passado para o manipulador de erro de validação.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="7f8ff-107">no Uma `VEContext` instância que contém informações de contexto sobre os erros de validação.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="7f8ff-108">[entrada, saída] A mensagem de erro amigável.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="7f8ff-109">no O comprimento máximo da mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="7f8ff-110">no Uma matriz segura de parâmetros adicionais a serem usados na mensagem.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f8ff-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="7f8ff-111">Return Value</span></span>  
  
|<span data-ttu-id="7f8ff-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f8ff-112">HRESULT</span></span>|<span data-ttu-id="7f8ff-113">Description</span><span class="sxs-lookup"><span data-stu-id="7f8ff-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f8ff-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f8ff-114">S_OK</span></span>|<span data-ttu-id="7f8ff-115">`FormatEventInfo`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="7f8ff-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7f8ff-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7f8ff-117">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7f8ff-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7f8ff-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7f8ff-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-119">The call timed out.</span></span>|  
|<span data-ttu-id="7f8ff-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7f8ff-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7f8ff-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7f8ff-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7f8ff-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7f8ff-123">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7f8ff-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7f8ff-124">E_FAIL</span></span>|<span data-ttu-id="7f8ff-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7f8ff-126">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7f8ff-127">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f8ff-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f8ff-128">Requirements</span></span>  
 <span data-ttu-id="7f8ff-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f8ff-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f8ff-130">**Cabeçalho:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="7f8ff-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="7f8ff-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7f8ff-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f8ff-132">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f8ff-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f8ff-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="7f8ff-133">See also</span></span>

- [<span data-ttu-id="7f8ff-134">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="7f8ff-134">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="7f8ff-135">Interface ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="7f8ff-135">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
