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
ms.openlocfilehash: 55cd444ffedc92ba74239421ae548ffd930e6ab7
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703935"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="3aa9e-102">Método ICLRRuntimeHost::Stop</span><span class="sxs-lookup"><span data-stu-id="3aa9e-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="3aa9e-103">Interrompe a execução do código pelo Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3aa9e-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3aa9e-104">Esse método não libera recursos para o host, descarrega domínios de aplicativo ou destrói threads.</span><span class="sxs-lookup"><span data-stu-id="3aa9e-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="3aa9e-105">Você deve encerrar o processo para liberar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="3aa9e-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aa9e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3aa9e-106">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3aa9e-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3aa9e-107">Return Value</span></span>  
  
|<span data-ttu-id="3aa9e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3aa9e-108">HRESULT</span></span>|<span data-ttu-id="3aa9e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="3aa9e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3aa9e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3aa9e-110">S_OK</span></span>|<span data-ttu-id="3aa9e-111">`Stop`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="3aa9e-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="3aa9e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3aa9e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3aa9e-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="3aa9e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3aa9e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3aa9e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3aa9e-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="3aa9e-115">The call timed out.</span></span>|  
|<span data-ttu-id="3aa9e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3aa9e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3aa9e-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="3aa9e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3aa9e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3aa9e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3aa9e-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="3aa9e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3aa9e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3aa9e-120">E_FAIL</span></span>|<span data-ttu-id="3aa9e-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="3aa9e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3aa9e-122">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="3aa9e-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3aa9e-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3aa9e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3aa9e-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3aa9e-124">Requirements</span></span>  
 <span data-ttu-id="3aa9e-125">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3aa9e-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3aa9e-126">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3aa9e-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3aa9e-127">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3aa9e-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3aa9e-128">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3aa9e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aa9e-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="3aa9e-129">See also</span></span>

- [<span data-ttu-id="3aa9e-130">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="3aa9e-130">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
