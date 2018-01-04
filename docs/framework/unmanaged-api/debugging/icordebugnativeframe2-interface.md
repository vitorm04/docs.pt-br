---
title: Interface ICorDebugNativeFrame2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2
helpviewer_keywords: ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f501d49f007e22c6f7db0e759ee19b40f87b4b33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="f8c20-102">Interface ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="f8c20-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="f8c20-103">Fornece métodos que testam relações de quadros pai e filho.</span><span class="sxs-lookup"><span data-stu-id="f8c20-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8c20-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="f8c20-104">Methods</span></span>  
  
|<span data-ttu-id="f8c20-105">Método</span><span class="sxs-lookup"><span data-stu-id="f8c20-105">Method</span></span>|<span data-ttu-id="f8c20-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8c20-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8c20-107">Método IsChild</span><span class="sxs-lookup"><span data-stu-id="f8c20-107">IsChild Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="f8c20-108">Determina se o quadro atual é um quadro filho.</span><span class="sxs-lookup"><span data-stu-id="f8c20-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="f8c20-109">Método IsMatchingParentFrame</span><span class="sxs-lookup"><span data-stu-id="f8c20-109">IsMatchingParentFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="f8c20-110">Determina se o intervalo especificado é o pai do quadro atual.</span><span class="sxs-lookup"><span data-stu-id="f8c20-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="f8c20-111">Método GetStackParameterSize</span><span class="sxs-lookup"><span data-stu-id="f8c20-111">GetStackParameterSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="f8c20-112">Retorna o tamanho cumulativo dos parâmetros na pilha em sistemas operacionais x86.</span><span class="sxs-lookup"><span data-stu-id="f8c20-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8c20-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="f8c20-113">Remarks</span></span>  
 <span data-ttu-id="f8c20-114">Essa interface logicamente estende a interface de "ICorDebugNativeFrame".</span><span class="sxs-lookup"><span data-stu-id="f8c20-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8c20-115">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="f8c20-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8c20-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f8c20-116">Requirements</span></span>  
 <span data-ttu-id="f8c20-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8c20-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8c20-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8c20-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8c20-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8c20-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8c20-120">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8c20-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8c20-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8c20-121">See Also</span></span>  
    
 [<span data-ttu-id="f8c20-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f8c20-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f8c20-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="f8c20-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
