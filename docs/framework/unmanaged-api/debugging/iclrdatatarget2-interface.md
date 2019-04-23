---
title: Interface ICLRDataTarget2
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2
helpviewer_keywords:
- ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d21bced214242866c47f40f392593f3f51cda02f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104709"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="42488-102">Interface ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="42488-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="42488-103">Uma subclasse de [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) que é usada pela camada de serviços de acesso a dados para manipular as regiões de memória virtual no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="42488-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="42488-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="42488-104">Methods</span></span>  
  
|<span data-ttu-id="42488-105">Método</span><span class="sxs-lookup"><span data-stu-id="42488-105">Method</span></span>|<span data-ttu-id="42488-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="42488-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="42488-107">Método AllocVirtual</span><span class="sxs-lookup"><span data-stu-id="42488-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="42488-108">Aloca memória no espaço de endereço do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="42488-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="42488-109">Método FreeVirtual</span><span class="sxs-lookup"><span data-stu-id="42488-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="42488-110">Libera memória anteriormente alocada no espaço de endereço do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="42488-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42488-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="42488-111">Remarks</span></span>  
 <span data-ttu-id="42488-112">O cliente da API (ou seja, o depurador) deve implementar a interface conforme o apropriado para o processo de destino específico.</span><span class="sxs-lookup"><span data-stu-id="42488-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="42488-113">Por exemplo, um processo dinâmico teria uma implementação diferente da implementação de um despejo de memória.</span><span class="sxs-lookup"><span data-stu-id="42488-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="42488-114">O destino pode não oferecer suporte à modificação de suas regiões de memória.</span><span class="sxs-lookup"><span data-stu-id="42488-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42488-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="42488-115">Requirements</span></span>  
 <span data-ttu-id="42488-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42488-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42488-117">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="42488-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="42488-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42488-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42488-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42488-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42488-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42488-120">See also</span></span>

- [<span data-ttu-id="42488-121">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="42488-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [<span data-ttu-id="42488-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="42488-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
