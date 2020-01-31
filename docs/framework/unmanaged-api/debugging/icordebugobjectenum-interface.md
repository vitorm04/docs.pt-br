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
ms.openlocfilehash: 0526c050bcf1316eccf2c756a404fbb971e6d7d0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792735"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="3f0d5-102">Interface ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="3f0d5-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="3f0d5-103">Implementa métodos ICorDebugEnum e enumera matrizes de objetos por seus endereços virtuais relativos (RVAs).</span><span class="sxs-lookup"><span data-stu-id="3f0d5-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f0d5-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="3f0d5-104">Methods</span></span>  
  
|<span data-ttu-id="3f0d5-105">Método</span><span class="sxs-lookup"><span data-stu-id="3f0d5-105">Method</span></span>|<span data-ttu-id="3f0d5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3f0d5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3f0d5-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="3f0d5-107">Next Method</span></span>](icordebugobjectenum-next-method.md)|<span data-ttu-id="3f0d5-108">Obtém o RVAs do número especificado de objetos da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="3f0d5-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f0d5-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="3f0d5-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f0d5-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="3f0d5-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f0d5-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="3f0d5-111">Requirements</span></span>  
 <span data-ttu-id="3f0d5-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f0d5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f0d5-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f0d5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f0d5-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f0d5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f0d5-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f0d5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f0d5-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="3f0d5-116">See also</span></span>

- [<span data-ttu-id="3f0d5-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3f0d5-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
