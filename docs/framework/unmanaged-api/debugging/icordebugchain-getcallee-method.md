---
title: Método ICorDebugChain::GetCallee
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
ms.openlocfilehash: 5d28af09faae84b0482d438ae33f593f250490c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196332"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="0e4db-102">Método ICorDebugChain::GetCallee</span><span class="sxs-lookup"><span data-stu-id="0e4db-102">ICorDebugChain::GetCallee Method</span></span>
<span data-ttu-id="0e4db-103">Obtém a cadeia que foi chamada por essa cadeia.</span><span class="sxs-lookup"><span data-stu-id="0e4db-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e4db-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e4db-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e4db-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0e4db-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="0e4db-106">fora Um ponteiro para o endereço de um objeto ICorDebugChain que representa a cadeia chamada.</span><span class="sxs-lookup"><span data-stu-id="0e4db-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="0e4db-107">Se essa cadeia estiver em execução no momento (ou seja, se essa cadeia não estiver esperando uma cadeia chamada retornar), `ppChain` será NULL.</span><span class="sxs-lookup"><span data-stu-id="0e4db-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e4db-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="0e4db-108">Remarks</span></span>  
 <span data-ttu-id="0e4db-109">Essa cadeia aguardará que a cadeia chamada seja retornada antes de retomar a execução.</span><span class="sxs-lookup"><span data-stu-id="0e4db-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="0e4db-110">A cadeia chamada pode estar em outro thread no caso de chamadas empacotadas entre threads.</span><span class="sxs-lookup"><span data-stu-id="0e4db-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e4db-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0e4db-111">Requirements</span></span>  
 <span data-ttu-id="0e4db-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e4db-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e4db-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e4db-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e4db-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e4db-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e4db-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e4db-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
