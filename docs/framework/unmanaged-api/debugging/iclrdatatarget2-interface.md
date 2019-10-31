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
ms.openlocfilehash: 1f0f4331302e56a90b4aefd657e07981994022ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73112309"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="3be8b-102">Interface ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="3be8b-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="3be8b-103">Uma subclasse de [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) que é usada pela camada de serviços de acesso a dados para manipular regiões de memória virtual no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="3be8b-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3be8b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3be8b-104">Methods</span></span>  
  
|<span data-ttu-id="3be8b-105">Método</span><span class="sxs-lookup"><span data-stu-id="3be8b-105">Method</span></span>|<span data-ttu-id="3be8b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3be8b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3be8b-107">Método AllocVirtual</span><span class="sxs-lookup"><span data-stu-id="3be8b-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="3be8b-108">Aloca memória no espaço de endereço do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="3be8b-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="3be8b-109">Método FreeVirtual</span><span class="sxs-lookup"><span data-stu-id="3be8b-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="3be8b-110">Libera a memória que foi alocada anteriormente no espaço de endereço do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="3be8b-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3be8b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="3be8b-111">Remarks</span></span>  
 <span data-ttu-id="3be8b-112">O cliente da API (ou seja, o depurador) deve implementar a interface conforme o apropriado para o processo de destino específico.</span><span class="sxs-lookup"><span data-stu-id="3be8b-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="3be8b-113">Por exemplo, um processo dinâmico teria uma implementação diferente da implementação de um despejo de memória.</span><span class="sxs-lookup"><span data-stu-id="3be8b-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="3be8b-114">O destino pode não oferecer suporte à modificação de suas regiões de memória.</span><span class="sxs-lookup"><span data-stu-id="3be8b-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3be8b-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3be8b-115">Requirements</span></span>  
 <span data-ttu-id="3be8b-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3be8b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3be8b-117">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="3be8b-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="3be8b-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3be8b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3be8b-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3be8b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3be8b-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3be8b-120">See also</span></span>

- [<span data-ttu-id="3be8b-121">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="3be8b-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [<span data-ttu-id="3be8b-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3be8b-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
