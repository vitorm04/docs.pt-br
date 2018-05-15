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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60bd7567f541a0bbaa3591d2f2905d13064dec3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="5a920-102">Método ICorDebugProcess::GetHandle</span><span class="sxs-lookup"><span data-stu-id="5a920-102">ICorDebugProcess::GetHandle Method</span></span>
<span data-ttu-id="5a920-103">Obtém um identificador para o processo.</span><span class="sxs-lookup"><span data-stu-id="5a920-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a920-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a920-104">Syntax</span></span>  
  
```  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a920-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5a920-105">Parameters</span></span>  
 `phProcessHandle`  
 <span data-ttu-id="5a920-106">[out] Um ponteiro para um `HPROCESS` que é o identificador para o processo.</span><span class="sxs-lookup"><span data-stu-id="5a920-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a920-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5a920-107">Remarks</span></span>  
 <span data-ttu-id="5a920-108">O identificador recuperado pertence a interface de depuração.</span><span class="sxs-lookup"><span data-stu-id="5a920-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="5a920-109">O depurador deve duplicar o identificador antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="5a920-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a920-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5a920-110">Requirements</span></span>  
 <span data-ttu-id="5a920-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a920-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a920-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a920-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a920-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a920-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a920-114">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a920-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
