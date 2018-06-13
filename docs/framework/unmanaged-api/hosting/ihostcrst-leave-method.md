---
title: Método IHostCrst::Leave
ms.date: 03/30/2017
api_name:
- IHostCrst.Leave
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Leave
helpviewer_keywords:
- IHostCrst::Leave method [.NET Framework hosting]
- Leave method [.NET Framework hosting]
ms.assetid: dfc51d9e-b36d-4dba-9ea1-4f63fa0601ae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae5561abb7cd0770fd5b7f290a4aa8dff85b6150
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441646"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="52c71-102">Método IHostCrst::Leave</span><span class="sxs-lookup"><span data-stu-id="52c71-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="52c71-103">Deixa a seção crítica que é representada pela instância atual do [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span><span class="sxs-lookup"><span data-stu-id="52c71-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52c71-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52c71-104">Syntax</span></span>  
  
```  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="52c71-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="52c71-105">Return Value</span></span>  
  
|<span data-ttu-id="52c71-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52c71-106">HRESULT</span></span>|<span data-ttu-id="52c71-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="52c71-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52c71-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="52c71-108">S_OK</span></span>|<span data-ttu-id="52c71-109">`Leave` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="52c71-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="52c71-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="52c71-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="52c71-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="52c71-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="52c71-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="52c71-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="52c71-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="52c71-113">The call timed out.</span></span>|  
|<span data-ttu-id="52c71-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="52c71-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="52c71-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="52c71-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="52c71-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="52c71-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="52c71-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="52c71-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="52c71-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="52c71-118">E_FAIL</span></span>|<span data-ttu-id="52c71-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="52c71-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="52c71-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="52c71-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="52c71-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="52c71-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52c71-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="52c71-122">Remarks</span></span>  
 <span data-ttu-id="52c71-123">`Leave` permite que o CLR para se comunicar diretamente com implementação de threading, no host vez de usar o Win32 correspondente `LeaveCriticalSection` função.</span><span class="sxs-lookup"><span data-stu-id="52c71-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="52c71-124">Um thread que assume a propriedade de seção crítica representada pelo atual `IHostCrst` instância deve chamar `Leave` depois de cada vez que entrar essa seção crítica.</span><span class="sxs-lookup"><span data-stu-id="52c71-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52c71-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="52c71-125">Requirements</span></span>  
 <span data-ttu-id="52c71-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52c71-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52c71-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="52c71-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52c71-128">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="52c71-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52c71-129">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52c71-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52c71-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52c71-130">See Also</span></span>  
 [<span data-ttu-id="52c71-131">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="52c71-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="52c71-132">Interface IHostCrst</span><span class="sxs-lookup"><span data-stu-id="52c71-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="52c71-133">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="52c71-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
