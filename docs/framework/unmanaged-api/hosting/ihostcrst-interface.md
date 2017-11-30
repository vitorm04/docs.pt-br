---
title: Interface IHostCrst
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst
helpviewer_keywords: IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 59485d7a642ba8b3233d5d077062e89fb2ac9b14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="70ff4-102">Interface IHostCrst</span><span class="sxs-lookup"><span data-stu-id="70ff4-102">IHostCrst Interface</span></span>
<span data-ttu-id="70ff4-103">Serve como a representação do host de uma seção crítica de threading.</span><span class="sxs-lookup"><span data-stu-id="70ff4-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70ff4-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="70ff4-104">Methods</span></span>  
  
|<span data-ttu-id="70ff4-105">Método</span><span class="sxs-lookup"><span data-stu-id="70ff4-105">Method</span></span>|<span data-ttu-id="70ff4-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="70ff4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70ff4-107">Método ENTER</span><span class="sxs-lookup"><span data-stu-id="70ff4-107">Enter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|<span data-ttu-id="70ff4-108">Entrar na seção crítica.</span><span class="sxs-lookup"><span data-stu-id="70ff4-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="70ff4-109">Método Leave</span><span class="sxs-lookup"><span data-stu-id="70ff4-109">Leave Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|<span data-ttu-id="70ff4-110">Deixa a seção crítica.</span><span class="sxs-lookup"><span data-stu-id="70ff4-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="70ff4-111">Método SetSpinCount</span><span class="sxs-lookup"><span data-stu-id="70ff4-111">SetSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|<span data-ttu-id="70ff4-112">Define a contagem de rotação da seção crítica.</span><span class="sxs-lookup"><span data-stu-id="70ff4-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="70ff4-113">Método TryEnter</span><span class="sxs-lookup"><span data-stu-id="70ff4-113">TryEnter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|<span data-ttu-id="70ff4-114">As tentativas de inserir a seção crítica e relatórios de êxito ou falha imediatamente.</span><span class="sxs-lookup"><span data-stu-id="70ff4-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70ff4-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="70ff4-115">Remarks</span></span>  
 <span data-ttu-id="70ff4-116">`IHostCrst`permite que o common language runtime (CLR) para se comunicar diretamente com a representação do host de uma seção crítica, em vez de usar as funções do Win32, como `EnterCriticalSection` ou `LeaveCriticalSection`.</span><span class="sxs-lookup"><span data-stu-id="70ff4-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70ff4-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="70ff4-117">Requirements</span></span>  
 <span data-ttu-id="70ff4-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70ff4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70ff4-119">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="70ff4-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="70ff4-120">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="70ff4-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70ff4-121">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70ff4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70ff4-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70ff4-122">See Also</span></span>  
 [<span data-ttu-id="70ff4-123">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="70ff4-123">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="70ff4-124">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="70ff4-124">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="70ff4-125">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="70ff4-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
