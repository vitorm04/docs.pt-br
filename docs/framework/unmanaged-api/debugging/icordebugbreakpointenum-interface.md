---
title: Interface ICorDebugBreakpointEnum
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum
helpviewer_keywords:
- ICorDebugBreakpointEnum interface [.NET Framework debugging]
ms.assetid: 4c6f4f6e-52cc-402e-881b-7b8526544c90
topic_type:
- apiref
ms.openlocfilehash: 22ae1d24040a8ee5000e0ff2fbeb2b45e08050df
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784352"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="79bcf-102">Interface ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="79bcf-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="79bcf-103">Implementa métodos ICorDebugEnum e enumera matrizes ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="79bcf-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79bcf-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="79bcf-104">Methods</span></span>  
  
|<span data-ttu-id="79bcf-105">Método</span><span class="sxs-lookup"><span data-stu-id="79bcf-105">Method</span></span>|<span data-ttu-id="79bcf-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="79bcf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="79bcf-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="79bcf-107">Next Method</span></span>](icordebugbreakpointenum-next-method.md)|<span data-ttu-id="79bcf-108">Obtém o número especificado de instâncias de `ICorDebugBreakpoint` da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="79bcf-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79bcf-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="79bcf-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79bcf-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="79bcf-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79bcf-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="79bcf-111">Requirements</span></span>  
 <span data-ttu-id="79bcf-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79bcf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79bcf-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79bcf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79bcf-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79bcf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79bcf-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79bcf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79bcf-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="79bcf-116">See also</span></span>

- [<span data-ttu-id="79bcf-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="79bcf-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
