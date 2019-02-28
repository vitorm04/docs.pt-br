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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c340eb76f3c1c570aa0c9ffa1d461f33d330175
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981498"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="592a2-102">Interface ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="592a2-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="592a2-103">Fornece o `Next` método, que retorna um número especificado de `ICorDebugAppDomainEnum` começando no próximo local na enumeração de valores.</span><span class="sxs-lookup"><span data-stu-id="592a2-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="592a2-104">Essa interface é uma subclasse de "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="592a2-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="592a2-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="592a2-105">Methods</span></span>  
  
|<span data-ttu-id="592a2-106">Método</span><span class="sxs-lookup"><span data-stu-id="592a2-106">Method</span></span>|<span data-ttu-id="592a2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="592a2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="592a2-108">Método Next</span><span class="sxs-lookup"><span data-stu-id="592a2-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="592a2-109">Obtém o número de domínios de aplicativo especificado da coleção, começando na posição atual do cursor.</span><span class="sxs-lookup"><span data-stu-id="592a2-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="592a2-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="592a2-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="592a2-111">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="592a2-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="592a2-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="592a2-112">Requirements</span></span>  
 <span data-ttu-id="592a2-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="592a2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="592a2-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="592a2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="592a2-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="592a2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="592a2-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="592a2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="592a2-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="592a2-117">See also</span></span>
- [<span data-ttu-id="592a2-118">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="592a2-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="592a2-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="592a2-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
