---
title: Método ICorDebugThread::GetID
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type:
- apiref
ms.openlocfilehash: d01936481ec139757566d5b96cb95ea887cb8c20
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378066"
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="a2248-102">Método ICorDebugThread::GetID</span><span class="sxs-lookup"><span data-stu-id="a2248-102">ICorDebugThread::GetID Method</span></span>
<span data-ttu-id="a2248-103">Obtém o identificador do sistema operacional atual da parte ativa deste ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="a2248-103">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2248-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2248-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2248-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a2248-105">Parameters</span></span>  
 `pdwThreadId`  
 <span data-ttu-id="a2248-106">fora O identificador do thread.</span><span class="sxs-lookup"><span data-stu-id="a2248-106">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2248-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a2248-107">Remarks</span></span>  
 <span data-ttu-id="a2248-108">O identificador do sistema operacional pode potencialmente ser alterado durante a execução de um processo e pode ser um valor diferente para diferentes partes do thread.</span><span class="sxs-lookup"><span data-stu-id="a2248-108">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2248-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a2248-109">Requirements</span></span>  
 <span data-ttu-id="a2248-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2248-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2248-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2248-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2248-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2248-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2248-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2248-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
