---
title: "Método ICorDebugProcess::GetThread"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetThread
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetThread
helpviewer_keywords:
- ICorDebugProcess::GetThread method [.NET Framework debugging]
- GetThread method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a48261ed-700b-41c9-8cb4-18c526546603
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: da5acebb9cb90efa69b0f553a1480e5e6883d079
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="599e4-102">Método ICorDebugProcess::GetThread</span><span class="sxs-lookup"><span data-stu-id="599e4-102">ICorDebugProcess::GetThread Method</span></span>
<span data-ttu-id="599e4-103">Obtém o segmento desse processo que tem a ID do thread de sistema operacional especificado (SO).</span><span class="sxs-lookup"><span data-stu-id="599e4-103">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="599e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="599e4-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="599e4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="599e4-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="599e4-106">[in] ID do thread a ser recuperado do thread do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="599e4-106">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="599e4-107">[out] Um ponteiro para o endereço de um objeto ICorDebugThread que representa o thread.</span><span class="sxs-lookup"><span data-stu-id="599e4-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="599e4-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="599e4-108">Requirements</span></span>  
 <span data-ttu-id="599e4-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="599e4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="599e4-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="599e4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="599e4-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="599e4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="599e4-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="599e4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
