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
ms.openlocfilehash: dc556dfb59e999ed9b7fc5f35c603dc26c35f314
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378715"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="a8145-102">Interface ICorDebugThread3</span><span class="sxs-lookup"><span data-stu-id="a8145-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="a8145-103">Fornece o ponto de entrada para o [ICorDebugStackWalk](icordebugstackwalk-interface.md) e as interfaces correspondentes.</span><span class="sxs-lookup"><span data-stu-id="a8145-103">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a8145-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a8145-104">Methods</span></span>  
  
|<span data-ttu-id="a8145-105">Método</span><span class="sxs-lookup"><span data-stu-id="a8145-105">Method</span></span>|<span data-ttu-id="a8145-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8145-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a8145-107">Método CreateStackWalk</span><span class="sxs-lookup"><span data-stu-id="a8145-107">CreateStackWalk Method</span></span>](icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="a8145-108">Cria um objeto [ICorDebugStackWalk](icordebugstackwalk-interface.md) para o thread cuja pilha você deseja desenrolar.</span><span class="sxs-lookup"><span data-stu-id="a8145-108">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="a8145-109">Método GetActiveInternalFrames</span><span class="sxs-lookup"><span data-stu-id="a8145-109">GetActiveInternalFrames Method</span></span>](icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="a8145-110">Retorna uma matriz de quadros internos (objetos[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) ) na pilha.</span><span class="sxs-lookup"><span data-stu-id="a8145-110">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8145-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8145-111">Remarks</span></span>  
 <span data-ttu-id="a8145-112">`ICorDebugThread3`é uma extensão lógica para a interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="a8145-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8145-113">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="a8145-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8145-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8145-114">Requirements</span></span>  
 <span data-ttu-id="a8145-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8145-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8145-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8145-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8145-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8145-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8145-118">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8145-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8145-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="a8145-119">See also</span></span>

- [<span data-ttu-id="a8145-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a8145-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a8145-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="a8145-121">Debugging</span></span>](index.md)
