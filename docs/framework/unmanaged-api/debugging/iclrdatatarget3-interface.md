---
title: Interface ICLRDataTarget3
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
- ICLRDataTarget3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 64ecb4ca4dfd829bb140c3067085c55a7b86c919
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="688d5-102">Interface ICLRDataTarget3</span><span class="sxs-lookup"><span data-stu-id="688d5-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="688d5-103">Uma subclasse de [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) que fornece acesso às informações de exceção.</span><span class="sxs-lookup"><span data-stu-id="688d5-103">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="688d5-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="688d5-104">Methods</span></span>  
  
|<span data-ttu-id="688d5-105">Método</span><span class="sxs-lookup"><span data-stu-id="688d5-105">Method</span></span>|<span data-ttu-id="688d5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="688d5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="688d5-107">Método GetExceptionRecord</span><span class="sxs-lookup"><span data-stu-id="688d5-107">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="688d5-108">Chamado pelo serviço de acesso a dados do CLR (Common Language Runtime) para recuperar o registro de exceção associado ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="688d5-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="688d5-109">Método GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="688d5-109">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="688d5-110">Chamado pelo serviço de acesso a dados do CLR para recuperar o registro de contexto associado ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="688d5-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="688d5-111">Método GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="688d5-111">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="688d5-112">Chamado pelos serviços de acesso a dados do CLR para obter o ID do thread que lança a exceção.</span><span class="sxs-lookup"><span data-stu-id="688d5-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="688d5-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="688d5-113">Remarks</span></span>  
 <span data-ttu-id="688d5-114">O cliente da API (ou seja, o depurador) deve implementar a interface conforme o apropriado para o processo de destino específico.</span><span class="sxs-lookup"><span data-stu-id="688d5-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="688d5-115">Por exemplo, um processo dinâmico teria uma implementação diferente da implementação de um despejo de memória.</span><span class="sxs-lookup"><span data-stu-id="688d5-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="688d5-116">O destino pode não oferecer suporte à modificação de suas regiões de memória.</span><span class="sxs-lookup"><span data-stu-id="688d5-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="688d5-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="688d5-117">Requirements</span></span>  
 <span data-ttu-id="688d5-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="688d5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="688d5-119">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="688d5-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="688d5-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="688d5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="688d5-121">**Versões do .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="688d5-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="688d5-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="688d5-122">See Also</span></span>  
 [<span data-ttu-id="688d5-123">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="688d5-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="688d5-124">Interface ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="688d5-124">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="688d5-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="688d5-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
