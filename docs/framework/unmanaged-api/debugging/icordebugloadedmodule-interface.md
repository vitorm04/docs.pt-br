---
title: Interface ICorDebugLoadedModule
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: d9b8245d8c37867971aa48ed3befb9cf22bd5b04
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210157"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="52639-102">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="52639-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="52639-103">Fornece informações sobre um módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="52639-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="52639-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="52639-104">Methods</span></span>  
  
|<span data-ttu-id="52639-105">Método</span><span class="sxs-lookup"><span data-stu-id="52639-105">Method</span></span>|<span data-ttu-id="52639-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="52639-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="52639-107">Método GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="52639-107">GetBaseAddress Method</span></span>](icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="52639-108">Obtém o endereço base do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="52639-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="52639-109">Método GetName</span><span class="sxs-lookup"><span data-stu-id="52639-109">GetName Method</span></span>](icordebugloadedmodule-getname-method.md)|<span data-ttu-id="52639-110">Obtém o nome do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="52639-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="52639-111">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="52639-111">GetSize Method</span></span>](icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="52639-112">Obtém o tamanho em bytes do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="52639-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52639-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="52639-113">Remarks</span></span>  
 <span data-ttu-id="52639-114">A `ICorDebugLoadedModule` interface é implementada por um depurador e é usada pelas interfaces de depuração CLR para obter informações sobre o módulo carregado do depurador.</span><span class="sxs-lookup"><span data-stu-id="52639-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52639-115">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="52639-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="52639-116">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="52639-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52639-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="52639-117">Requirements</span></span>  
 <span data-ttu-id="52639-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52639-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52639-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52639-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52639-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52639-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52639-121">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52639-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52639-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="52639-122">See also</span></span>

- [<span data-ttu-id="52639-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="52639-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="52639-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="52639-124">Debugging</span></span>](index.md)
