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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7247dddc2d3313948fe6f49fbaa1440b141c4cf3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440759"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="998fc-102">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="998fc-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="998fc-103">Fornece métodos que notificam o host das ações que executa o common language runtime (CLR) no caso do anula, tempos limites ou falhas.</span><span class="sxs-lookup"><span data-stu-id="998fc-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="998fc-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="998fc-104">Methods</span></span>  
  
|<span data-ttu-id="998fc-105">Método</span><span class="sxs-lookup"><span data-stu-id="998fc-105">Method</span></span>|<span data-ttu-id="998fc-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="998fc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="998fc-107">Método OnDefaultAction</span><span class="sxs-lookup"><span data-stu-id="998fc-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="998fc-108">Notifica o host que o CLR está prestes a realizar a ação padrão especificada por uma chamada para [SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) em resposta a um thread de anulação ou <xref:System.AppDomain> descarregar.</span><span class="sxs-lookup"><span data-stu-id="998fc-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="998fc-109">Método OnFailure</span><span class="sxs-lookup"><span data-stu-id="998fc-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="998fc-110">Notifica o host que o CLR está prestes a realizar a ação especificada por uma chamada para [SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) em resposta a uma falha de alocação ou recuperação de recursos.</span><span class="sxs-lookup"><span data-stu-id="998fc-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="998fc-111">Método OnTimeout</span><span class="sxs-lookup"><span data-stu-id="998fc-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="998fc-112">Notifica o host que o CLR está prestes a realizar a ação especificada por uma chamada para [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) em resposta a um tempo limite.</span><span class="sxs-lookup"><span data-stu-id="998fc-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="998fc-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="998fc-113">Requirements</span></span>  
 <span data-ttu-id="998fc-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="998fc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="998fc-115">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="998fc-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="998fc-116">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="998fc-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="998fc-117">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="998fc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="998fc-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="998fc-118">See Also</span></span>  
 [<span data-ttu-id="998fc-119">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="998fc-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="998fc-120">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="998fc-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="998fc-121">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="998fc-121">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="998fc-122">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="998fc-122">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="998fc-123">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="998fc-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
