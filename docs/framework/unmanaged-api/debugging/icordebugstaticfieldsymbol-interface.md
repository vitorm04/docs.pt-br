---
title: Interface ICorDebugStaticFieldSymbol
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: b50b9c8435f19e1a77229f01dc85514f5f75c9f5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791797"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="b3a9d-102">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="b3a9d-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="b3a9d-103">Representa as informações de símbolo de depuração de um campo estático.</span><span class="sxs-lookup"><span data-stu-id="b3a9d-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b3a9d-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b3a9d-104">Methods</span></span>  
  
|<span data-ttu-id="b3a9d-105">Método</span><span class="sxs-lookup"><span data-stu-id="b3a9d-105">Method</span></span>|<span data-ttu-id="b3a9d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b3a9d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b3a9d-107">Método GetAddress</span><span class="sxs-lookup"><span data-stu-id="b3a9d-107">GetAddress Method</span></span>](icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="b3a9d-108">Obtém o endereço do campo estático.</span><span class="sxs-lookup"><span data-stu-id="b3a9d-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="b3a9d-109">Método GetName</span><span class="sxs-lookup"><span data-stu-id="b3a9d-109">GetName Method</span></span>](icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="b3a9d-110">Obtém o nome do campo estático.</span><span class="sxs-lookup"><span data-stu-id="b3a9d-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="b3a9d-111">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="b3a9d-111">GetSize Method</span></span>](icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="b3a9d-112">Obtém o tamanho em bytes do campo estático.</span><span class="sxs-lookup"><span data-stu-id="b3a9d-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3a9d-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="b3a9d-113">Remarks</span></span>  
 <span data-ttu-id="b3a9d-114">A interface `ICorDebugStaticFieldSymbol` é usada para recuperar as informações de símbolo de depuração para um campo estático.</span><span class="sxs-lookup"><span data-stu-id="b3a9d-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3a9d-115">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b3a9d-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b3a9d-116">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="b3a9d-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3a9d-117">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b3a9d-117">Requirements</span></span>  
 <span data-ttu-id="b3a9d-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3a9d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3a9d-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3a9d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3a9d-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3a9d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3a9d-121">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3a9d-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a9d-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="b3a9d-122">See also</span></span>

- [<span data-ttu-id="b3a9d-123">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="b3a9d-123">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="b3a9d-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b3a9d-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b3a9d-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="b3a9d-125">Debugging</span></span>](index.md)
