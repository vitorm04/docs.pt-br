---
title: Interface ICorDebugDataTarget
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c6a8ee1bcc65e640ef871e57acdeef21acd7896
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930830"
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="56f2f-102">Interface ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="56f2f-102">ICorDebugDataTarget Interface</span></span>
<span data-ttu-id="56f2f-103">Fornece uma interface de retorno de chamada que oferece acesso a um determinado processo de destino.</span><span class="sxs-lookup"><span data-stu-id="56f2f-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="56f2f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="56f2f-104">Methods</span></span>  
  
|<span data-ttu-id="56f2f-105">Método</span><span class="sxs-lookup"><span data-stu-id="56f2f-105">Method</span></span>|<span data-ttu-id="56f2f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="56f2f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="56f2f-107">Método GetPlatform</span><span class="sxs-lookup"><span data-stu-id="56f2f-107">GetPlatform Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="56f2f-108">Fornece informações sobre a plataforma, incluindo arquitetura do processador e sistema operacional, em que o processo de destino está em execução.</span><span class="sxs-lookup"><span data-stu-id="56f2f-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="56f2f-109">Método ReadVirtual</span><span class="sxs-lookup"><span data-stu-id="56f2f-109">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="56f2f-110">Obtém um bloco de memória contígua a partir do endereço especificado e a retorna no buffer fornecido.</span><span class="sxs-lookup"><span data-stu-id="56f2f-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="56f2f-111">Método GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="56f2f-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="56f2f-112">Solicita o contexto de thread atual para o thread especificado.</span><span class="sxs-lookup"><span data-stu-id="56f2f-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56f2f-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="56f2f-113">Remarks</span></span>  
 <span data-ttu-id="56f2f-114">`ICorDebugDataTarget`e seus métodos têm as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="56f2f-114">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
- <span data-ttu-id="56f2f-115">Os serviços de depuração chamam os métodos nessa interface para acessar a memória e outros dados no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="56f2f-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
- <span data-ttu-id="56f2f-116">O cliente do depurador deve implementar essa interface conforme apropriado para o destino específico (por exemplo, um processo ao vivo ou um despejo de memória).</span><span class="sxs-lookup"><span data-stu-id="56f2f-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
- <span data-ttu-id="56f2f-117">Os `ICorDebugDataTarget` métodos podem ser invocados somente de dentro de métodos implementados em outras `ICorDebug*` interfaces.</span><span class="sxs-lookup"><span data-stu-id="56f2f-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="56f2f-118">Isso garante que o cliente do depurador tenha controle sobre qual thread ele é invocado e quando.</span><span class="sxs-lookup"><span data-stu-id="56f2f-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
- <span data-ttu-id="56f2f-119">A `ICorDebugDataTarget` implementação sempre deve retornar informações atualizadas sobre o destino.</span><span class="sxs-lookup"><span data-stu-id="56f2f-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="56f2f-120">O processo de destino deve ser interrompido e não alterado de nenhuma forma `ICorDebug*` enquanto as interfaces ( `ICorDebugDataTarget` e, portanto, os métodos) estão sendo chamadas.</span><span class="sxs-lookup"><span data-stu-id="56f2f-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="56f2f-121">Se o destino for um processo ao vivo e seu estado for alterado, o método [ICLRDebugging:: OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) precisará ser chamado novamente para fornecer uma instância de ICorDebugProcess substituta.</span><span class="sxs-lookup"><span data-stu-id="56f2f-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56f2f-122">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="56f2f-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56f2f-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="56f2f-123">Requirements</span></span>  
 <span data-ttu-id="56f2f-124">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56f2f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56f2f-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56f2f-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56f2f-126">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56f2f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56f2f-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56f2f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f2f-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56f2f-128">See also</span></span>

- [<span data-ttu-id="56f2f-129">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="56f2f-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="56f2f-130">Depuração</span><span class="sxs-lookup"><span data-stu-id="56f2f-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
