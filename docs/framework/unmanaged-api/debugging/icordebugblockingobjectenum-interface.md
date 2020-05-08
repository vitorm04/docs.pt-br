---
title: Interface ICorDebugBlockingObjectEnum
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum
helpviewer_keywords:
- ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type:
- apiref
ms.openlocfilehash: 8be4332da77c3fbf4229a3fbeb9ba835a7a13eee
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894799"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="236e8-102">Interface ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="236e8-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="236e8-103">Fornece um enumerador para uma lista de estruturas [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="236e8-103">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="236e8-104">Essa interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="236e8-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="236e8-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="236e8-105">Methods</span></span>  
  
|<span data-ttu-id="236e8-106">Método</span><span class="sxs-lookup"><span data-stu-id="236e8-106">Method</span></span>|<span data-ttu-id="236e8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="236e8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="236e8-108">Método Next</span><span class="sxs-lookup"><span data-stu-id="236e8-108">Next Method</span></span>](icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="236e8-109">Enumera por meio de uma lista de estruturas [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="236e8-109">Enumerates through a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="236e8-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="236e8-110">Remarks</span></span>  
 <span data-ttu-id="236e8-111">Cada `CorDebugBlockingObject` estrutura representa um objeto que está bloqueando um thread.</span><span class="sxs-lookup"><span data-stu-id="236e8-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="236e8-112">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="236e8-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="236e8-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="236e8-113">Requirements</span></span>  
 <span data-ttu-id="236e8-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="236e8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="236e8-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="236e8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="236e8-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="236e8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="236e8-117">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="236e8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="236e8-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="236e8-118">See also</span></span>

- [<span data-ttu-id="236e8-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="236e8-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="236e8-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="236e8-120">Debugging</span></span>](index.md)
