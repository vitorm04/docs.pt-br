---
title: Interface ICLROnEventManager
ms.date: 03/30/2017
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
ms.openlocfilehash: a1b22e77fe20d5e2d755efcd7a63c8f2bdc781e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140847"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="b89b9-102">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="b89b9-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="b89b9-103">Fornece métodos que permitem ao host registrar e cancelar o registro de retornos de chamada para eventos de Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b89b9-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b89b9-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b89b9-104">Methods</span></span>  
  
|<span data-ttu-id="b89b9-105">Método</span><span class="sxs-lookup"><span data-stu-id="b89b9-105">Method</span></span>|<span data-ttu-id="b89b9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b89b9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b89b9-107">Método RegisterActionOnEvent</span><span class="sxs-lookup"><span data-stu-id="b89b9-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="b89b9-108">Registra um ponteiro de retorno de chamada para o evento especificado.</span><span class="sxs-lookup"><span data-stu-id="b89b9-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="b89b9-109">Método UnregisterActionOnEvent</span><span class="sxs-lookup"><span data-stu-id="b89b9-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="b89b9-110">Cancela o registro de um ponteiro de retorno de chamada registrado anteriormente para o evento especificado.</span><span class="sxs-lookup"><span data-stu-id="b89b9-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b89b9-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b89b9-111">Remarks</span></span>  
 <span data-ttu-id="b89b9-112">Para registrar e cancelar o registro de retornos de chamada de evento, o host obtém uma referência a `ICLROnEventManager` chamando o método [ICLRControl:: GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b89b9-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b89b9-113">Os eventos descritos por [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) podem ser acionados mais de uma vez e de threads diferentes para sinalizar um descarregamento ou desabilitar o CLR.</span><span class="sxs-lookup"><span data-stu-id="b89b9-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b89b9-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b89b9-114">Requirements</span></span>  
 <span data-ttu-id="b89b9-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b89b9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b89b9-116">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b89b9-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b89b9-117">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b89b9-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b89b9-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b89b9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b89b9-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b89b9-119">See also</span></span>

- [<span data-ttu-id="b89b9-120">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="b89b9-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="b89b9-121">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="b89b9-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="b89b9-122">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="b89b9-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="b89b9-123">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="b89b9-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
