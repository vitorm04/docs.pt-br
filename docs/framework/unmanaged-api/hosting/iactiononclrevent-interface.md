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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 864a8a4dd9f96da2fd0e0025848a910b4f8b0a70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985524"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="e642a-102">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="e642a-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="e642a-103">Fornece o [iactiononclrevent:: ONEVENT](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) método, o que faz retornos de chamada de eventos que foram registrados por meio de uma chamada para o [iclroneventmanager:: Registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="e642a-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e642a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="e642a-104">Methods</span></span>  
  
|<span data-ttu-id="e642a-105">Método</span><span class="sxs-lookup"><span data-stu-id="e642a-105">Method</span></span>|<span data-ttu-id="e642a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e642a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e642a-107">Método OnEvent</span><span class="sxs-lookup"><span data-stu-id="e642a-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="e642a-108">Executa um retorno de chamada para um evento registrado.</span><span class="sxs-lookup"><span data-stu-id="e642a-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e642a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e642a-109">Requirements</span></span>  
 <span data-ttu-id="e642a-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e642a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e642a-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e642a-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e642a-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e642a-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e642a-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e642a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e642a-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e642a-114">See also</span></span>

- [<span data-ttu-id="e642a-115">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="e642a-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="e642a-116">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="e642a-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="e642a-117">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="e642a-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="e642a-118">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="e642a-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
