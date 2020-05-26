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
ms.openlocfilehash: e8cb1486ccea11ba6edcf7bbb781a9bf210b496d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804910"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="efc38-102">Interface IHostCrst</span><span class="sxs-lookup"><span data-stu-id="efc38-102">IHostCrst Interface</span></span>
<span data-ttu-id="efc38-103">Serve como a representação do host de uma seção crítica para Threading.</span><span class="sxs-lookup"><span data-stu-id="efc38-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="efc38-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="efc38-104">Methods</span></span>  
  
|<span data-ttu-id="efc38-105">Método</span><span class="sxs-lookup"><span data-stu-id="efc38-105">Method</span></span>|<span data-ttu-id="efc38-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="efc38-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="efc38-107">Método Enter</span><span class="sxs-lookup"><span data-stu-id="efc38-107">Enter Method</span></span>](ihostcrst-enter-method.md)|<span data-ttu-id="efc38-108">Insere a seção crítica.</span><span class="sxs-lookup"><span data-stu-id="efc38-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="efc38-109">Método Leave</span><span class="sxs-lookup"><span data-stu-id="efc38-109">Leave Method</span></span>](ihostcrst-leave-method.md)|<span data-ttu-id="efc38-110">Deixa a seção crítica.</span><span class="sxs-lookup"><span data-stu-id="efc38-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="efc38-111">Método SetSpinCount</span><span class="sxs-lookup"><span data-stu-id="efc38-111">SetSpinCount Method</span></span>](ihostcrst-setspincount-method.md)|<span data-ttu-id="efc38-112">Define a contagem de rotação para a seção crítica.</span><span class="sxs-lookup"><span data-stu-id="efc38-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="efc38-113">Método TryEnter</span><span class="sxs-lookup"><span data-stu-id="efc38-113">TryEnter Method</span></span>](ihostcrst-tryenter-method.md)|<span data-ttu-id="efc38-114">Tenta inserir a seção crítica e relata êxito ou falha imediatamente.</span><span class="sxs-lookup"><span data-stu-id="efc38-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efc38-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="efc38-115">Remarks</span></span>  
 <span data-ttu-id="efc38-116">`IHostCrst`permite que o Common Language Runtime (CLR) se comunique diretamente com a representação do host de uma seção crítica, em vez de usar funções do Win32, como `EnterCriticalSection` ou `LeaveCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="efc38-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efc38-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="efc38-117">Requirements</span></span>  
 <span data-ttu-id="efc38-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efc38-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efc38-119">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="efc38-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="efc38-120">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="efc38-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="efc38-121">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efc38-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efc38-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="efc38-122">See also</span></span>

- [<span data-ttu-id="efc38-123">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="efc38-123">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="efc38-124">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="efc38-124">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="efc38-125">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="efc38-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
