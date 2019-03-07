---
title: Método ICorDebugProcess::GetThread
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThread
helpviewer_keywords:
- ICorDebugProcess::GetThread method [.NET Framework debugging]
- GetThread method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a48261ed-700b-41c9-8cb4-18c526546603
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36070d5374a11daf4b7800481c86d61057989631
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470063"
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="c2b4f-102">Método ICorDebugProcess::GetThread</span><span class="sxs-lookup"><span data-stu-id="c2b4f-102">ICorDebugProcess::GetThread Method</span></span>
<span data-ttu-id="c2b4f-103">Obtém o thread desse processador que tem a ID do thread de sistema operacional especificado (SO).</span><span class="sxs-lookup"><span data-stu-id="c2b4f-103">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2b4f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2b4f-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2b4f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2b4f-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="c2b4f-106">[in] O sistema operacional do thread ID do thread a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="c2b4f-106">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="c2b4f-107">[out] Um ponteiro para o endereço de um objeto de ICorDebugThread que representa o thread.</span><span class="sxs-lookup"><span data-stu-id="c2b4f-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2b4f-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2b4f-108">Requirements</span></span>  
 <span data-ttu-id="c2b4f-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2b4f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2b4f-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2b4f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2b4f-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2b4f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2b4f-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2b4f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
