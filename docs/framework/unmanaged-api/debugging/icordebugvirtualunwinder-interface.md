---
title: Interface ICorDebugVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 065f71e45c2a56dbaa16a45f70958ca3dea80c48
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790834"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="c3233-102">Interface ICorDebugVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="c3233-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="c3233-103">Fornece métodos para ajudar no desenrolamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="c3233-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c3233-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c3233-104">Methods</span></span>  
  
|<span data-ttu-id="c3233-105">Método</span><span class="sxs-lookup"><span data-stu-id="c3233-105">Method</span></span>|<span data-ttu-id="c3233-106">Name</span><span class="sxs-lookup"><span data-stu-id="c3233-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="c3233-107">Método GetContext</span><span class="sxs-lookup"><span data-stu-id="c3233-107">GetContext Method</span></span>](icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="c3233-108">Obtém o contexto atual deste desenrolador.</span><span class="sxs-lookup"><span data-stu-id="c3233-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="c3233-109">Método Next</span><span class="sxs-lookup"><span data-stu-id="c3233-109">Next Method</span></span>](icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="c3233-110">Avança para o contexto do chamador.</span><span class="sxs-lookup"><span data-stu-id="c3233-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3233-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3233-111">Remarks</span></span>  
 <span data-ttu-id="c3233-112">Os membros da interface `ICorDebugVirtualUnwinder` são implementados pelo depurador para ajudar no desenrolamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="c3233-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3233-113">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c3233-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="c3233-114">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="c3233-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3233-115">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="c3233-115">Requirements</span></span>  
 <span data-ttu-id="c3233-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3233-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3233-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3233-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3233-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3233-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3233-119">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3233-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3233-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="c3233-120">See also</span></span>

- [<span data-ttu-id="c3233-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c3233-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c3233-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="c3233-122">Debugging</span></span>](index.md)
