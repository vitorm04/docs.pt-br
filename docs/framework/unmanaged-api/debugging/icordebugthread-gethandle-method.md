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
ms.openlocfilehash: 33219d9a67379244e23da49c13617a4c4a2fa66d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133460"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="d6e81-102">Método ICorDebugThread::GetHandle</span><span class="sxs-lookup"><span data-stu-id="d6e81-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="d6e81-103">Obtém o identificador atual da parte ativa deste ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="d6e81-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6e81-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6e81-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6e81-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6e81-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="d6e81-106">fora Um ponteiro para um HTHREAD que é o identificador da parte ativa deste thread.</span><span class="sxs-lookup"><span data-stu-id="d6e81-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6e81-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6e81-107">Remarks</span></span>  
 <span data-ttu-id="d6e81-108">O identificador pode ser alterado conforme o processo é executado e pode ser diferente para partes diferentes do thread.</span><span class="sxs-lookup"><span data-stu-id="d6e81-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="d6e81-109">Esse identificador é de propriedade da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="d6e81-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="d6e81-110">O depurador deve duplicá-lo antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="d6e81-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6e81-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6e81-111">Requirements</span></span>  
 <span data-ttu-id="d6e81-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6e81-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6e81-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6e81-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6e81-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6e81-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6e81-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6e81-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
