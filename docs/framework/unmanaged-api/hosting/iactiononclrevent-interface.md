---
title: Interface IActionOnCLREvent
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent
helpviewer_keywords:
- IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type:
- apiref
ms.openlocfilehash: 9277fe2c241ce4f502339de826dccd08a2ce8055
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126966"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="e0511-102">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="e0511-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="e0511-103">Fornece o método [IActionOnCLREvent:: OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) , que executa retornos de chamada em eventos que foram registrados usando uma chamada para o método [ICLROnEventManager:: RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e0511-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e0511-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="e0511-104">Methods</span></span>  
  
|<span data-ttu-id="e0511-105">Método</span><span class="sxs-lookup"><span data-stu-id="e0511-105">Method</span></span>|<span data-ttu-id="e0511-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0511-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e0511-107">Método OnEvent</span><span class="sxs-lookup"><span data-stu-id="e0511-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="e0511-108">Executa um retorno de chamada para um evento registrado.</span><span class="sxs-lookup"><span data-stu-id="e0511-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0511-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0511-109">Requirements</span></span>  
 <span data-ttu-id="e0511-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0511-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0511-111">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e0511-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0511-112">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e0511-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0511-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0511-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0511-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0511-114">See also</span></span>

- [<span data-ttu-id="e0511-115">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="e0511-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="e0511-116">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="e0511-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="e0511-117">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="e0511-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="e0511-118">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="e0511-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
