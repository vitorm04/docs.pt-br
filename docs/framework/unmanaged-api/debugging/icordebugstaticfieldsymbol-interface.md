---
title: Interface ICorDebugStaticFieldSymbol
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cde5f60764772ece8528eb67a82836c0ae9e651b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="19bbb-102">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="19bbb-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="19bbb-103">Representa as informações de símbolo de depuração para um campo estático.</span><span class="sxs-lookup"><span data-stu-id="19bbb-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19bbb-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="19bbb-104">Methods</span></span>  
  
|<span data-ttu-id="19bbb-105">Método</span><span class="sxs-lookup"><span data-stu-id="19bbb-105">Method</span></span>|<span data-ttu-id="19bbb-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="19bbb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19bbb-107">Método GetAddress</span><span class="sxs-lookup"><span data-stu-id="19bbb-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="19bbb-108">Obtém o endereço do campo estático.</span><span class="sxs-lookup"><span data-stu-id="19bbb-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="19bbb-109">Método GetName</span><span class="sxs-lookup"><span data-stu-id="19bbb-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="19bbb-110">Obtém o nome do campo estático.</span><span class="sxs-lookup"><span data-stu-id="19bbb-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="19bbb-111">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="19bbb-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="19bbb-112">Obtém o tamanho em bytes do campo estático.</span><span class="sxs-lookup"><span data-stu-id="19bbb-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19bbb-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="19bbb-113">Remarks</span></span>  
 <span data-ttu-id="19bbb-114">O `ICorDebugStaticFieldSymbol` interface é usada para recuperar as informações de símbolo de depuração para um campo estático.</span><span class="sxs-lookup"><span data-stu-id="19bbb-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19bbb-115">Esta interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="19bbb-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="19bbb-116">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="19bbb-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19bbb-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="19bbb-117">Requirements</span></span>  
 <span data-ttu-id="19bbb-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19bbb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19bbb-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19bbb-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19bbb-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19bbb-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19bbb-121">**Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19bbb-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19bbb-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19bbb-122">See Also</span></span>  
 [<span data-ttu-id="19bbb-123">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="19bbb-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="19bbb-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="19bbb-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="19bbb-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="19bbb-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
