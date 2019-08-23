---
title: Interface ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca77360c36ff2cdce7ee47d5c3883dd824c6cef8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959321"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="2c0a4-102">Interface ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="2c0a4-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="2c0a4-103">Estende logicamente a interface ICorDebugAssembly para fornecer suporte para assemblies de contêiner e seus assemblies contidos.</span><span class="sxs-lookup"><span data-stu-id="2c0a4-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c0a4-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2c0a4-104">Methods</span></span>  
  
|<span data-ttu-id="2c0a4-105">Método</span><span class="sxs-lookup"><span data-stu-id="2c0a4-105">Method</span></span>|<span data-ttu-id="2c0a4-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c0a4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c0a4-107">Método EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="2c0a4-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="2c0a4-108">Obtém um enumerador para os assemblies contidos neste assembly.</span><span class="sxs-lookup"><span data-stu-id="2c0a4-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="2c0a4-109">Método GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="2c0a4-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="2c0a4-110">Retorna o assembly do contêiner desse objeto `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="2c0a4-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c0a4-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2c0a4-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c0a4-112">A interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2c0a4-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="2c0a4-113">A tentativa de chamar `QueryInterface` para recuperar um ponteiro de interface `E_NOINTERFACE` retorna para cenários ICorDebug fora do .net Native.</span><span class="sxs-lookup"><span data-stu-id="2c0a4-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c0a4-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2c0a4-114">Requirements</span></span>  
 <span data-ttu-id="2c0a4-115">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c0a4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c0a4-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c0a4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c0a4-117">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c0a4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c0a4-118">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c0a4-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c0a4-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c0a4-119">See also</span></span>

- [<span data-ttu-id="2c0a4-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2c0a4-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2c0a4-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="2c0a4-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
