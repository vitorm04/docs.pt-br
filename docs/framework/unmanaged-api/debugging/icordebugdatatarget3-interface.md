---
title: Interface ICorDebugDataTarget3
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3b0d67d390931cc92c0b6a1320f66545517cde3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965198"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="e3502-102">Interface ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="e3502-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="e3502-103">Estende logicamente a [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface para fornecer informações sobre os módulos carregados.</span><span class="sxs-lookup"><span data-stu-id="e3502-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="e3502-104">Método</span><span class="sxs-lookup"><span data-stu-id="e3502-104">Method</span></span>  
  
|<span data-ttu-id="e3502-105">Método</span><span class="sxs-lookup"><span data-stu-id="e3502-105">Method</span></span>|<span data-ttu-id="e3502-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3502-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e3502-107">Método GetLoadedModules</span><span class="sxs-lookup"><span data-stu-id="e3502-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="e3502-108">Obtém uma lista dos módulos que foram carregados até o momento.</span><span class="sxs-lookup"><span data-stu-id="e3502-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3502-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3502-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3502-110">Essa interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e3502-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e3502-111">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="e3502-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3502-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3502-112">Requirements</span></span>  
 <span data-ttu-id="e3502-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3502-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3502-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3502-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3502-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3502-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3502-116">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3502-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3502-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3502-117">See also</span></span>

- [<span data-ttu-id="e3502-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e3502-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e3502-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="e3502-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
