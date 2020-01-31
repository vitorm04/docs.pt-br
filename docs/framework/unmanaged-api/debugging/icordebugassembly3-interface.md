---
title: Interface ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: deb300ced2ff7a116bd443c9a7b10dcc0b7955ac
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784527"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="d3324-102">Interface ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="d3324-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="d3324-103">Estende logicamente a interface ICorDebugAssembly para oferecer suporte a assemblies de contêiner e seus assemblies contidos.</span><span class="sxs-lookup"><span data-stu-id="d3324-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3324-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d3324-104">Methods</span></span>  
  
|<span data-ttu-id="d3324-105">Método</span><span class="sxs-lookup"><span data-stu-id="d3324-105">Method</span></span>|<span data-ttu-id="d3324-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3324-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3324-107">Método EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="d3324-107">EnumerateContainedAssemblies Method</span></span>](icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="d3324-108">Obtém um enumerador para os assemblies contidos neste assembly.</span><span class="sxs-lookup"><span data-stu-id="d3324-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="d3324-109">Método GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="d3324-109">GetContainerAssembly Method</span></span>](icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="d3324-110">Retorna o assembly do contêiner desse objeto `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="d3324-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3324-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d3324-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3324-112">A interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d3324-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="d3324-113">A tentativa de chamar `QueryInterface` para recuperar um ponteiro de interface retorna `E_NOINTERFACE` para cenários ICorDebug fora do .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d3324-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3324-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="d3324-114">Requirements</span></span>  
 <span data-ttu-id="d3324-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3324-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3324-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3324-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3324-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3324-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3324-118">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3324-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3324-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="d3324-119">See also</span></span>

- [<span data-ttu-id="d3324-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d3324-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d3324-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="d3324-121">Debugging</span></span>](index.md)
