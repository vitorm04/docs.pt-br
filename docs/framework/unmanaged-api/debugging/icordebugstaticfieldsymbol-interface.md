---
title: Interface ICorDebugStaticFieldSymbol
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: 0891df1fc0528ff485605b2c4168fcff0adff990
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131702"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="fb3c7-102">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="fb3c7-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="fb3c7-103">Representa as informações de símbolo de depuração de um campo estático.</span><span class="sxs-lookup"><span data-stu-id="fb3c7-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fb3c7-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="fb3c7-104">Methods</span></span>  
  
|<span data-ttu-id="fb3c7-105">Método</span><span class="sxs-lookup"><span data-stu-id="fb3c7-105">Method</span></span>|<span data-ttu-id="fb3c7-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb3c7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fb3c7-107">Método GetAddress</span><span class="sxs-lookup"><span data-stu-id="fb3c7-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="fb3c7-108">Obtém o endereço do campo estático.</span><span class="sxs-lookup"><span data-stu-id="fb3c7-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="fb3c7-109">Método GetName</span><span class="sxs-lookup"><span data-stu-id="fb3c7-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="fb3c7-110">Obtém o nome do campo estático.</span><span class="sxs-lookup"><span data-stu-id="fb3c7-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="fb3c7-111">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="fb3c7-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="fb3c7-112">Obtém o tamanho em bytes do campo estático.</span><span class="sxs-lookup"><span data-stu-id="fb3c7-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb3c7-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb3c7-113">Remarks</span></span>  
 <span data-ttu-id="fb3c7-114">A interface `ICorDebugStaticFieldSymbol` é usada para recuperar as informações de símbolo de depuração para um campo estático.</span><span class="sxs-lookup"><span data-stu-id="fb3c7-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb3c7-115">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fb3c7-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="fb3c7-116">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="fb3c7-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb3c7-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb3c7-117">Requirements</span></span>  
 <span data-ttu-id="fb3c7-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb3c7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb3c7-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb3c7-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb3c7-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb3c7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb3c7-121">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb3c7-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb3c7-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb3c7-122">See also</span></span>

- [<span data-ttu-id="fb3c7-123">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="fb3c7-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="fb3c7-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fb3c7-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="fb3c7-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="fb3c7-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
