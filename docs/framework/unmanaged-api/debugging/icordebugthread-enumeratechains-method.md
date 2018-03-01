---
title: "Método ICorDebugThread::EnumerateChains"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8e6a9637edb4a846b4d10dd6565533a9219ad558
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="815e4-102">Método ICorDebugThread::EnumerateChains</span><span class="sxs-lookup"><span data-stu-id="815e4-102">ICorDebugThread::EnumerateChains Method</span></span>
<span data-ttu-id="815e4-103">Obtém um ponteiro de interface para um enumerador de ICorDebugChainEnum que contém todas as cadeias de pilha no objeto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="815e4-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="815e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="815e4-104">Syntax</span></span>  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="815e4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="815e4-105">Parameters</span></span>  
 `ppChains`  
 <span data-ttu-id="815e4-106">[out] Um ponteiro para o endereço de uma `ICorDebugChainEnum` objeto que permite a enumeração de todos os a pilha encadeia neste thread, começando na cadeia de ativo (ou seja, o mais recente).</span><span class="sxs-lookup"><span data-stu-id="815e4-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="815e4-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="815e4-107">Remarks</span></span>  
 <span data-ttu-id="815e4-108">A cadeia da pilha representa a pilha de chamadas físico para o thread.</span><span class="sxs-lookup"><span data-stu-id="815e4-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="815e4-109">As circunstâncias a seguir criar um limite de cadeia de pilha:</span><span class="sxs-lookup"><span data-stu-id="815e4-109">The following circumstances create a stack chain boundary:</span></span>  
  
-   <span data-ttu-id="815e4-110">Uma transição gerenciado para gerenciado ou não gerenciado para gerenciado.</span><span class="sxs-lookup"><span data-stu-id="815e4-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
-   <span data-ttu-id="815e4-111">Uma alternância de contexto.</span><span class="sxs-lookup"><span data-stu-id="815e4-111">A context switch.</span></span>  
  
-   <span data-ttu-id="815e4-112">Um sequestro de um thread de usuário do depurador.</span><span class="sxs-lookup"><span data-stu-id="815e4-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="815e4-113">No caso mais simples para um thread que está executando o código totalmente gerenciado em um único contexto, exista uma correspondência entre threads e cadeias de pilha.</span><span class="sxs-lookup"><span data-stu-id="815e4-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="815e4-114">Um depurador talvez queira reorganizar as pilhas de chamadas física de todos os threads em pilhas de chamadas lógicas.</span><span class="sxs-lookup"><span data-stu-id="815e4-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="815e4-115">Isso envolve a classificação de cadeias de todos os threads por suas relações de chamador/receptor e reagrupá-los.</span><span class="sxs-lookup"><span data-stu-id="815e4-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="815e4-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="815e4-116">Requirements</span></span>  
 <span data-ttu-id="815e4-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="815e4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="815e4-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="815e4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="815e4-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="815e4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="815e4-120">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="815e4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
