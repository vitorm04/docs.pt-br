---
title: Interface ICorDebugAppDomainEnum
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum
helpviewer_keywords:
- ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: e9226e6e-ca2c-428e-bb38-0c099210f507
topic_type:
- apiref
ms.openlocfilehash: 38603fb53b9cd6548595437b05c1e99ef208d940
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895092"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="be5cf-102">Interface ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="be5cf-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="be5cf-103">Fornece o `Next` método, que retorna um número especificado de `ICorDebugAppDomainEnum` valores começando no próximo local na enumeração.</span><span class="sxs-lookup"><span data-stu-id="be5cf-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="be5cf-104">Essa interface é uma subclasse de "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="be5cf-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be5cf-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="be5cf-105">Methods</span></span>  
  
|<span data-ttu-id="be5cf-106">Método</span><span class="sxs-lookup"><span data-stu-id="be5cf-106">Method</span></span>|<span data-ttu-id="be5cf-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="be5cf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="be5cf-108">Método Next</span><span class="sxs-lookup"><span data-stu-id="be5cf-108">Next Method</span></span>](icordebugappdomainenum-next-method.md)|<span data-ttu-id="be5cf-109">Obtém o número especificado de domínios de aplicativo da coleção, começando na posição atual do cursor.</span><span class="sxs-lookup"><span data-stu-id="be5cf-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be5cf-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="be5cf-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be5cf-111">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="be5cf-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be5cf-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="be5cf-112">Requirements</span></span>  
 <span data-ttu-id="be5cf-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be5cf-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be5cf-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be5cf-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be5cf-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be5cf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be5cf-116">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be5cf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be5cf-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be5cf-117">See also</span></span>

- [<span data-ttu-id="be5cf-118">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="be5cf-118">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="be5cf-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="be5cf-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
