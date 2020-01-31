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
ms.openlocfilehash: 22a3f39bc1f9b4e6cad1db4fd0a6480b7c04e8fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792750"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="0d2a6-102">Interface ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="0d2a6-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="0d2a6-103">Fornece métodos que testam relações de quadros pai e filho.</span><span class="sxs-lookup"><span data-stu-id="0d2a6-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0d2a6-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="0d2a6-104">Methods</span></span>  
  
|<span data-ttu-id="0d2a6-105">Método</span><span class="sxs-lookup"><span data-stu-id="0d2a6-105">Method</span></span>|<span data-ttu-id="0d2a6-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d2a6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0d2a6-107">Método IsChild</span><span class="sxs-lookup"><span data-stu-id="0d2a6-107">IsChild Method</span></span>](icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="0d2a6-108">Determina se o quadro atual é um quadro filho.</span><span class="sxs-lookup"><span data-stu-id="0d2a6-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="0d2a6-109">Método IsMatchingParentFrame</span><span class="sxs-lookup"><span data-stu-id="0d2a6-109">IsMatchingParentFrame Method</span></span>](icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="0d2a6-110">Determina se o quadro especificado é o pai do quadro atual.</span><span class="sxs-lookup"><span data-stu-id="0d2a6-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="0d2a6-111">Método GetStackParameterSize</span><span class="sxs-lookup"><span data-stu-id="0d2a6-111">GetStackParameterSize Method</span></span>](icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="0d2a6-112">Retorna o tamanho cumulativo dos parâmetros na pilha em sistemas operacionais x86.</span><span class="sxs-lookup"><span data-stu-id="0d2a6-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d2a6-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d2a6-113">Remarks</span></span>  
 <span data-ttu-id="0d2a6-114">Essa interface estende logicamente a interface "ICorDebugNativeFrame".</span><span class="sxs-lookup"><span data-stu-id="0d2a6-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d2a6-115">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="0d2a6-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d2a6-116">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="0d2a6-116">Requirements</span></span>  
 <span data-ttu-id="0d2a6-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d2a6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d2a6-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d2a6-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d2a6-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d2a6-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d2a6-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d2a6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d2a6-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="0d2a6-121">See also</span></span>

- [<span data-ttu-id="0d2a6-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="0d2a6-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0d2a6-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="0d2a6-123">Debugging</span></span>](index.md)
