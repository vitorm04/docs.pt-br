---
title: Interface ICorDebugThreadEnum
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum
helpviewer_keywords:
- ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: 796de687-7dd4-4b7b-a10b-8bf22dc7779f
topic_type:
- apiref
ms.openlocfilehash: 6de2cb7c1a1423c5bd38a6f2e5d01c39166ab119
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791328"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="5fc50-102">Interface ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="5fc50-102">ICorDebugThreadEnum Interface</span></span>
<span data-ttu-id="5fc50-103">Implementa métodos ICorDebugEnum e enumera matrizes ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="5fc50-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5fc50-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="5fc50-104">Methods</span></span>  
  
|<span data-ttu-id="5fc50-105">Método</span><span class="sxs-lookup"><span data-stu-id="5fc50-105">Method</span></span>|<span data-ttu-id="5fc50-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5fc50-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5fc50-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="5fc50-107">Next Method</span></span>](icordebugthreadenum-next-method.md)|<span data-ttu-id="5fc50-108">Obtém o número especificado de instâncias de `ICorDebugThread` da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="5fc50-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fc50-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="5fc50-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5fc50-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="5fc50-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fc50-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="5fc50-111">Requirements</span></span>  
 <span data-ttu-id="5fc50-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fc50-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fc50-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fc50-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fc50-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fc50-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fc50-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fc50-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fc50-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="5fc50-116">See also</span></span>

- [<span data-ttu-id="5fc50-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5fc50-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
