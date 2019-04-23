---
title: Método ICLRRuntimeHost::Stop
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85116244ad21842fab025ddd48106deef75f210b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166953"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="227e2-102">Método ICLRRuntimeHost::Stop</span><span class="sxs-lookup"><span data-stu-id="227e2-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="227e2-103">Interrompe a execução de código, o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="227e2-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="227e2-104">Esse método não liberar recursos para o host, descarregar domínios de aplicativo ou destruir threads.</span><span class="sxs-lookup"><span data-stu-id="227e2-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="227e2-105">Você deve encerrar o processo para liberar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="227e2-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="227e2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="227e2-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="227e2-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="227e2-107">Return Value</span></span>  
  
|<span data-ttu-id="227e2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="227e2-108">HRESULT</span></span>|<span data-ttu-id="227e2-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="227e2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="227e2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="227e2-110">S_OK</span></span>|<span data-ttu-id="227e2-111">`Stop` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="227e2-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="227e2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="227e2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="227e2-113">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="227e2-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="227e2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="227e2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="227e2-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="227e2-115">The call timed out.</span></span>|  
|<span data-ttu-id="227e2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="227e2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="227e2-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="227e2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="227e2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="227e2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="227e2-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="227e2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="227e2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="227e2-120">E_FAIL</span></span>|<span data-ttu-id="227e2-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="227e2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="227e2-122">Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="227e2-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="227e2-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="227e2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="227e2-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="227e2-124">Requirements</span></span>  
 <span data-ttu-id="227e2-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="227e2-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="227e2-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="227e2-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="227e2-127">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="227e2-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="227e2-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="227e2-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="227e2-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="227e2-129">See also</span></span>

- [<span data-ttu-id="227e2-130">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="227e2-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
