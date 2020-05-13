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
ms.openlocfilehash: cd2a2821128ad9265e8a831f7b02792e6453b1ee
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213784"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="1dfe9-102">Interface ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="1dfe9-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="1dfe9-103">Fornece métodos que testam relações de quadros pai e filho.</span><span class="sxs-lookup"><span data-stu-id="1dfe9-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1dfe9-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="1dfe9-104">Methods</span></span>  
  
|<span data-ttu-id="1dfe9-105">Método</span><span class="sxs-lookup"><span data-stu-id="1dfe9-105">Method</span></span>|<span data-ttu-id="1dfe9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1dfe9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1dfe9-107">Método IsChild</span><span class="sxs-lookup"><span data-stu-id="1dfe9-107">IsChild Method</span></span>](icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="1dfe9-108">Determina se o quadro atual é um quadro filho.</span><span class="sxs-lookup"><span data-stu-id="1dfe9-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="1dfe9-109">Método IsMatchingParentFrame</span><span class="sxs-lookup"><span data-stu-id="1dfe9-109">IsMatchingParentFrame Method</span></span>](icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="1dfe9-110">Determina se o quadro especificado é o pai do quadro atual.</span><span class="sxs-lookup"><span data-stu-id="1dfe9-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="1dfe9-111">Método GetStackParameterSize</span><span class="sxs-lookup"><span data-stu-id="1dfe9-111">GetStackParameterSize Method</span></span>](icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="1dfe9-112">Retorna o tamanho cumulativo dos parâmetros na pilha em sistemas operacionais x86.</span><span class="sxs-lookup"><span data-stu-id="1dfe9-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dfe9-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="1dfe9-113">Remarks</span></span>  
 <span data-ttu-id="1dfe9-114">Essa interface estende logicamente a interface "ICorDebugNativeFrame".</span><span class="sxs-lookup"><span data-stu-id="1dfe9-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1dfe9-115">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="1dfe9-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dfe9-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1dfe9-116">Requirements</span></span>  
 <span data-ttu-id="1dfe9-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dfe9-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dfe9-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1dfe9-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1dfe9-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1dfe9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1dfe9-120">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dfe9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dfe9-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="1dfe9-121">See also</span></span>

- [<span data-ttu-id="1dfe9-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1dfe9-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1dfe9-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="1dfe9-123">Debugging</span></span>](index.md)
