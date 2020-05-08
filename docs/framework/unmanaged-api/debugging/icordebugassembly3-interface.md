---
title: Interface ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 67707092c80b0e07aa284336c426aba09ff991af
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894820"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="55d95-102">Interface ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="55d95-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="55d95-103">Estende logicamente a interface ICorDebugAssembly para oferecer suporte a assemblies de contêiner e seus assemblies contidos.</span><span class="sxs-lookup"><span data-stu-id="55d95-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="55d95-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="55d95-104">Methods</span></span>  
  
|<span data-ttu-id="55d95-105">Método</span><span class="sxs-lookup"><span data-stu-id="55d95-105">Method</span></span>|<span data-ttu-id="55d95-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="55d95-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="55d95-107">Método EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="55d95-107">EnumerateContainedAssemblies Method</span></span>](icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="55d95-108">Obtém um enumerador para os assemblies contidos neste assembly.</span><span class="sxs-lookup"><span data-stu-id="55d95-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="55d95-109">Método GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="55d95-109">GetContainerAssembly Method</span></span>](icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="55d95-110">Retorna o assembly do contêiner desse objeto `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="55d95-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55d95-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="55d95-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55d95-112">A interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="55d95-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="55d95-113">A tentativa de chamar `QueryInterface` para recuperar um ponteiro de interface `E_NOINTERFACE` retorna para cenários ICorDebug fora do .net Native.</span><span class="sxs-lookup"><span data-stu-id="55d95-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55d95-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="55d95-114">Requirements</span></span>  
 <span data-ttu-id="55d95-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55d95-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55d95-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55d95-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55d95-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55d95-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55d95-118">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55d95-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55d95-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55d95-119">See also</span></span>

- [<span data-ttu-id="55d95-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="55d95-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="55d95-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="55d95-121">Debugging</span></span>](index.md)
