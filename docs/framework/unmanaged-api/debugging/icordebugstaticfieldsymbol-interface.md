---
title: Interface ICorDebugStaticFieldSymbol
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f4e245e96ac9d47db10072e50a5b3c516d5dd27
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962675"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="c928d-102">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="c928d-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="c928d-103">Representa as informações de símbolo de depuração de um campo estático.</span><span class="sxs-lookup"><span data-stu-id="c928d-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c928d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c928d-104">Methods</span></span>  
  
|<span data-ttu-id="c928d-105">Método</span><span class="sxs-lookup"><span data-stu-id="c928d-105">Method</span></span>|<span data-ttu-id="c928d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c928d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c928d-107">Método GetAddress</span><span class="sxs-lookup"><span data-stu-id="c928d-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="c928d-108">Obtém o endereço do campo estático.</span><span class="sxs-lookup"><span data-stu-id="c928d-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="c928d-109">Método GetName</span><span class="sxs-lookup"><span data-stu-id="c928d-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="c928d-110">Obtém o nome do campo estático.</span><span class="sxs-lookup"><span data-stu-id="c928d-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="c928d-111">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="c928d-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="c928d-112">Obtém o tamanho em bytes do campo estático.</span><span class="sxs-lookup"><span data-stu-id="c928d-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c928d-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="c928d-113">Remarks</span></span>  
 <span data-ttu-id="c928d-114">A `ICorDebugStaticFieldSymbol` interface é usada para recuperar as informações de símbolo de depuração para um campo estático.</span><span class="sxs-lookup"><span data-stu-id="c928d-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c928d-115">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c928d-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="c928d-116">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="c928d-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c928d-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c928d-117">Requirements</span></span>  
 <span data-ttu-id="c928d-118">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c928d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c928d-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c928d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c928d-120">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c928d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c928d-121">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c928d-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c928d-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c928d-122">See also</span></span>

- [<span data-ttu-id="c928d-123">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="c928d-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="c928d-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c928d-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c928d-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="c928d-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
