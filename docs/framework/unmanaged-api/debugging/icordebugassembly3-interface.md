---
title: Interface ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66d3024c0bb2c0014cbec2b24deb7b0d5845fe88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627519"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="cefee-102">Interface ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="cefee-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="cefee-103">Estende logicamente a interface ICorDebugAssembly para fornecer suporte para assemblies de contêiner e seus assemblies contidos.</span><span class="sxs-lookup"><span data-stu-id="cefee-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cefee-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="cefee-104">Methods</span></span>  
  
|<span data-ttu-id="cefee-105">Método</span><span class="sxs-lookup"><span data-stu-id="cefee-105">Method</span></span>|<span data-ttu-id="cefee-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="cefee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cefee-107">Método EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="cefee-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="cefee-108">Obtém um enumerador para os assemblies contidos neste assembly.</span><span class="sxs-lookup"><span data-stu-id="cefee-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="cefee-109">Método GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="cefee-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="cefee-110">Retorna o assembly do contêiner desse objeto `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="cefee-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cefee-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="cefee-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cefee-112">A interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cefee-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="cefee-113">A tentativa de chamar `QueryInterface` recuperar um ponteiro de interface retorna `E_NOINTERFACE` para cenários de ICorDebug fora do .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cefee-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cefee-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cefee-114">Requirements</span></span>  
 <span data-ttu-id="cefee-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cefee-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cefee-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cefee-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cefee-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cefee-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cefee-118">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cefee-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cefee-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cefee-119">See also</span></span>
- [<span data-ttu-id="cefee-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="cefee-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cefee-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="cefee-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
