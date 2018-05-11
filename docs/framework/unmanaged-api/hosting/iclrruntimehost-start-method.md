---
title: Método ICLRRuntimeHost::Start
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Start
helpviewer_keywords:
- ICLRRuntimeHost::Start method [.NET Framework hosting]
- Start method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: c0a6dce5-0a8d-42e8-808b-6ca14df9d289
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df2747b7cce112e61c6fb99cdb91dc0d56047b9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="9af4f-102">Método ICLRRuntimeHost::Start</span><span class="sxs-lookup"><span data-stu-id="9af4f-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="9af4f-103">Inicializa o common language runtime (CLR) em um processo.</span><span class="sxs-lookup"><span data-stu-id="9af4f-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9af4f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9af4f-104">Syntax</span></span>  
  
```  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9af4f-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9af4f-105">Return Value</span></span>  
  
|<span data-ttu-id="9af4f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9af4f-106">HRESULT</span></span>|<span data-ttu-id="9af4f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9af4f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9af4f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9af4f-108">S_OK</span></span>|<span data-ttu-id="9af4f-109">`Start` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="9af4f-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="9af4f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9af4f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9af4f-111">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9af4f-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9af4f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9af4f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9af4f-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="9af4f-113">The call timed out.</span></span>|  
|<span data-ttu-id="9af4f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9af4f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9af4f-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="9af4f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9af4f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9af4f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9af4f-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="9af4f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9af4f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9af4f-118">E_FAIL</span></span>|<span data-ttu-id="9af4f-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9af4f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9af4f-120">Se um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="9af4f-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9af4f-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9af4f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9af4f-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="9af4f-122">Remarks</span></span>  
 <span data-ttu-id="9af4f-123">Em muitos cenários, não é necessário chamar `Start`, pois o tempo de execução será se inicialize automaticamente após a primeira solicitação para executar código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9af4f-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="9af4f-124">No entanto, você pode usar `Start` para especificar exatamente quando o tempo de execução deve ser inicializado.</span><span class="sxs-lookup"><span data-stu-id="9af4f-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9af4f-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9af4f-125">Requirements</span></span>  
 <span data-ttu-id="9af4f-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9af4f-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9af4f-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9af4f-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9af4f-128">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9af4f-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9af4f-129">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9af4f-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9af4f-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9af4f-130">See Also</span></span>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="9af4f-131">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9af4f-131">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
