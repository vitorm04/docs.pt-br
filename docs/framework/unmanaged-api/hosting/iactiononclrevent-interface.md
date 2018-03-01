---
title: Interface IActionOnCLREvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4b51784f07a90faa9eeb29c18a784d4fbc2c4654
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="b17ae-102">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="b17ae-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="b17ae-103">Fornece o [Iactiononclrevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) método, que executa os retornos de chamada em eventos registrados por meio de uma chamada para o [Iclroneventmanager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b17ae-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b17ae-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b17ae-104">Methods</span></span>  
  
|<span data-ttu-id="b17ae-105">Método</span><span class="sxs-lookup"><span data-stu-id="b17ae-105">Method</span></span>|<span data-ttu-id="b17ae-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b17ae-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b17ae-107">Método OnEvent</span><span class="sxs-lookup"><span data-stu-id="b17ae-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="b17ae-108">Executa um retorno de chamada para um evento registrado.</span><span class="sxs-lookup"><span data-stu-id="b17ae-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b17ae-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b17ae-109">Requirements</span></span>  
 <span data-ttu-id="b17ae-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b17ae-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b17ae-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b17ae-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b17ae-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b17ae-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b17ae-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b17ae-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b17ae-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b17ae-114">See Also</span></span>  
 [<span data-ttu-id="b17ae-115">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="b17ae-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="b17ae-116">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="b17ae-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="b17ae-117">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="b17ae-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="b17ae-118">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="b17ae-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
