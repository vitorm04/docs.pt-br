---
title: Interface ICorDebugVirtualUnwinder
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 936df5c3d913a2ee5a1648906fb3ece2751d8ef5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="4b493-102">Interface ICorDebugVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="4b493-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="4b493-103">Fornece métodos para ajudar a desenrolamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="4b493-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b493-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="4b493-104">Methods</span></span>  
  
|<span data-ttu-id="4b493-105">Método</span><span class="sxs-lookup"><span data-stu-id="4b493-105">Method</span></span>|<span data-ttu-id="4b493-106">Nome</span><span class="sxs-lookup"><span data-stu-id="4b493-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="4b493-107">Método GetContext</span><span class="sxs-lookup"><span data-stu-id="4b493-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="4b493-108">Obtém o contexto atual deste unwinder.</span><span class="sxs-lookup"><span data-stu-id="4b493-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="4b493-109">Método Next</span><span class="sxs-lookup"><span data-stu-id="4b493-109">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="4b493-110">Avança para o contexto do chamador.</span><span class="sxs-lookup"><span data-stu-id="4b493-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b493-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b493-111">Remarks</span></span>  
 <span data-ttu-id="4b493-112">Os membros de `ICorDebugVirtualUnwinder` interface são implementadas pelo depurador para ajudar o desenrolamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="4b493-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b493-113">Esta interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4b493-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="4b493-114">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="4b493-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b493-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b493-115">Requirements</span></span>  
 <span data-ttu-id="4b493-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b493-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b493-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b493-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b493-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b493-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b493-119">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b493-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b493-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b493-120">See Also</span></span>  
 [<span data-ttu-id="4b493-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4b493-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4b493-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="4b493-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
