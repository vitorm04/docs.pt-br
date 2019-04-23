---
title: Interface ICLRDataTarget3
ms.date: 03/30/2017
api_name:
- ICLRDataTarget3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df113a2839b0f2651e15f4029d86cc5efc171c63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111807"
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="c28aa-102">Interface ICLRDataTarget3</span><span class="sxs-lookup"><span data-stu-id="c28aa-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="c28aa-103">Uma subclasse de [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) que fornece acesso a informações de exceção.</span><span class="sxs-lookup"><span data-stu-id="c28aa-103">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c28aa-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c28aa-104">Methods</span></span>  
  
|<span data-ttu-id="c28aa-105">Método</span><span class="sxs-lookup"><span data-stu-id="c28aa-105">Method</span></span>|<span data-ttu-id="c28aa-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c28aa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c28aa-107">Método GetExceptionRecord</span><span class="sxs-lookup"><span data-stu-id="c28aa-107">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="c28aa-108">Chamado pelo serviço de acesso a dados do CLR (Common Language Runtime) para recuperar o registro de exceção associado ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="c28aa-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="c28aa-109">Método GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="c28aa-109">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="c28aa-110">Chamado pelo serviço de acesso a dados do CLR para recuperar o registro de contexto associado ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="c28aa-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="c28aa-111">Método GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="c28aa-111">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="c28aa-112">Chamado pelos serviços de acesso a dados do CLR para obter o ID do thread que lança a exceção.</span><span class="sxs-lookup"><span data-stu-id="c28aa-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c28aa-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="c28aa-113">Remarks</span></span>  
 <span data-ttu-id="c28aa-114">O cliente da API (ou seja, o depurador) deve implementar a interface conforme o apropriado para o processo de destino específico.</span><span class="sxs-lookup"><span data-stu-id="c28aa-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="c28aa-115">Por exemplo, um processo dinâmico teria uma implementação diferente da implementação de um despejo de memória.</span><span class="sxs-lookup"><span data-stu-id="c28aa-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="c28aa-116">O destino pode não oferecer suporte à modificação de suas regiões de memória.</span><span class="sxs-lookup"><span data-stu-id="c28aa-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c28aa-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c28aa-117">Requirements</span></span>  
 <span data-ttu-id="c28aa-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c28aa-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c28aa-119">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c28aa-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c28aa-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c28aa-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c28aa-121">**Versões do .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c28aa-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c28aa-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c28aa-122">See also</span></span>

- [<span data-ttu-id="c28aa-123">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="c28aa-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [<span data-ttu-id="c28aa-124">Interface ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="c28aa-124">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="c28aa-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c28aa-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
