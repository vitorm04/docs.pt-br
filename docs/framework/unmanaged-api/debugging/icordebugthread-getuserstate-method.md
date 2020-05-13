---
title: Método ICorDebugThread::GetUserState
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetUserState
helpviewer_keywords:
- GetUserState method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetUserState method [.NET Framework debugging]
ms.assetid: ae0cfd73-8ead-4d36-9310-dccaac9db0bd
topic_type:
- apiref
ms.openlocfilehash: d1ff3427feb5dc8395bbb2fda78e3e93e1a1a8f0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378854"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="1c329-102">Método ICorDebugThread::GetUserState</span><span class="sxs-lookup"><span data-stu-id="1c329-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="1c329-103">Obtém o estado atual do usuário deste ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="1c329-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c329-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c329-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c329-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c329-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="1c329-106">fora Um ponteiro para uma combinação de bits de valor de enumeração CorDebugUserState que descreve o estado atual do usuário desse thread.</span><span class="sxs-lookup"><span data-stu-id="1c329-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c329-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1c329-107">Remarks</span></span>  
 <span data-ttu-id="1c329-108">O estado do usuário do thread é o estado do thread quando ele é examinado pelo programa que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="1c329-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="1c329-109">Um thread pode ter vários bits de estado definidos.</span><span class="sxs-lookup"><span data-stu-id="1c329-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c329-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1c329-110">Requirements</span></span>  
 <span data-ttu-id="1c329-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c329-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c329-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c329-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c329-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c329-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c329-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c329-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
