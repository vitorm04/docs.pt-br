---
title: Interface ICorDebugStaticFieldSymbol
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 382f3fc9377c25379809badac0bc580c3593cbde
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103890"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="dde9c-102">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="dde9c-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="dde9c-103">Representa as informações de símbolo de depuração de um campo estático.</span><span class="sxs-lookup"><span data-stu-id="dde9c-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dde9c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="dde9c-104">Methods</span></span>  
  
|<span data-ttu-id="dde9c-105">Método</span><span class="sxs-lookup"><span data-stu-id="dde9c-105">Method</span></span>|<span data-ttu-id="dde9c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="dde9c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dde9c-107">Método GetAddress</span><span class="sxs-lookup"><span data-stu-id="dde9c-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="dde9c-108">Obtém o endereço do campo estático.</span><span class="sxs-lookup"><span data-stu-id="dde9c-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="dde9c-109">Método GetName</span><span class="sxs-lookup"><span data-stu-id="dde9c-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="dde9c-110">Obtém o nome do campo estático.</span><span class="sxs-lookup"><span data-stu-id="dde9c-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="dde9c-111">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="dde9c-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="dde9c-112">Obtém o tamanho em bytes do campo estático.</span><span class="sxs-lookup"><span data-stu-id="dde9c-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dde9c-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="dde9c-113">Remarks</span></span>  
 <span data-ttu-id="dde9c-114">O `ICorDebugStaticFieldSymbol` interface é usada para recuperar as informações de símbolo de depuração para um campo estático.</span><span class="sxs-lookup"><span data-stu-id="dde9c-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dde9c-115">Essa interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="dde9c-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="dde9c-116">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="dde9c-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dde9c-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dde9c-117">Requirements</span></span>  
 <span data-ttu-id="dde9c-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dde9c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dde9c-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dde9c-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dde9c-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dde9c-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="dde9c-121">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="dde9c-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dde9c-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dde9c-122">See also</span></span>

- [<span data-ttu-id="dde9c-123">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="dde9c-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="dde9c-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="dde9c-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="dde9c-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="dde9c-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
