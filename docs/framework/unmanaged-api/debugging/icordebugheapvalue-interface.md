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
ms.openlocfilehash: 4f87065fc4a3d80a8363f3ae2fbb76c29f3d9b96
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138410"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="eaf84-102">Interface ICorDebugHeapValue</span><span class="sxs-lookup"><span data-stu-id="eaf84-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="eaf84-103">Uma subclasse de "ICorDebugValue" que representa um objeto que foi coletado pelo coletor de lixo Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="eaf84-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eaf84-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="eaf84-104">Methods</span></span>  
  
|<span data-ttu-id="eaf84-105">Método</span><span class="sxs-lookup"><span data-stu-id="eaf84-105">Method</span></span>|<span data-ttu-id="eaf84-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="eaf84-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eaf84-107">Método CreateRelocBreakpoint</span><span class="sxs-lookup"><span data-stu-id="eaf84-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="eaf84-108">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="eaf84-108">Not implemented.</span></span>|  
|[<span data-ttu-id="eaf84-109">Método IsValid</span><span class="sxs-lookup"><span data-stu-id="eaf84-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="eaf84-110">Obtém um valor que indica se o objeto representado por este `ICorDebugHeapValue` é válido ou se foi recuperado pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="eaf84-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="eaf84-111">Esse método foi preterido no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="eaf84-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eaf84-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="eaf84-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eaf84-113">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="eaf84-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaf84-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eaf84-114">Requirements</span></span>  
 <span data-ttu-id="eaf84-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaf84-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaf84-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eaf84-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eaf84-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eaf84-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eaf84-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaf84-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaf84-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eaf84-119">See also</span></span>

- [<span data-ttu-id="eaf84-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="eaf84-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
