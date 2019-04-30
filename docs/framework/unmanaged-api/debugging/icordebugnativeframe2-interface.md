---
title: Interface ICorDebugNativeFrame2
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2
helpviewer_keywords:
- ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc664d308d4db3e97597d785eda159e32255fa54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987838"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="1cb70-102">Interface ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="1cb70-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="1cb70-103">Fornece métodos que testam relações de quadros pai e filho.</span><span class="sxs-lookup"><span data-stu-id="1cb70-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1cb70-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="1cb70-104">Methods</span></span>  
  
|<span data-ttu-id="1cb70-105">Método</span><span class="sxs-lookup"><span data-stu-id="1cb70-105">Method</span></span>|<span data-ttu-id="1cb70-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1cb70-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1cb70-107">Método IsChild</span><span class="sxs-lookup"><span data-stu-id="1cb70-107">IsChild Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="1cb70-108">Determina se o quadro atual é um quadro filho.</span><span class="sxs-lookup"><span data-stu-id="1cb70-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="1cb70-109">Método IsMatchingParentFrame</span><span class="sxs-lookup"><span data-stu-id="1cb70-109">IsMatchingParentFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="1cb70-110">Determina se o quadro especificado é o pai do quadro atual.</span><span class="sxs-lookup"><span data-stu-id="1cb70-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="1cb70-111">Método GetStackParameterSize</span><span class="sxs-lookup"><span data-stu-id="1cb70-111">GetStackParameterSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="1cb70-112">Retorna o tamanho cumulativo dos parâmetros na pilha em sistemas operacionais x86.</span><span class="sxs-lookup"><span data-stu-id="1cb70-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1cb70-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="1cb70-113">Remarks</span></span>  
 <span data-ttu-id="1cb70-114">Essa interface estende logicamente a interface "ICorDebugNativeFrame".</span><span class="sxs-lookup"><span data-stu-id="1cb70-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1cb70-115">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="1cb70-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cb70-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1cb70-116">Requirements</span></span>  
 <span data-ttu-id="1cb70-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cb70-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cb70-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1cb70-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1cb70-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cb70-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cb70-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cb70-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cb70-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cb70-121">See also</span></span>

- [<span data-ttu-id="1cb70-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1cb70-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1cb70-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="1cb70-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
