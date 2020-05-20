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
ms.openlocfilehash: 4e72cd8bee2cb4f35155d7b99cfe8d9cf63f463a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616067"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="e39b6-102">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="e39b6-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="e39b6-103">Fornece o método [IActionOnCLREvent:: OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) , que executa retornos de chamada em eventos que foram registrados usando uma chamada para o método [ICLROnEventManager:: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e39b6-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e39b6-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="e39b6-104">Methods</span></span>  
  
|<span data-ttu-id="e39b6-105">Método</span><span class="sxs-lookup"><span data-stu-id="e39b6-105">Method</span></span>|<span data-ttu-id="e39b6-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e39b6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e39b6-107">Método OnEvent</span><span class="sxs-lookup"><span data-stu-id="e39b6-107">OnEvent Method</span></span>](iactiononclrevent-onevent-method.md)|<span data-ttu-id="e39b6-108">Executa um retorno de chamada para um evento registrado.</span><span class="sxs-lookup"><span data-stu-id="e39b6-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e39b6-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e39b6-109">Requirements</span></span>  
 <span data-ttu-id="e39b6-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e39b6-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e39b6-111">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e39b6-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e39b6-112">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e39b6-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e39b6-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e39b6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e39b6-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="e39b6-114">See also</span></span>

- [<span data-ttu-id="e39b6-115">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="e39b6-115">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="e39b6-116">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="e39b6-116">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="e39b6-117">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="e39b6-117">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="e39b6-118">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="e39b6-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
