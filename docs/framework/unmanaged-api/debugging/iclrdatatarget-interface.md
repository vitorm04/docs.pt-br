---
title: Interface ICLRDataTarget
ms.date: 03/30/2017
api_name:
- ICLRDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget
helpviewer_keywords:
- ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type:
- apiref
ms.openlocfilehash: 51b246e45b8bbdf809f5e90ac2bc29ca724751fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113498"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="6bdea-102">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="6bdea-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="6bdea-103">Fornece métodos para interação com um item de destino do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="6bdea-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6bdea-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6bdea-104">Methods</span></span>  
  
|<span data-ttu-id="6bdea-105">Método</span><span class="sxs-lookup"><span data-stu-id="6bdea-105">Method</span></span>|<span data-ttu-id="6bdea-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6bdea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6bdea-107">Método GetCurrentThreadID</span><span class="sxs-lookup"><span data-stu-id="6bdea-107">GetCurrentThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="6bdea-108">Obtém o identificador do sistema operacional para o thread atual.</span><span class="sxs-lookup"><span data-stu-id="6bdea-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="6bdea-109">Método GetImageBase</span><span class="sxs-lookup"><span data-stu-id="6bdea-109">GetImageBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="6bdea-110">Obtém o endereço de memória base da imagem especificada.</span><span class="sxs-lookup"><span data-stu-id="6bdea-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="6bdea-111">Método GetMachineType</span><span class="sxs-lookup"><span data-stu-id="6bdea-111">GetMachineType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="6bdea-112">Obtém um identificador para o tipo de instrução que o processo de destino está usando.</span><span class="sxs-lookup"><span data-stu-id="6bdea-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="6bdea-113">Método GetPointerSize</span><span class="sxs-lookup"><span data-stu-id="6bdea-113">GetPointerSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="6bdea-114">Obtém o tamanho, em bytes, de um ponteiro para o destino atual.</span><span class="sxs-lookup"><span data-stu-id="6bdea-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="6bdea-115">Método GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="6bdea-115">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="6bdea-116">Obtém um ponteiro para o contexto do thread com o identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="6bdea-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="6bdea-117">Método GetTLSValue</span><span class="sxs-lookup"><span data-stu-id="6bdea-117">GetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="6bdea-118">Obtém um valor no armazenamento local de thread (TLS) no índice especificado para o thread especificado.</span><span class="sxs-lookup"><span data-stu-id="6bdea-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="6bdea-119">Método ReadVirtual</span><span class="sxs-lookup"><span data-stu-id="6bdea-119">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="6bdea-120">Lê dados do endereço de memória virtual especificado no buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="6bdea-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="6bdea-121">Método Request</span><span class="sxs-lookup"><span data-stu-id="6bdea-121">Request Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|<span data-ttu-id="6bdea-122">Chamado pelos serviços de acesso a dados do Common Language Runtime (CLR) para solicitar uma operação, conforme definido pela implementação.</span><span class="sxs-lookup"><span data-stu-id="6bdea-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="6bdea-123">Método SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="6bdea-123">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="6bdea-124">Define o contexto atual do thread especificado no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="6bdea-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="6bdea-125">Método SetTLSValue</span><span class="sxs-lookup"><span data-stu-id="6bdea-125">SetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="6bdea-126">Define um valor no armazenamento local de threads (TLS) do thread especificado no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="6bdea-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="6bdea-127">Método WriteVirtual</span><span class="sxs-lookup"><span data-stu-id="6bdea-127">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="6bdea-128">Grava dados do buffer especificado para o endereço de memória virtual especificado.</span><span class="sxs-lookup"><span data-stu-id="6bdea-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bdea-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="6bdea-129">Remarks</span></span>  
 <span data-ttu-id="6bdea-130">O cliente de API (ou seja, o depurador) deve implementar essa interface conforme apropriado para o item de destino específico.</span><span class="sxs-lookup"><span data-stu-id="6bdea-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="6bdea-131">Por exemplo, um processo dinâmico teria uma implementação diferente da implementação de um despejo de memória.</span><span class="sxs-lookup"><span data-stu-id="6bdea-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bdea-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6bdea-132">Requirements</span></span>  
 <span data-ttu-id="6bdea-133">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bdea-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bdea-134">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="6bdea-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="6bdea-135">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bdea-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bdea-136">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bdea-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bdea-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bdea-137">See also</span></span>

- [<span data-ttu-id="6bdea-138">Interface ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="6bdea-138">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="6bdea-139">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6bdea-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
