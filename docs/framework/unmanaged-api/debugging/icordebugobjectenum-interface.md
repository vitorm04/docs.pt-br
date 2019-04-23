---
title: Interface ICorDebugObjectEnum
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum
helpviewer_keywords:
- ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0144539987f14bed83bfc9eab2f5ca26d2a609ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157711"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="63556-102">Interface ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="63556-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="63556-103">Implementa métodos ICorDebugEnum e enumera matrizes de objetos por endereços virtuais (relacionados RVAs).</span><span class="sxs-lookup"><span data-stu-id="63556-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63556-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="63556-104">Methods</span></span>  
  
|<span data-ttu-id="63556-105">Método</span><span class="sxs-lookup"><span data-stu-id="63556-105">Method</span></span>|<span data-ttu-id="63556-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="63556-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63556-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="63556-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="63556-108">Obtém os RVAs do número especificado de objetos de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="63556-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63556-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="63556-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63556-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="63556-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63556-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="63556-111">Requirements</span></span>  
 <span data-ttu-id="63556-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63556-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63556-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63556-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63556-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63556-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63556-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63556-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63556-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63556-116">See also</span></span>

- [<span data-ttu-id="63556-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="63556-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
