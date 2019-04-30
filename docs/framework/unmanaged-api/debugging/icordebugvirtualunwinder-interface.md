---
title: Interface ICorDebugVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 639cfc514d2a206f0de72db4b0bac02b53305ae3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946153"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="4201a-102">Interface ICorDebugVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="4201a-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="4201a-103">Fornece métodos para ajudá-lo desenrolamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="4201a-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4201a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="4201a-104">Methods</span></span>  
  
|<span data-ttu-id="4201a-105">Método</span><span class="sxs-lookup"><span data-stu-id="4201a-105">Method</span></span>|<span data-ttu-id="4201a-106">Nome</span><span class="sxs-lookup"><span data-stu-id="4201a-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="4201a-107">Método GetContext</span><span class="sxs-lookup"><span data-stu-id="4201a-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="4201a-108">Obtém o contexto atual deste desenrolador.</span><span class="sxs-lookup"><span data-stu-id="4201a-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="4201a-109">Método Next</span><span class="sxs-lookup"><span data-stu-id="4201a-109">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="4201a-110">Avança para o contexto do chamador.</span><span class="sxs-lookup"><span data-stu-id="4201a-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4201a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="4201a-111">Remarks</span></span>  
 <span data-ttu-id="4201a-112">Os membros do `ICorDebugVirtualUnwinder` interface são implementados pelo depurador para ajudá-lo desenrolamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="4201a-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4201a-113">Essa interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4201a-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="4201a-114">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="4201a-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4201a-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4201a-115">Requirements</span></span>  
 <span data-ttu-id="4201a-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4201a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4201a-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4201a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4201a-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4201a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4201a-119">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4201a-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4201a-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4201a-120">See also</span></span>

- [<span data-ttu-id="4201a-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4201a-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="4201a-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="4201a-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
