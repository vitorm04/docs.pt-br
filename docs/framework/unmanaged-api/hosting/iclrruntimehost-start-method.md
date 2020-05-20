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
ms.openlocfilehash: e5ed1cbb640e760d75e1722871453a0bec283bde
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703907"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="f9c52-102">Método ICLRRuntimeHost::Start</span><span class="sxs-lookup"><span data-stu-id="f9c52-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="f9c52-103">Inicializa o Common Language Runtime (CLR) em um processo.</span><span class="sxs-lookup"><span data-stu-id="f9c52-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9c52-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9c52-104">Syntax</span></span>  
  
```cpp  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f9c52-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f9c52-105">Return Value</span></span>  
  
|<span data-ttu-id="f9c52-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9c52-106">HRESULT</span></span>|<span data-ttu-id="f9c52-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9c52-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9c52-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f9c52-108">S_OK</span></span>|<span data-ttu-id="f9c52-109">`Start`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f9c52-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="f9c52-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f9c52-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f9c52-111">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f9c52-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f9c52-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f9c52-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f9c52-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="f9c52-113">The call timed out.</span></span>|  
|<span data-ttu-id="f9c52-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9c52-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f9c52-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f9c52-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f9c52-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f9c52-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f9c52-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="f9c52-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f9c52-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f9c52-118">E_FAIL</span></span>|<span data-ttu-id="f9c52-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f9c52-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f9c52-120">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="f9c52-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f9c52-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f9c52-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9c52-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="f9c52-122">Remarks</span></span>  
 <span data-ttu-id="f9c52-123">Em muitos cenários, não é necessário chamar `Start` , pois o tempo de execução será inicializado automaticamente na primeira solicitação para executar código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f9c52-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="f9c52-124">No entanto, você pode usar `Start` para especificar exatamente quando o tempo de execução deve ser inicializado.</span><span class="sxs-lookup"><span data-stu-id="f9c52-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9c52-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f9c52-125">Requirements</span></span>  
 <span data-ttu-id="f9c52-126">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9c52-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9c52-127">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f9c52-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9c52-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f9c52-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9c52-129">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9c52-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9c52-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="f9c52-130">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="f9c52-131">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="f9c52-131">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
