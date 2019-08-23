---
title: Interface ICorDebugDataTarget3
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee94e25201dee4999fd5acb2be44a80454e9efbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911410"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="a6508-102">Interface ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="a6508-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="a6508-103">Estende logicamente a interface [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) para fornecer informações sobre os módulos carregados.</span><span class="sxs-lookup"><span data-stu-id="a6508-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="a6508-104">Método</span><span class="sxs-lookup"><span data-stu-id="a6508-104">Method</span></span>  
  
|<span data-ttu-id="a6508-105">Método</span><span class="sxs-lookup"><span data-stu-id="a6508-105">Method</span></span>|<span data-ttu-id="a6508-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6508-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a6508-107">Método GetLoadedModules</span><span class="sxs-lookup"><span data-stu-id="a6508-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="a6508-108">Obtém uma lista dos módulos que foram carregados até agora.</span><span class="sxs-lookup"><span data-stu-id="a6508-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6508-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a6508-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6508-110">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a6508-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="a6508-111">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="a6508-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6508-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a6508-112">Requirements</span></span>  
 <span data-ttu-id="a6508-113">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6508-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6508-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6508-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6508-115">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6508-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6508-116">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6508-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6508-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6508-117">See also</span></span>

- [<span data-ttu-id="a6508-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a6508-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a6508-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="a6508-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
