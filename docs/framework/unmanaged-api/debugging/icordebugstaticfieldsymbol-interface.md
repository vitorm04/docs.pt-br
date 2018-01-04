---
title: Interface ICorDebugStaticFieldSymbol
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a25e19bf43d852670bc5f4f491fb25707395e04a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="2ead9-102">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="2ead9-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="2ead9-103">Representa as informações de símbolo de depuração para um campo estático.</span><span class="sxs-lookup"><span data-stu-id="2ead9-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2ead9-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2ead9-104">Methods</span></span>  
  
|<span data-ttu-id="2ead9-105">Método</span><span class="sxs-lookup"><span data-stu-id="2ead9-105">Method</span></span>|<span data-ttu-id="2ead9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2ead9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2ead9-107">Método GetAddress</span><span class="sxs-lookup"><span data-stu-id="2ead9-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="2ead9-108">Obtém o endereço do campo estático.</span><span class="sxs-lookup"><span data-stu-id="2ead9-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="2ead9-109">Método GetName</span><span class="sxs-lookup"><span data-stu-id="2ead9-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="2ead9-110">Obtém o nome do campo estático.</span><span class="sxs-lookup"><span data-stu-id="2ead9-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="2ead9-111">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="2ead9-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="2ead9-112">Obtém o tamanho em bytes do campo estático.</span><span class="sxs-lookup"><span data-stu-id="2ead9-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ead9-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="2ead9-113">Remarks</span></span>  
 <span data-ttu-id="2ead9-114">O `ICorDebugStaticFieldSymbol` interface é usada para recuperar as informações de símbolo de depuração para um campo estático.</span><span class="sxs-lookup"><span data-stu-id="2ead9-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ead9-115">Esta interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2ead9-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="2ead9-116">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="2ead9-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ead9-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2ead9-117">Requirements</span></span>  
 <span data-ttu-id="2ead9-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ead9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ead9-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ead9-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ead9-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ead9-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ead9-121">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ead9-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ead9-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ead9-122">See Also</span></span>  
 [<span data-ttu-id="2ead9-123">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="2ead9-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="2ead9-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2ead9-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2ead9-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="2ead9-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
