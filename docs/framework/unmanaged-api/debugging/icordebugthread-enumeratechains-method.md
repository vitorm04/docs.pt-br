---
title: Método ICorDebugThread::EnumerateChains
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f0ed843f72d3f1e1575da15776a94a9097fd02
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771107"
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="2c79c-102">Método ICorDebugThread::EnumerateChains</span><span class="sxs-lookup"><span data-stu-id="2c79c-102">ICorDebugThread::EnumerateChains Method</span></span>
<span data-ttu-id="2c79c-103">Obtém um ponteiro de interface para um enumerador de ICorDebugChainEnum que contém todas as cadeias de pilha neste objeto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="2c79c-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c79c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2c79c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c79c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c79c-105">Parameters</span></span>  
 `ppChains`  
 <span data-ttu-id="2c79c-106">[out] Um ponteiro para o endereço de um `ICorDebugChainEnum` objeto que permite a enumeração de todos os a pilha encadeia neste thread, começando na cadeia de ativo (ou seja, o mais recente).</span><span class="sxs-lookup"><span data-stu-id="2c79c-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c79c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2c79c-107">Remarks</span></span>  
 <span data-ttu-id="2c79c-108">A cadeia da pilha representa a pilha de chamadas física para o thread.</span><span class="sxs-lookup"><span data-stu-id="2c79c-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="2c79c-109">As circunstâncias a seguir criar um limite de cadeia de pilha:</span><span class="sxs-lookup"><span data-stu-id="2c79c-109">The following circumstances create a stack chain boundary:</span></span>  
  
- <span data-ttu-id="2c79c-110">Uma transição para gerenciado ou não gerenciado para gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2c79c-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
- <span data-ttu-id="2c79c-111">A alternância de contexto.</span><span class="sxs-lookup"><span data-stu-id="2c79c-111">A context switch.</span></span>  
  
- <span data-ttu-id="2c79c-112">Um sequestro de um thread de usuário do depurador.</span><span class="sxs-lookup"><span data-stu-id="2c79c-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="2c79c-113">No caso mais simples para um thread que está executando código puramente gerenciado em um único contexto, uma correspondência direta existirá entre os threads e cadeias de pilha.</span><span class="sxs-lookup"><span data-stu-id="2c79c-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="2c79c-114">Um depurador talvez queira reorganizar as pilhas de chamadas física de todos os threads em pilhas de chamadas lógicas.</span><span class="sxs-lookup"><span data-stu-id="2c79c-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="2c79c-115">Isso envolveria a classificação de cadeias de todos os threads por suas relações de chamador/receptor e reagrupá-los.</span><span class="sxs-lookup"><span data-stu-id="2c79c-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c79c-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2c79c-116">Requirements</span></span>  
 <span data-ttu-id="2c79c-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c79c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c79c-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c79c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c79c-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c79c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c79c-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c79c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
