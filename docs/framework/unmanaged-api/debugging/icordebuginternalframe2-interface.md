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
ms.openlocfilehash: 9e333d71505a055cfe27df2c79a102c939bafc9d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788473"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="7c1a5-102">Interface ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="7c1a5-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="7c1a5-103">Fornece informações sobre os quadros internos, incluindo o endereço de pilha e a posição em relação a objetos ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="7c1a5-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c1a5-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7c1a5-104">Methods</span></span>  
  
|<span data-ttu-id="7c1a5-105">Método</span><span class="sxs-lookup"><span data-stu-id="7c1a5-105">Method</span></span>|<span data-ttu-id="7c1a5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c1a5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c1a5-107">Método GetFrameAddress</span><span class="sxs-lookup"><span data-stu-id="7c1a5-107">GetFrameAddress Method</span></span>](icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="7c1a5-108">Retorna o endereço da pilha do quadro interno.</span><span class="sxs-lookup"><span data-stu-id="7c1a5-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="7c1a5-109">Método IsCloserToLeaf</span><span class="sxs-lookup"><span data-stu-id="7c1a5-109">IsCloserToLeaf Method</span></span>](icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="7c1a5-110">Verifica se o quadro interno `this` está mais próximo da folha do que o objeto ICorDebugFrame especificado.</span><span class="sxs-lookup"><span data-stu-id="7c1a5-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c1a5-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c1a5-111">Remarks</span></span>  
 <span data-ttu-id="7c1a5-112">Essa interface estende a interface ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="7c1a5-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7c1a5-113">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="7c1a5-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c1a5-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="7c1a5-114">Requirements</span></span>  
 <span data-ttu-id="7c1a5-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c1a5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c1a5-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c1a5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c1a5-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c1a5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c1a5-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c1a5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c1a5-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="7c1a5-119">See also</span></span>

- [<span data-ttu-id="7c1a5-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7c1a5-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7c1a5-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="7c1a5-121">Debugging</span></span>](index.md)
