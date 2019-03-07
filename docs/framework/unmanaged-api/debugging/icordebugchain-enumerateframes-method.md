---
title: Método ICorDebugChain::EnumerateFrames
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7568f8ca3b92ef465ab595348f68895f389d61e4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489703"
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="b1b7b-102">Método ICorDebugChain::EnumerateFrames</span><span class="sxs-lookup"><span data-stu-id="b1b7b-102">ICorDebugChain::EnumerateFrames Method</span></span>
<span data-ttu-id="b1b7b-103">Obtém um enumerador que contém todos os quadros de pilha gerenciada na cadeia, começando com o quadro mais recente.</span><span class="sxs-lookup"><span data-stu-id="b1b7b-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1b7b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1b7b-104">Syntax</span></span>  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1b7b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1b7b-105">Parameters</span></span>  
 `ppFrames`  
 <span data-ttu-id="b1b7b-106">[out] Um ponteiro para o endereço de um objeto ICorDebugFrameEnum que é o enumerador para os quadros de pilha.</span><span class="sxs-lookup"><span data-stu-id="b1b7b-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1b7b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1b7b-107">Remarks</span></span>  
 <span data-ttu-id="b1b7b-108">A cadeia representa a pilha de chamadas física para o thread.</span><span class="sxs-lookup"><span data-stu-id="b1b7b-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="b1b7b-109">O `EnumerateFrames` método deve ser chamado apenas para cadeias de gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b1b7b-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="b1b7b-110">A API de depuração não fornece métodos para obter quadros contidos nas cadeias de não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="b1b7b-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="b1b7b-111">O depurador deve usar outros meios para obter essas informações.</span><span class="sxs-lookup"><span data-stu-id="b1b7b-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1b7b-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1b7b-112">Requirements</span></span>  
 <span data-ttu-id="b1b7b-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1b7b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1b7b-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1b7b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1b7b-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1b7b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1b7b-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1b7b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
