---
title: Interface ICorDebugLoadedModule
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5cdc89ec81d76a3ce7d39a53e097745d6c9822f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="32a62-102">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="32a62-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="32a62-103">Fornece informações sobre um módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="32a62-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="32a62-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="32a62-104">Methods</span></span>  
  
|<span data-ttu-id="32a62-105">Método</span><span class="sxs-lookup"><span data-stu-id="32a62-105">Method</span></span>|<span data-ttu-id="32a62-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="32a62-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="32a62-107">Método GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="32a62-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="32a62-108">Obtém o endereço base do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="32a62-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="32a62-109">Método GetName</span><span class="sxs-lookup"><span data-stu-id="32a62-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="32a62-110">Obtém o nome do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="32a62-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="32a62-111">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="32a62-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="32a62-112">Obtém o tamanho em bytes do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="32a62-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32a62-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="32a62-113">Remarks</span></span>  
 <span data-ttu-id="32a62-114">O `ICorDebugLoadedModule` interface é implementada por um depurador e é usado pelo CLR interfaces de depuração para obter informações sobre o módulo carregado do depurador.</span><span class="sxs-lookup"><span data-stu-id="32a62-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32a62-115">Esta interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="32a62-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="32a62-116">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="32a62-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32a62-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="32a62-117">Requirements</span></span>  
 <span data-ttu-id="32a62-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32a62-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32a62-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32a62-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32a62-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32a62-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32a62-121">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32a62-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a62-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32a62-122">See Also</span></span>  
 [<span data-ttu-id="32a62-123">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="32a62-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="32a62-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="32a62-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
