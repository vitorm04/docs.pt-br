---
title: Interface ICLROnEventManager
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
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 02a19a3daf72cdfa493b09fa984fe7b50865ed30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="97f4f-102">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="97f4f-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="97f4f-103">Fornece métodos que permitem que o host registrar e cancelar o registro de retornos de chamada para eventos de tempo de execução (CLR) de linguagem comum.</span><span class="sxs-lookup"><span data-stu-id="97f4f-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97f4f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="97f4f-104">Methods</span></span>  
  
|<span data-ttu-id="97f4f-105">Método</span><span class="sxs-lookup"><span data-stu-id="97f4f-105">Method</span></span>|<span data-ttu-id="97f4f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="97f4f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97f4f-107">Método RegisterActionOnEvent</span><span class="sxs-lookup"><span data-stu-id="97f4f-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="97f4f-108">Registra um ponteiro de retorno de chamada para o evento especificado.</span><span class="sxs-lookup"><span data-stu-id="97f4f-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="97f4f-109">Método UnregisterActionOnEvent</span><span class="sxs-lookup"><span data-stu-id="97f4f-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="97f4f-110">Cancela o registro de um ponteiro de retorno de chamada registrado anteriormente para o evento especificado.</span><span class="sxs-lookup"><span data-stu-id="97f4f-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97f4f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="97f4f-111">Remarks</span></span>  
 <span data-ttu-id="97f4f-112">Para registrar e cancelar o registro de retornos de chamada de evento, o host obtém uma referência a `ICLROnEventManager` chamando o [Iclrcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="97f4f-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97f4f-113">Os eventos descritos por [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) podem ser acionados mais de uma vez e de diversos threads para sinalizar um descarregamento ou a desabilitação do CLR.</span><span class="sxs-lookup"><span data-stu-id="97f4f-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97f4f-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="97f4f-114">Requirements</span></span>  
 <span data-ttu-id="97f4f-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97f4f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97f4f-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="97f4f-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97f4f-117">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="97f4f-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97f4f-118">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97f4f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97f4f-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97f4f-119">See Also</span></span>  
 [<span data-ttu-id="97f4f-120">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="97f4f-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="97f4f-121">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="97f4f-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="97f4f-122">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="97f4f-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="97f4f-123">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="97f4f-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
