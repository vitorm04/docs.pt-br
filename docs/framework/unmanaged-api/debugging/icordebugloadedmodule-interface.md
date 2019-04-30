---
title: Interface ICorDebugLoadedModule
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e91dda9cbc5957768e98db2b2a9e1026d94c03e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946276"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="e4aa5-102">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="e4aa5-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="e4aa5-103">Fornece informações sobre um módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="e4aa5-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4aa5-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="e4aa5-104">Methods</span></span>  
  
|<span data-ttu-id="e4aa5-105">Método</span><span class="sxs-lookup"><span data-stu-id="e4aa5-105">Method</span></span>|<span data-ttu-id="e4aa5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4aa5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4aa5-107">Método GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="e4aa5-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="e4aa5-108">Obtém o endereço base do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="e4aa5-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="e4aa5-109">Método GetName</span><span class="sxs-lookup"><span data-stu-id="e4aa5-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="e4aa5-110">Obtém o nome do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="e4aa5-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="e4aa5-111">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="e4aa5-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="e4aa5-112">Obtém o tamanho em bytes do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="e4aa5-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4aa5-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4aa5-113">Remarks</span></span>  
 <span data-ttu-id="e4aa5-114">O `ICorDebugLoadedModule` interface é implementada por um depurador e é usado por interfaces de depuração CLR para obter informações sobre o módulo carregado a partir do depurador.</span><span class="sxs-lookup"><span data-stu-id="e4aa5-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4aa5-115">Essa interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e4aa5-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e4aa5-116">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="e4aa5-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4aa5-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4aa5-117">Requirements</span></span>  
 <span data-ttu-id="e4aa5-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4aa5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4aa5-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4aa5-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4aa5-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4aa5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4aa5-121">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4aa5-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4aa5-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4aa5-122">See also</span></span>

- [<span data-ttu-id="e4aa5-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e4aa5-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e4aa5-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="e4aa5-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
