---
title: Interface ICorDebugModuleEnum
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
ms.openlocfilehash: ccb9eff963da1d502d1ed789640f1a108676754c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213342"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="5b672-102">Interface ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="5b672-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="5b672-103">Implementa métodos ICorDebugEnum e enumera matrizes ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="5b672-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5b672-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="5b672-104">Methods</span></span>  
  
|<span data-ttu-id="5b672-105">Método</span><span class="sxs-lookup"><span data-stu-id="5b672-105">Method</span></span>|<span data-ttu-id="5b672-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b672-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5b672-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="5b672-107">Next Method</span></span>](icordebugmoduleenum-next-method.md)|<span data-ttu-id="5b672-108">Obtém o número especificado de `ICorDebugModule` instâncias da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="5b672-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b672-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="5b672-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b672-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="5b672-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b672-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5b672-111">Requirements</span></span>  
 <span data-ttu-id="5b672-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b672-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b672-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b672-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b672-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b672-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b672-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b672-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b672-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="5b672-116">See also</span></span>

- [<span data-ttu-id="5b672-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5b672-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
