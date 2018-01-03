---
title: Interface ICorDebugAssembly3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e581b4256da2ecc19a8b97520e0e70fef972b549
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="6323c-102">Interface ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="6323c-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="6323c-103">Logicamente estende a interface ICorDebugAssembly para fornecer suporte para assemblies de contêiner e seus assemblies independentes.</span><span class="sxs-lookup"><span data-stu-id="6323c-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6323c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6323c-104">Methods</span></span>  
  
|<span data-ttu-id="6323c-105">Método</span><span class="sxs-lookup"><span data-stu-id="6323c-105">Method</span></span>|<span data-ttu-id="6323c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6323c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6323c-107">Método EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="6323c-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="6323c-108">Obtém um enumerador para os assemblies contidos neste assembly.</span><span class="sxs-lookup"><span data-stu-id="6323c-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="6323c-109">Método GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="6323c-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="6323c-110">Retorna o assembly do contêiner desse objeto `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="6323c-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6323c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="6323c-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6323c-112">A interface está disponível com o .NET Native somente.</span><span class="sxs-lookup"><span data-stu-id="6323c-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="6323c-113">Tentando chamar `QueryInterface` recuperar um ponteiro de interface retorna `E_NOINTERFACE` para cenários de ICorDebug fora do .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6323c-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6323c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6323c-114">Requirements</span></span>  
 <span data-ttu-id="6323c-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6323c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6323c-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6323c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6323c-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6323c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6323c-118">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6323c-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6323c-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6323c-119">See Also</span></span>  
 [<span data-ttu-id="6323c-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6323c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6323c-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="6323c-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
