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
ms.openlocfilehash: 30806394a8895084068acaec6f7d03c6b67bb14b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860572"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="4581f-102">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="4581f-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="4581f-103">Fornece métodos para interação com um item de destino do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="4581f-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4581f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="4581f-104">Methods</span></span>  
  
|<span data-ttu-id="4581f-105">Método</span><span class="sxs-lookup"><span data-stu-id="4581f-105">Method</span></span>|<span data-ttu-id="4581f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4581f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4581f-107">Método GetCurrentThreadID</span><span class="sxs-lookup"><span data-stu-id="4581f-107">GetCurrentThreadID Method</span></span>](iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="4581f-108">Obtém o identificador do sistema operacional para o thread atual.</span><span class="sxs-lookup"><span data-stu-id="4581f-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="4581f-109">Método GetImageBase</span><span class="sxs-lookup"><span data-stu-id="4581f-109">GetImageBase Method</span></span>](iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="4581f-110">Obtém o endereço de memória base da imagem especificada.</span><span class="sxs-lookup"><span data-stu-id="4581f-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="4581f-111">Método GetMachineType</span><span class="sxs-lookup"><span data-stu-id="4581f-111">GetMachineType Method</span></span>](iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="4581f-112">Obtém um identificador para o tipo de instrução que o processo de destino está usando.</span><span class="sxs-lookup"><span data-stu-id="4581f-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="4581f-113">Método GetPointerSize</span><span class="sxs-lookup"><span data-stu-id="4581f-113">GetPointerSize Method</span></span>](iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="4581f-114">Obtém o tamanho, em bytes, de um ponteiro para o destino atual.</span><span class="sxs-lookup"><span data-stu-id="4581f-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="4581f-115">Método GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="4581f-115">GetThreadContext Method</span></span>](iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="4581f-116">Obtém um ponteiro para o contexto do thread com o identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="4581f-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="4581f-117">Método GetTLSValue</span><span class="sxs-lookup"><span data-stu-id="4581f-117">GetTLSValue Method</span></span>](iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="4581f-118">Obtém um valor no armazenamento local de thread (TLS) no índice especificado para o thread especificado.</span><span class="sxs-lookup"><span data-stu-id="4581f-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="4581f-119">Método ReadVirtual</span><span class="sxs-lookup"><span data-stu-id="4581f-119">ReadVirtual Method</span></span>](iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="4581f-120">Lê dados do endereço de memória virtual especificado no buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="4581f-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="4581f-121">Método Request</span><span class="sxs-lookup"><span data-stu-id="4581f-121">Request Method</span></span>](iclrdatatarget-request-method.md)|<span data-ttu-id="4581f-122">Chamado pelos serviços de acesso a dados do Common Language Runtime (CLR) para solicitar uma operação, conforme definido pela implementação.</span><span class="sxs-lookup"><span data-stu-id="4581f-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="4581f-123">Método SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="4581f-123">SetThreadContext Method</span></span>](iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="4581f-124">Define o contexto atual do thread especificado no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="4581f-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="4581f-125">Método SetTLSValue</span><span class="sxs-lookup"><span data-stu-id="4581f-125">SetTLSValue Method</span></span>](iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="4581f-126">Define um valor no armazenamento local de threads (TLS) do thread especificado no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="4581f-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="4581f-127">Método WriteVirtual</span><span class="sxs-lookup"><span data-stu-id="4581f-127">WriteVirtual Method</span></span>](iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="4581f-128">Grava dados do buffer especificado para o endereço de memória virtual especificado.</span><span class="sxs-lookup"><span data-stu-id="4581f-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4581f-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="4581f-129">Remarks</span></span>  
 <span data-ttu-id="4581f-130">O cliente de API (ou seja, o depurador) deve implementar essa interface conforme apropriado para o item de destino específico.</span><span class="sxs-lookup"><span data-stu-id="4581f-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="4581f-131">Por exemplo, um processo dinâmico teria uma implementação diferente da implementação de um despejo de memória.</span><span class="sxs-lookup"><span data-stu-id="4581f-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4581f-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4581f-132">Requirements</span></span>  
 <span data-ttu-id="4581f-133">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4581f-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4581f-134">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="4581f-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4581f-135">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4581f-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4581f-136">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4581f-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4581f-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="4581f-137">See also</span></span>

- [<span data-ttu-id="4581f-138">Interface ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="4581f-138">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="4581f-139">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4581f-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
