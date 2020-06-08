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
ms.openlocfilehash: f577e9252d97ec188ff1076fd8340336b16c8257
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504323"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="2a4da-102">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="2a4da-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="2a4da-103">Fornece o método [IActionOnCLREvent:: OnEvent](iactiononclrevent-onevent-method.md) , que executa retornos de chamada em eventos que foram registrados usando uma chamada para o método [ICLROnEventManager:: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2a4da-103">Provides the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2a4da-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2a4da-104">Methods</span></span>  
  
|<span data-ttu-id="2a4da-105">Método</span><span class="sxs-lookup"><span data-stu-id="2a4da-105">Method</span></span>|<span data-ttu-id="2a4da-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a4da-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2a4da-107">Método OnEvent</span><span class="sxs-lookup"><span data-stu-id="2a4da-107">OnEvent Method</span></span>](iactiononclrevent-onevent-method.md)|<span data-ttu-id="2a4da-108">Executa um retorno de chamada para um evento registrado.</span><span class="sxs-lookup"><span data-stu-id="2a4da-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a4da-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a4da-109">Requirements</span></span>  
 <span data-ttu-id="2a4da-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a4da-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a4da-111">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2a4da-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2a4da-112">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2a4da-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a4da-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a4da-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a4da-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="2a4da-114">See also</span></span>

- [<span data-ttu-id="2a4da-115">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="2a4da-115">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="2a4da-116">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="2a4da-116">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="2a4da-117">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="2a4da-117">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="2a4da-118">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="2a4da-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
