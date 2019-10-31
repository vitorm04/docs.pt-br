---
title: Método ICorDebugProcess::GetHandle
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
ms.openlocfilehash: e4061580d59b0cf2a6e6e481d5242005e9452caf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128866"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="2ca66-102">Método ICorDebugProcess::GetHandle</span><span class="sxs-lookup"><span data-stu-id="2ca66-102">ICorDebugProcess::GetHandle Method</span></span>
<span data-ttu-id="2ca66-103">Obtém um identificador para o processo.</span><span class="sxs-lookup"><span data-stu-id="2ca66-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ca66-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ca66-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ca66-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2ca66-105">Parameters</span></span>  
 `phProcessHandle`  
 <span data-ttu-id="2ca66-106">fora Um ponteiro para um `HPROCESS` que é o identificador para o processo.</span><span class="sxs-lookup"><span data-stu-id="2ca66-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ca66-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2ca66-107">Remarks</span></span>  
 <span data-ttu-id="2ca66-108">O identificador recuperado pertence à interface de depuração.</span><span class="sxs-lookup"><span data-stu-id="2ca66-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="2ca66-109">O depurador deve duplicar o identificador antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="2ca66-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ca66-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2ca66-110">Requirements</span></span>  
 <span data-ttu-id="2ca66-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ca66-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ca66-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ca66-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ca66-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ca66-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ca66-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ca66-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
