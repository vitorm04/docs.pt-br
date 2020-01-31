---
title: Interface ICorDebugThread3
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
ms.openlocfilehash: 19bd869aec7e4d046890d2314f5142753ba0b112
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791387"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="c0f85-102">Interface ICorDebugThread3</span><span class="sxs-lookup"><span data-stu-id="c0f85-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="c0f85-103">Fornece o ponto de entrada para o [ICorDebugStackWalk](icordebugstackwalk-interface.md) e as interfaces correspondentes.</span><span class="sxs-lookup"><span data-stu-id="c0f85-103">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c0f85-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c0f85-104">Methods</span></span>  
  
|<span data-ttu-id="c0f85-105">Método</span><span class="sxs-lookup"><span data-stu-id="c0f85-105">Method</span></span>|<span data-ttu-id="c0f85-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0f85-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c0f85-107">Método CreateStackWalk</span><span class="sxs-lookup"><span data-stu-id="c0f85-107">CreateStackWalk Method</span></span>](icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="c0f85-108">Cria um objeto [ICorDebugStackWalk](icordebugstackwalk-interface.md) para o thread cuja pilha você deseja desenrolar.</span><span class="sxs-lookup"><span data-stu-id="c0f85-108">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="c0f85-109">Método GetActiveInternalFrames</span><span class="sxs-lookup"><span data-stu-id="c0f85-109">GetActiveInternalFrames Method</span></span>](icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="c0f85-110">Retorna uma matriz de quadros internos (objetos[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) ) na pilha.</span><span class="sxs-lookup"><span data-stu-id="c0f85-110">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0f85-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="c0f85-111">Remarks</span></span>  
 <span data-ttu-id="c0f85-112">`ICorDebugThread3` é uma extensão lógica para a interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="c0f85-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0f85-113">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="c0f85-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0f85-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="c0f85-114">Requirements</span></span>  
 <span data-ttu-id="c0f85-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0f85-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0f85-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0f85-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0f85-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0f85-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0f85-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0f85-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0f85-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="c0f85-119">See also</span></span>

- [<span data-ttu-id="c0f85-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c0f85-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c0f85-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="c0f85-121">Debugging</span></span>](index.md)
