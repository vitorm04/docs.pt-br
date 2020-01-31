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
ms.openlocfilehash: be1e1cd0d38ad71de43478af5565bb1ac98a8c0d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778010"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="74111-102">Interface ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="74111-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="74111-103">Fornece um enumerador para uma lista de estruturas [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="74111-103">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="74111-104">Essa interface é uma subclasse da interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="74111-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="74111-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="74111-105">Methods</span></span>  
  
|<span data-ttu-id="74111-106">Método</span><span class="sxs-lookup"><span data-stu-id="74111-106">Method</span></span>|<span data-ttu-id="74111-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="74111-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="74111-108">Método Next</span><span class="sxs-lookup"><span data-stu-id="74111-108">Next Method</span></span>](icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="74111-109">Enumera por meio de uma lista de estruturas [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="74111-109">Enumerates through a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74111-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="74111-110">Remarks</span></span>  
 <span data-ttu-id="74111-111">Cada estrutura de `CorDebugBlockingObject` representa um objeto que está bloqueando um thread.</span><span class="sxs-lookup"><span data-stu-id="74111-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74111-112">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="74111-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74111-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="74111-113">Requirements</span></span>  
 <span data-ttu-id="74111-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74111-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74111-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74111-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74111-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74111-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74111-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74111-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74111-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="74111-118">See also</span></span>

- [<span data-ttu-id="74111-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="74111-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="74111-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="74111-120">Debugging</span></span>](index.md)
