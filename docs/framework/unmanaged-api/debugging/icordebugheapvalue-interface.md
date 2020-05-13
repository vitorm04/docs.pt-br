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
ms.openlocfilehash: 36a485413490045ca49b99fca4fe5d43edc37114
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213004"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="fff7c-102">Interface ICorDebugHeapValue</span><span class="sxs-lookup"><span data-stu-id="fff7c-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="fff7c-103">Uma subclasse de "ICorDebugValue" que representa um objeto que foi coletado pelo coletor de lixo Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="fff7c-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fff7c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="fff7c-104">Methods</span></span>  
  
|<span data-ttu-id="fff7c-105">Método</span><span class="sxs-lookup"><span data-stu-id="fff7c-105">Method</span></span>|<span data-ttu-id="fff7c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="fff7c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fff7c-107">Método CreateRelocBreakpoint</span><span class="sxs-lookup"><span data-stu-id="fff7c-107">CreateRelocBreakpoint Method</span></span>](icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="fff7c-108">Não implementado.</span><span class="sxs-lookup"><span data-stu-id="fff7c-108">Not implemented.</span></span>|  
|[<span data-ttu-id="fff7c-109">Método IsValid</span><span class="sxs-lookup"><span data-stu-id="fff7c-109">IsValid Method</span></span>](icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="fff7c-110">Obtém um valor que indica se o objeto representado por ele `ICorDebugHeapValue` é válido ou se foi recuperado pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="fff7c-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="fff7c-111">Esse método foi preterido no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="fff7c-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fff7c-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="fff7c-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fff7c-113">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="fff7c-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fff7c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fff7c-114">Requirements</span></span>  
 <span data-ttu-id="fff7c-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fff7c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fff7c-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fff7c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fff7c-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fff7c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fff7c-118">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fff7c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fff7c-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="fff7c-119">See also</span></span>

- [<span data-ttu-id="fff7c-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fff7c-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
