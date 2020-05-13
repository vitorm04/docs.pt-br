---
title: Interface ICorDebugInternalFrame2
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2
helpviewer_keywords:
- ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type:
- apiref
ms.openlocfilehash: ce3ca4745727a1738fdc1a526480d70ffc55ccf8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209897"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="0ca1c-102">Interface ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="0ca1c-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="0ca1c-103">Fornece informações sobre os quadros internos, incluindo o endereço de pilha e a posição em relação a objetos ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="0ca1c-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ca1c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="0ca1c-104">Methods</span></span>  
  
|<span data-ttu-id="0ca1c-105">Método</span><span class="sxs-lookup"><span data-stu-id="0ca1c-105">Method</span></span>|<span data-ttu-id="0ca1c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ca1c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ca1c-107">Método GetFrameAddress</span><span class="sxs-lookup"><span data-stu-id="0ca1c-107">GetFrameAddress Method</span></span>](icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="0ca1c-108">Retorna o endereço da pilha do quadro interno.</span><span class="sxs-lookup"><span data-stu-id="0ca1c-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="0ca1c-109">Método IsCloserToLeaf</span><span class="sxs-lookup"><span data-stu-id="0ca1c-109">IsCloserToLeaf Method</span></span>](icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="0ca1c-110">Verifica se o `this` quadro interno está mais próximo da folha do que o objeto ICorDebugFrame especificado.</span><span class="sxs-lookup"><span data-stu-id="0ca1c-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ca1c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="0ca1c-111">Remarks</span></span>  
 <span data-ttu-id="0ca1c-112">Essa interface estende a interface ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="0ca1c-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ca1c-113">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="0ca1c-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ca1c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0ca1c-114">Requirements</span></span>  
 <span data-ttu-id="0ca1c-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ca1c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ca1c-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ca1c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ca1c-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ca1c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ca1c-118">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ca1c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ca1c-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="0ca1c-119">See also</span></span>

- [<span data-ttu-id="0ca1c-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="0ca1c-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0ca1c-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="0ca1c-121">Debugging</span></span>](index.md)
