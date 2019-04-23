---
title: Interface ICorDebugStaticFieldSymbol
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 382f3fc9377c25379809badac0bc580c3593cbde
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103890"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="3ec3f-102">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="3ec3f-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="3ec3f-103">Representa as informações de símbolo de depuração de um campo estático.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3ec3f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3ec3f-104">Methods</span></span>  
  
|<span data-ttu-id="3ec3f-105">Método</span><span class="sxs-lookup"><span data-stu-id="3ec3f-105">Method</span></span>|<span data-ttu-id="3ec3f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ec3f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ec3f-107">Método GetAddress</span><span class="sxs-lookup"><span data-stu-id="3ec3f-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="3ec3f-108">Obtém o endereço do campo estático.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="3ec3f-109">Método GetName</span><span class="sxs-lookup"><span data-stu-id="3ec3f-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="3ec3f-110">Obtém o nome do campo estático.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="3ec3f-111">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="3ec3f-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="3ec3f-112">Obtém o tamanho em bytes do campo estático.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ec3f-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="3ec3f-113">Remarks</span></span>  
 <span data-ttu-id="3ec3f-114">O `ICorDebugStaticFieldSymbol` interface é usada para recuperar as informações de símbolo de depuração para um campo estático.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ec3f-115">Essa interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="3ec3f-116">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ec3f-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3ec3f-117">Requirements</span></span>  
 <span data-ttu-id="3ec3f-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ec3f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ec3f-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3ec3f-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ec3f-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ec3f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ec3f-121">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ec3f-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ec3f-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ec3f-122">See also</span></span>

- [<span data-ttu-id="3ec3f-123">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="3ec3f-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="3ec3f-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3ec3f-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3ec3f-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="3ec3f-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
