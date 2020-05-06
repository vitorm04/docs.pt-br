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
ms.openlocfilehash: 6b2700b2f12e312f06640a06e5ec82fbc58f2ca9
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860467"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="0a2fc-102">Interface ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="0a2fc-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="0a2fc-103">Uma subclasse de [ICLRDataTarget](iclrdatatarget-interface.md) que é usada pela camada de serviços de acesso a dados para manipular regiões de memória virtual no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="0a2fc-103">A subclass of [ICLRDataTarget](iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a2fc-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="0a2fc-104">Methods</span></span>  
  
|<span data-ttu-id="0a2fc-105">Método</span><span class="sxs-lookup"><span data-stu-id="0a2fc-105">Method</span></span>|<span data-ttu-id="0a2fc-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a2fc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a2fc-107">Método AllocVirtual</span><span class="sxs-lookup"><span data-stu-id="0a2fc-107">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="0a2fc-108">Aloca memória no espaço de endereço do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="0a2fc-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="0a2fc-109">Método FreeVirtual</span><span class="sxs-lookup"><span data-stu-id="0a2fc-109">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="0a2fc-110">Libera a memória que foi alocada anteriormente no espaço de endereço do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="0a2fc-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a2fc-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="0a2fc-111">Remarks</span></span>  
 <span data-ttu-id="0a2fc-112">O cliente da API (ou seja, o depurador) deve implementar a interface conforme o apropriado para o processo de destino específico.</span><span class="sxs-lookup"><span data-stu-id="0a2fc-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="0a2fc-113">Por exemplo, um processo dinâmico teria uma implementação diferente da implementação de um despejo de memória.</span><span class="sxs-lookup"><span data-stu-id="0a2fc-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="0a2fc-114">O destino pode não oferecer suporte à modificação de suas regiões de memória.</span><span class="sxs-lookup"><span data-stu-id="0a2fc-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a2fc-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0a2fc-115">Requirements</span></span>  
 <span data-ttu-id="0a2fc-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a2fc-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a2fc-117">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="0a2fc-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0a2fc-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a2fc-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a2fc-119">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a2fc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a2fc-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="0a2fc-120">See also</span></span>

- [<span data-ttu-id="0a2fc-121">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="0a2fc-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="0a2fc-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="0a2fc-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
