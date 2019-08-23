---
title: Interface ICorDebugInstanceFieldSymbol
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e5f63df9354df6a4d142c2f6ae12f9a0d5600fb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910133"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="3b6d0-102">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="3b6d0-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="3b6d0-103">Representa as informações de símbolo de depuração de um campo de instância.</span><span class="sxs-lookup"><span data-stu-id="3b6d0-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3b6d0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3b6d0-104">Methods</span></span>  
  
|<span data-ttu-id="3b6d0-105">Método</span><span class="sxs-lookup"><span data-stu-id="3b6d0-105">Method</span></span>|<span data-ttu-id="3b6d0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b6d0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3b6d0-107">Método GetName</span><span class="sxs-lookup"><span data-stu-id="3b6d0-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="3b6d0-108">Obtém o nome do campo de instância.</span><span class="sxs-lookup"><span data-stu-id="3b6d0-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="3b6d0-109">Método GetOffset</span><span class="sxs-lookup"><span data-stu-id="3b6d0-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="3b6d0-110">Obtém o deslocamento em bytes deste campo de instância em sua classe pai.</span><span class="sxs-lookup"><span data-stu-id="3b6d0-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="3b6d0-111">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="3b6d0-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="3b6d0-112">Obtém o tamanho em bytes do campo de instância.</span><span class="sxs-lookup"><span data-stu-id="3b6d0-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b6d0-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="3b6d0-113">Remarks</span></span>  
 <span data-ttu-id="3b6d0-114">A `ICorDebugInstanceFieldSymbol` interface é usada para recuperar as informações de símbolo de depuração para um campo de instância.</span><span class="sxs-lookup"><span data-stu-id="3b6d0-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b6d0-115">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3b6d0-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="3b6d0-116">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="3b6d0-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b6d0-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3b6d0-117">Requirements</span></span>  
 <span data-ttu-id="3b6d0-118">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b6d0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b6d0-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b6d0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b6d0-120">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b6d0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b6d0-121">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b6d0-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b6d0-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b6d0-122">See also</span></span>

- [<span data-ttu-id="3b6d0-123">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="3b6d0-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="3b6d0-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3b6d0-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3b6d0-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="3b6d0-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
