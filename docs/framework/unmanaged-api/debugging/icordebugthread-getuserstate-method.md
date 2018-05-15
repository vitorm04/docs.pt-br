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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06ff8f0f13d7710d2d3d59aac4b5fdcadfe707be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="8be44-102">Método ICorDebugThread::GetUserState</span><span class="sxs-lookup"><span data-stu-id="8be44-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="8be44-103">Obtém o estado do usuário atual deste ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="8be44-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8be44-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8be44-104">Syntax</span></span>  
  
```  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8be44-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8be44-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="8be44-106">[out] Um ponteiro para uma combinação bit a bit dos valores de enumeração CorDebugUserState que descrevem o estado do usuário atual deste thread.</span><span class="sxs-lookup"><span data-stu-id="8be44-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8be44-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8be44-107">Remarks</span></span>  
 <span data-ttu-id="8be44-108">O estado do usuário do thread é o estado do thread quando ele é examinado com o programa que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="8be44-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="8be44-109">Um thread pode ter vários bits de estado definido.</span><span class="sxs-lookup"><span data-stu-id="8be44-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8be44-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8be44-110">Requirements</span></span>  
 <span data-ttu-id="8be44-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8be44-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8be44-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8be44-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8be44-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8be44-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8be44-114">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8be44-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
