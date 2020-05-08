---
title: Interface ICorDebugDataTarget3
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
ms.openlocfilehash: 57ef9b567d57c77c523ca6daefcf80b1d7de66d1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976402"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="2ac3b-102">Interface ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="2ac3b-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="2ac3b-103">Estende logicamente a interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) para fornecer informações sobre os módulos carregados.</span><span class="sxs-lookup"><span data-stu-id="2ac3b-103">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="2ac3b-104">Método</span><span class="sxs-lookup"><span data-stu-id="2ac3b-104">Method</span></span>  
  
|<span data-ttu-id="2ac3b-105">Método</span><span class="sxs-lookup"><span data-stu-id="2ac3b-105">Method</span></span>|<span data-ttu-id="2ac3b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2ac3b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2ac3b-107">Método GetLoadedModules</span><span class="sxs-lookup"><span data-stu-id="2ac3b-107">GetLoadedModules Method</span></span>](icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="2ac3b-108">Obtém uma lista dos módulos que foram carregados até agora.</span><span class="sxs-lookup"><span data-stu-id="2ac3b-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ac3b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2ac3b-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ac3b-110">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2ac3b-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="2ac3b-111">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="2ac3b-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ac3b-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2ac3b-112">Requirements</span></span>  
 <span data-ttu-id="2ac3b-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ac3b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ac3b-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ac3b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ac3b-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ac3b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ac3b-116">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ac3b-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac3b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ac3b-117">See also</span></span>

- [<span data-ttu-id="2ac3b-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2ac3b-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2ac3b-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="2ac3b-119">Debugging</span></span>](index.md)
