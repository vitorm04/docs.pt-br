---
title: Método ICorDebug::Initialize
ms.date: 03/30/2017
api_name:
- ICorDebug.Initialize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type:
- apiref
ms.openlocfilehash: aeecf19cb85ce5d7781c3dfedca079e97cab76ce
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895352"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="c2b5b-102">Método ICorDebug::Initialize</span><span class="sxs-lookup"><span data-stu-id="c2b5b-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="c2b5b-103">Inicializa o objeto `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2b5b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2b5b-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c2b5b-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2b5b-105">Remarks</span></span>  
 <span data-ttu-id="c2b5b-106">O depurador deve chamar `Initialize` no momento da criação para inicializar os serviços de depuração.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="c2b5b-107">Esse método deve ser chamado antes que qualquer outro método `ICorDebug` em seja chamado.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2b5b-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2b5b-108">Requirements</span></span>  
 <span data-ttu-id="c2b5b-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2b5b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2b5b-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2b5b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2b5b-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2b5b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2b5b-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2b5b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2b5b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2b5b-113">See also</span></span>

- [<span data-ttu-id="c2b5b-114">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="c2b5b-114">ICorDebug Interface</span></span>](icordebug-interface.md)
