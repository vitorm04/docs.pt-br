---
title: Interface IHostCrst
ms.date: 03/30/2017
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34a911668db09b255282833cec3e6272b315373b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618653"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="a3b99-102">Interface IHostCrst</span><span class="sxs-lookup"><span data-stu-id="a3b99-102">IHostCrst Interface</span></span>
<span data-ttu-id="a3b99-103">Serve como a representação do host de uma seção crítica para threading.</span><span class="sxs-lookup"><span data-stu-id="a3b99-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3b99-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a3b99-104">Methods</span></span>  
  
|<span data-ttu-id="a3b99-105">Método</span><span class="sxs-lookup"><span data-stu-id="a3b99-105">Method</span></span>|<span data-ttu-id="a3b99-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3b99-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3b99-107">Método Enter</span><span class="sxs-lookup"><span data-stu-id="a3b99-107">Enter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|<span data-ttu-id="a3b99-108">Entrar na seção crítica.</span><span class="sxs-lookup"><span data-stu-id="a3b99-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="a3b99-109">Método Leave</span><span class="sxs-lookup"><span data-stu-id="a3b99-109">Leave Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|<span data-ttu-id="a3b99-110">Deixa a seção crítica.</span><span class="sxs-lookup"><span data-stu-id="a3b99-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="a3b99-111">Método SetSpinCount</span><span class="sxs-lookup"><span data-stu-id="a3b99-111">SetSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|<span data-ttu-id="a3b99-112">Define a contagem de rotação para a seção crítica.</span><span class="sxs-lookup"><span data-stu-id="a3b99-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="a3b99-113">Método TryEnter</span><span class="sxs-lookup"><span data-stu-id="a3b99-113">TryEnter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|<span data-ttu-id="a3b99-114">Tentativas de inserir a seção crítica e relatórios de êxito ou falha imediatamente.</span><span class="sxs-lookup"><span data-stu-id="a3b99-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3b99-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="a3b99-115">Remarks</span></span>  
 <span data-ttu-id="a3b99-116">`IHostCrst` permite que o common language runtime (CLR) para se comunicar diretamente com a representação do host de uma seção crítica, em vez de usar as funções do Win32, como `EnterCriticalSection` ou `LeaveCriticalSection`.</span><span class="sxs-lookup"><span data-stu-id="a3b99-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3b99-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a3b99-117">Requirements</span></span>  
 <span data-ttu-id="a3b99-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3b99-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3b99-119">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a3b99-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3b99-120">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a3b99-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3b99-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3b99-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3b99-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3b99-122">See also</span></span>
- [<span data-ttu-id="a3b99-123">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="a3b99-123">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="a3b99-124">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="a3b99-124">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="a3b99-125">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="a3b99-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
