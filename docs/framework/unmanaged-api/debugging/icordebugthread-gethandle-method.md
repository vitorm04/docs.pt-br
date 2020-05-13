---
title: Método ICorDebugThread::GetHandle
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
ms.openlocfilehash: 16aafa439fc81c3606f98ca2ba860316ec46e0db
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379746"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="dcbe4-102">Método ICorDebugThread::GetHandle</span><span class="sxs-lookup"><span data-stu-id="dcbe4-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="dcbe4-103">Obtém o identificador atual da parte ativa deste ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="dcbe4-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcbe4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dcbe4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcbe4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dcbe4-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="dcbe4-106">fora Um ponteiro para um HTHREAD que é o identificador da parte ativa deste thread.</span><span class="sxs-lookup"><span data-stu-id="dcbe4-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcbe4-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="dcbe4-107">Remarks</span></span>  
 <span data-ttu-id="dcbe4-108">O identificador pode ser alterado conforme o processo é executado e pode ser diferente para partes diferentes do thread.</span><span class="sxs-lookup"><span data-stu-id="dcbe4-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="dcbe4-109">Esse identificador é de propriedade da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="dcbe4-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="dcbe4-110">O depurador deve duplicá-lo antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="dcbe4-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcbe4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dcbe4-111">Requirements</span></span>  
 <span data-ttu-id="dcbe4-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcbe4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcbe4-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dcbe4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dcbe4-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dcbe4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcbe4-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcbe4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
