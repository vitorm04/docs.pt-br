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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180503"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="b380e-102">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="b380e-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="b380e-103">Fornece o [iactiononclrevent:: ONEVENT](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) método, o que faz retornos de chamada de eventos que foram registrados por meio de uma chamada para o [iclroneventmanager:: Registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b380e-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b380e-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b380e-104">Methods</span></span>  
  
|<span data-ttu-id="b380e-105">Método</span><span class="sxs-lookup"><span data-stu-id="b380e-105">Method</span></span>|<span data-ttu-id="b380e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b380e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b380e-107">Método OnEvent</span><span class="sxs-lookup"><span data-stu-id="b380e-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="b380e-108">Executa um retorno de chamada para um evento registrado.</span><span class="sxs-lookup"><span data-stu-id="b380e-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b380e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b380e-109">Requirements</span></span>  
 <span data-ttu-id="b380e-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b380e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b380e-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b380e-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b380e-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b380e-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b380e-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b380e-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b380e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b380e-114">See also</span></span>

- [<span data-ttu-id="b380e-115">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="b380e-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="b380e-116">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="b380e-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="b380e-117">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="b380e-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="b380e-118">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="b380e-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
