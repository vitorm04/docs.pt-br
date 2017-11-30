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
ms.openlocfilehash: b747d2d43fd7ff4dc901dff14277dbce9606497f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="885e0-102">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="885e0-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="885e0-103">Representa as informações de símbolo de depuração para um campo estático.</span><span class="sxs-lookup"><span data-stu-id="885e0-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="885e0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="885e0-104">Methods</span></span>  
  
|<span data-ttu-id="885e0-105">Método</span><span class="sxs-lookup"><span data-stu-id="885e0-105">Method</span></span>|<span data-ttu-id="885e0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="885e0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="885e0-107">Método GetAddress</span><span class="sxs-lookup"><span data-stu-id="885e0-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="885e0-108">Obtém o endereço do campo estático.</span><span class="sxs-lookup"><span data-stu-id="885e0-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="885e0-109">Método GetName</span><span class="sxs-lookup"><span data-stu-id="885e0-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="885e0-110">Obtém o nome do campo estático.</span><span class="sxs-lookup"><span data-stu-id="885e0-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="885e0-111">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="885e0-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="885e0-112">Obtém o tamanho em bytes do campo estático.</span><span class="sxs-lookup"><span data-stu-id="885e0-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="885e0-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="885e0-113">Remarks</span></span>  
 <span data-ttu-id="885e0-114">O `ICorDebugStaticFieldSymbol` interface é usada para recuperar as informações de símbolo de depuração para um campo estático.</span><span class="sxs-lookup"><span data-stu-id="885e0-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="885e0-115">Esta interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="885e0-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="885e0-116">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="885e0-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="885e0-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="885e0-117">Requirements</span></span>  
 <span data-ttu-id="885e0-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="885e0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="885e0-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="885e0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="885e0-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="885e0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="885e0-121">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="885e0-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="885e0-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="885e0-122">See Also</span></span>  
 [<span data-ttu-id="885e0-123">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="885e0-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="885e0-124">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="885e0-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="885e0-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="885e0-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
