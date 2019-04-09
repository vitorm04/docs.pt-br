---
title: Interface ICorDebugLoadedModule
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e91dda9cbc5957768e98db2b2a9e1026d94c03e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200747"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="3f068-102">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="3f068-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="3f068-103">Fornece informações sobre um módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="3f068-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f068-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3f068-104">Methods</span></span>  
  
|<span data-ttu-id="3f068-105">Método</span><span class="sxs-lookup"><span data-stu-id="3f068-105">Method</span></span>|<span data-ttu-id="3f068-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3f068-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3f068-107">Método GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="3f068-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="3f068-108">Obtém o endereço base do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="3f068-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="3f068-109">Método GetName</span><span class="sxs-lookup"><span data-stu-id="3f068-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="3f068-110">Obtém o nome do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="3f068-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="3f068-111">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="3f068-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="3f068-112">Obtém o tamanho em bytes do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="3f068-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f068-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="3f068-113">Remarks</span></span>  
 <span data-ttu-id="3f068-114">O `ICorDebugLoadedModule` interface é implementada por um depurador e é usado por interfaces de depuração CLR para obter informações sobre o módulo carregado a partir do depurador.</span><span class="sxs-lookup"><span data-stu-id="3f068-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f068-115">Essa interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3f068-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="3f068-116">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="3f068-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f068-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3f068-117">Requirements</span></span>  
 <span data-ttu-id="3f068-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f068-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f068-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f068-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f068-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f068-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3f068-121">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="3f068-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3f068-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f068-122">See also</span></span>

- [<span data-ttu-id="3f068-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3f068-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3f068-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="3f068-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
