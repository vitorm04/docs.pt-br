---
title: Interface ICorDebugHeapValue
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5263474b7b5001d561652291c23220da0a942bd1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980562"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="1c6e7-102">Interface ICorDebugHeapValue</span><span class="sxs-lookup"><span data-stu-id="1c6e7-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="1c6e7-103">Uma subclasse de "ICorDebugValue" que representa um objeto que foram coletado pelo coletor de lixo do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="1c6e7-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1c6e7-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="1c6e7-104">Methods</span></span>  
  
|<span data-ttu-id="1c6e7-105">Método</span><span class="sxs-lookup"><span data-stu-id="1c6e7-105">Method</span></span>|<span data-ttu-id="1c6e7-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c6e7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1c6e7-107">Método CreateRelocBreakpoint</span><span class="sxs-lookup"><span data-stu-id="1c6e7-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="1c6e7-108">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="1c6e7-108">Not implemented.</span></span>|  
|[<span data-ttu-id="1c6e7-109">Método IsValid</span><span class="sxs-lookup"><span data-stu-id="1c6e7-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="1c6e7-110">Obtém um valor que indica se o objeto representado por este `ICorDebugHeapValue` é válido ou foi recuperado pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="1c6e7-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="1c6e7-111">Esse método foi preterido no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="1c6e7-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c6e7-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="1c6e7-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c6e7-113">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="1c6e7-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c6e7-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1c6e7-114">Requirements</span></span>  
 <span data-ttu-id="1c6e7-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c6e7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c6e7-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c6e7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c6e7-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c6e7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c6e7-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c6e7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c6e7-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c6e7-119">See also</span></span>



- [<span data-ttu-id="1c6e7-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1c6e7-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
