---
title: Interface ICorDebugBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
ms.openlocfilehash: 53d8d219a13f2dade16a338efccf0837f8de0158
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784368"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="4a514-102">Interface ICorDebugBreakpoint</span><span class="sxs-lookup"><span data-stu-id="4a514-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="4a514-103">Representa um ponto de interrupção em uma função ou um apontador em um valor.</span><span class="sxs-lookup"><span data-stu-id="4a514-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4a514-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4a514-104">Methods</span></span>  
  
|<span data-ttu-id="4a514-105">Método</span><span class="sxs-lookup"><span data-stu-id="4a514-105">Method</span></span>|<span data-ttu-id="4a514-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a514-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4a514-107">Método Activate</span><span class="sxs-lookup"><span data-stu-id="4a514-107">Activate Method</span></span>](icordebugbreakpoint-activate-method.md)|<span data-ttu-id="4a514-108">Define o estado ativo deste `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="4a514-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="4a514-109">Método IsActive</span><span class="sxs-lookup"><span data-stu-id="4a514-109">IsActive Method</span></span>](icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="4a514-110">Obtém um valor que indica se este `ICorDebugBreakpoint` está ativo.</span><span class="sxs-lookup"><span data-stu-id="4a514-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a514-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a514-111">Remarks</span></span>  
 <span data-ttu-id="4a514-112">Os pontos de interrupção não oferecem suporte direto a expressões condicionais.</span><span class="sxs-lookup"><span data-stu-id="4a514-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="4a514-113">Se essa funcionalidade for desejada, um depurador deverá implementá-la sobre o `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="4a514-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="4a514-114">A interface ICorDebugFunctionBreakpoint estende `ICorDebugBreakpoint` para dar suporte a pontos de interrupção dentro de funções.</span><span class="sxs-lookup"><span data-stu-id="4a514-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a514-115">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="4a514-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a514-116">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="4a514-116">Requirements</span></span>  
 <span data-ttu-id="4a514-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a514-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a514-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a514-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a514-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a514-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a514-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a514-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a514-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="4a514-121">See also</span></span>

- [<span data-ttu-id="4a514-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4a514-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
