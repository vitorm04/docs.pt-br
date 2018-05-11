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
ms.openlocfilehash: 6fc26694bded2c7df1a53a96e8743f3be73c93eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="7286c-102">Interface ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="7286c-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="7286c-103">Uma subclasse de [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) que é usado pela camada de serviços de acesso a dados para manipular as regiões de memória virtual no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="7286c-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7286c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="7286c-104">Methods</span></span>  
  
|<span data-ttu-id="7286c-105">Método</span><span class="sxs-lookup"><span data-stu-id="7286c-105">Method</span></span>|<span data-ttu-id="7286c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7286c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7286c-107">Método AllocVirtual</span><span class="sxs-lookup"><span data-stu-id="7286c-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="7286c-108">Aloca memória no espaço de endereço do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="7286c-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="7286c-109">Método FreeVirtual</span><span class="sxs-lookup"><span data-stu-id="7286c-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="7286c-110">Libera a memória que antes era alocada no espaço de endereço do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="7286c-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7286c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="7286c-111">Remarks</span></span>  
 <span data-ttu-id="7286c-112">O cliente da API (ou seja, o depurador) deve implementar a interface conforme o apropriado para o processo de destino específico.</span><span class="sxs-lookup"><span data-stu-id="7286c-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="7286c-113">Por exemplo, um processo dinâmico teria uma implementação diferente da implementação de um despejo de memória.</span><span class="sxs-lookup"><span data-stu-id="7286c-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="7286c-114">O destino pode não oferecer suporte à modificação de suas regiões de memória.</span><span class="sxs-lookup"><span data-stu-id="7286c-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7286c-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7286c-115">Requirements</span></span>  
 <span data-ttu-id="7286c-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7286c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7286c-117">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="7286c-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7286c-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7286c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7286c-119">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7286c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7286c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7286c-120">See Also</span></span>  
 [<span data-ttu-id="7286c-121">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="7286c-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="7286c-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7286c-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
