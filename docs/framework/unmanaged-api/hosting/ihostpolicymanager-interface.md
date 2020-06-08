---
title: Interface IHostPolicyManager
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
ms.openlocfilehash: d6b34403a45cc40863d79b59396041e496989045
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503916"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="2887c-102">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="2887c-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="2887c-103">Fornece métodos que notificam o host das ações que o Common Language Runtime (CLR) executa em caso de anulações, tempos limite ou falhas.</span><span class="sxs-lookup"><span data-stu-id="2887c-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2887c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2887c-104">Methods</span></span>  
  
|<span data-ttu-id="2887c-105">Método</span><span class="sxs-lookup"><span data-stu-id="2887c-105">Method</span></span>|<span data-ttu-id="2887c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2887c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2887c-107">Método OnDefaultAction</span><span class="sxs-lookup"><span data-stu-id="2887c-107">OnDefaultAction Method</span></span>](ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="2887c-108">Notifica o host de que o CLR está prestes a tomar a ação padrão especificada por uma chamada para [ICLRPolicyManager:: Setpadrãoaction](iclrpolicymanager-setdefaultaction-method.md) em resposta a um descarregamento ou anulação de thread <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="2887c-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="2887c-109">Método OnFailure</span><span class="sxs-lookup"><span data-stu-id="2887c-109">OnFailure Method</span></span>](ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="2887c-110">Notifica o host de que o CLR está prestes a executar a ação especificada por uma chamada para [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) em resposta a uma alocação de recurso ou falha de recuperação.</span><span class="sxs-lookup"><span data-stu-id="2887c-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="2887c-111">Método OnTimeout</span><span class="sxs-lookup"><span data-stu-id="2887c-111">OnTimeout Method</span></span>](ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="2887c-112">Notifica o host de que o CLR está prestes a executar a ação especificada por uma chamada para [ICLRPolicyManager:: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) em resposta a um tempo limite.</span><span class="sxs-lookup"><span data-stu-id="2887c-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2887c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2887c-113">Requirements</span></span>  
 <span data-ttu-id="2887c-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2887c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2887c-115">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2887c-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2887c-116">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2887c-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2887c-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2887c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2887c-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="2887c-118">See also</span></span>

- [<span data-ttu-id="2887c-119">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="2887c-119">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="2887c-120">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="2887c-120">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="2887c-121">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="2887c-121">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="2887c-122">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="2887c-122">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="2887c-123">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="2887c-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
