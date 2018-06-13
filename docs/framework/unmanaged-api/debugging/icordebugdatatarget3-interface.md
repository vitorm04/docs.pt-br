---
title: Interface ICorDebugDataTarget3
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6392d1040c9d76944f79dc3a39213ae6c2191bef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415562"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="05b0d-102">Interface ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="05b0d-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="05b0d-103">Logicamente estende o [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface para fornecer informações sobre os módulos carregados.</span><span class="sxs-lookup"><span data-stu-id="05b0d-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="05b0d-104">Método</span><span class="sxs-lookup"><span data-stu-id="05b0d-104">Method</span></span>  
  
|<span data-ttu-id="05b0d-105">Método</span><span class="sxs-lookup"><span data-stu-id="05b0d-105">Method</span></span>|<span data-ttu-id="05b0d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="05b0d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05b0d-107">Método GetLoadedModules</span><span class="sxs-lookup"><span data-stu-id="05b0d-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="05b0d-108">Obtém uma lista dos módulos que foram carregados até o momento.</span><span class="sxs-lookup"><span data-stu-id="05b0d-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05b0d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="05b0d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05b0d-110">Esta interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="05b0d-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="05b0d-111">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="05b0d-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05b0d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="05b0d-112">Requirements</span></span>  
 <span data-ttu-id="05b0d-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05b0d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05b0d-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05b0d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05b0d-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05b0d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05b0d-116">**Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05b0d-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05b0d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05b0d-117">See Also</span></span>  
 [<span data-ttu-id="05b0d-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="05b0d-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="05b0d-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="05b0d-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
