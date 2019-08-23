---
title: Interface ICorDebugDataTarget2
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57ea68474a1ee3a856b2e9393ff67d44f40a471c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911436"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="4b906-102">Interface ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="4b906-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="4b906-103">Estende logicamente a interface [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4b906-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b906-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="4b906-104">Methods</span></span>  
  
|<span data-ttu-id="4b906-105">Método</span><span class="sxs-lookup"><span data-stu-id="4b906-105">Method</span></span>|<span data-ttu-id="4b906-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b906-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b906-107">Método CreateVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="4b906-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="4b906-108">Cria um novo unwinder de pilha que inicia o desenrolamento de um contexto inicial (que não é necessariamente folha de um thread).</span><span class="sxs-lookup"><span data-stu-id="4b906-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="4b906-109">Método EnumerateThreadIDs</span><span class="sxs-lookup"><span data-stu-id="4b906-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="4b906-110">Retorna uma lista de IDs de thread ativo.</span><span class="sxs-lookup"><span data-stu-id="4b906-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="4b906-111">Método GetImageFromPointer</span><span class="sxs-lookup"><span data-stu-id="4b906-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="4b906-112">Retorna o endereço base do módulo e o tamanho de um endereço no módulo.</span><span class="sxs-lookup"><span data-stu-id="4b906-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="4b906-113">Método GetImageLocation</span><span class="sxs-lookup"><span data-stu-id="4b906-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="4b906-114">Retorna o caminho de um módulo de endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="4b906-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="4b906-115">Método GetSymbolProviderForImage</span><span class="sxs-lookup"><span data-stu-id="4b906-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="4b906-116">Retorna o provedor de símbolo para um módulo do endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="4b906-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b906-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b906-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b906-118">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4b906-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="4b906-119">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="4b906-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b906-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b906-120">Requirements</span></span>  
 <span data-ttu-id="4b906-121">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b906-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b906-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b906-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b906-123">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b906-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b906-124">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b906-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b906-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b906-125">See also</span></span>

- [<span data-ttu-id="4b906-126">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4b906-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="4b906-127">Depuração</span><span class="sxs-lookup"><span data-stu-id="4b906-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
