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
ms.openlocfilehash: 6ba7b7adc104db528293d77c3591370c6ce02c25
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128593"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="6cf80-102">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="6cf80-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="6cf80-103">Fornece métodos que notificam o host das ações que o Common Language Runtime (CLR) executa em caso de anulações, tempos limite ou falhas.</span><span class="sxs-lookup"><span data-stu-id="6cf80-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6cf80-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6cf80-104">Methods</span></span>  
  
|<span data-ttu-id="6cf80-105">Método</span><span class="sxs-lookup"><span data-stu-id="6cf80-105">Method</span></span>|<span data-ttu-id="6cf80-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6cf80-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6cf80-107">Método OnDefaultAction</span><span class="sxs-lookup"><span data-stu-id="6cf80-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="6cf80-108">Notifica o host de que o CLR está prestes a tomar a ação padrão especificada por uma chamada para [ICLRPolicyManager:: Setpadrãoaction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) em resposta a um descarregamento de thread ou de <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="6cf80-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="6cf80-109">Método OnFailure</span><span class="sxs-lookup"><span data-stu-id="6cf80-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="6cf80-110">Notifica o host de que o CLR está prestes a executar a ação especificada por uma chamada para [ICLRPolicyManager:: SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) em resposta a uma alocação de recurso ou falha de recuperação.</span><span class="sxs-lookup"><span data-stu-id="6cf80-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="6cf80-111">Método OnTimeout</span><span class="sxs-lookup"><span data-stu-id="6cf80-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="6cf80-112">Notifica o host de que o CLR está prestes a executar a ação especificada por uma chamada para [ICLRPolicyManager:: SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) em resposta a um tempo limite.</span><span class="sxs-lookup"><span data-stu-id="6cf80-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6cf80-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6cf80-113">Requirements</span></span>  
 <span data-ttu-id="6cf80-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cf80-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cf80-115">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6cf80-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6cf80-116">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6cf80-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6cf80-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cf80-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cf80-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6cf80-118">See also</span></span>

- [<span data-ttu-id="6cf80-119">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="6cf80-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="6cf80-120">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="6cf80-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="6cf80-121">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="6cf80-121">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="6cf80-122">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="6cf80-122">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="6cf80-123">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="6cf80-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
