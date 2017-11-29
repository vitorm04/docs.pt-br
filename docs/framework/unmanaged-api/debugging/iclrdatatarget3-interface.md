---
title: Interface ICLRDataTarget3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget3
api_location: mscordbi.dll
api_type: COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16e2d2aa1a2626f4124e1b43ff85abcdd17f6990
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="bdac5-102">Interface ICLRDataTarget3</span><span class="sxs-lookup"><span data-stu-id="bdac5-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="bdac5-103">Uma subclasse de [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) que fornece acesso às informações de exceção.</span><span class="sxs-lookup"><span data-stu-id="bdac5-103">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bdac5-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="bdac5-104">Methods</span></span>  
  
|<span data-ttu-id="bdac5-105">Método</span><span class="sxs-lookup"><span data-stu-id="bdac5-105">Method</span></span>|<span data-ttu-id="bdac5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="bdac5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bdac5-107">Método GetExceptionRecord</span><span class="sxs-lookup"><span data-stu-id="bdac5-107">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="bdac5-108">Chamado pelo serviço de acesso a dados do CLR (Common Language Runtime) para recuperar o registro de exceção associado ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="bdac5-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="bdac5-109">Método GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="bdac5-109">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="bdac5-110">Chamado pelo serviço de acesso a dados do CLR para recuperar o registro de contexto associado ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="bdac5-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="bdac5-111">Método GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="bdac5-111">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="bdac5-112">Chamado pelos serviços de acesso a dados do CLR para obter o ID do thread que lança a exceção.</span><span class="sxs-lookup"><span data-stu-id="bdac5-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdac5-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="bdac5-113">Remarks</span></span>  
 <span data-ttu-id="bdac5-114">O cliente da API (ou seja, o depurador) deve implementar a interface conforme o apropriado para o processo de destino específico.</span><span class="sxs-lookup"><span data-stu-id="bdac5-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="bdac5-115">Por exemplo, um processo dinâmico teria uma implementação diferente da implementação de um despejo de memória.</span><span class="sxs-lookup"><span data-stu-id="bdac5-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="bdac5-116">O destino pode não oferecer suporte à modificação de suas regiões de memória.</span><span class="sxs-lookup"><span data-stu-id="bdac5-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdac5-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bdac5-117">Requirements</span></span>  
 <span data-ttu-id="bdac5-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdac5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdac5-119">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="bdac5-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="bdac5-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdac5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdac5-121">**Versões do .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdac5-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdac5-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bdac5-122">See Also</span></span>  
 [<span data-ttu-id="bdac5-123">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="bdac5-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="bdac5-124">Interface ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="bdac5-124">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="bdac5-125">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="bdac5-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
