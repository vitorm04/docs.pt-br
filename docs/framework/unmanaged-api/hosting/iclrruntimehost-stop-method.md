---
title: "Método ICLRRuntimeHost::Stop"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.Stop
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3cb9eaecdec661ae56727e5fd38c7e9a3b9621d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="0b6f1-102">Método ICLRRuntimeHost::Stop</span><span class="sxs-lookup"><span data-stu-id="0b6f1-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="0b6f1-103">Interrompe a execução de código, o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="0b6f1-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0b6f1-104">Esse método não liberar recursos para o host, descarregar domínios de aplicativo ou destruir threads.</span><span class="sxs-lookup"><span data-stu-id="0b6f1-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="0b6f1-105">Você deve encerrar o processo para liberar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="0b6f1-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b6f1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b6f1-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0b6f1-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0b6f1-107">Return Value</span></span>  
  
|<span data-ttu-id="0b6f1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b6f1-108">HRESULT</span></span>|<span data-ttu-id="0b6f1-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b6f1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b6f1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b6f1-110">S_OK</span></span>|<span data-ttu-id="0b6f1-111">`Stop`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="0b6f1-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="0b6f1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0b6f1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0b6f1-113">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="0b6f1-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0b6f1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0b6f1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0b6f1-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="0b6f1-115">The call timed out.</span></span>|  
|<span data-ttu-id="0b6f1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0b6f1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0b6f1-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="0b6f1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0b6f1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0b6f1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0b6f1-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="0b6f1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0b6f1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0b6f1-120">E_FAIL</span></span>|<span data-ttu-id="0b6f1-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="0b6f1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0b6f1-122">Se um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="0b6f1-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0b6f1-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0b6f1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0b6f1-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0b6f1-124">Requirements</span></span>  
 <span data-ttu-id="0b6f1-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b6f1-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b6f1-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0b6f1-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b6f1-127">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="0b6f1-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b6f1-128">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b6f1-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b6f1-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b6f1-129">See Also</span></span>  
 [<span data-ttu-id="0b6f1-130">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0b6f1-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
