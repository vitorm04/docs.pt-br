---
title: Método ICorDebugProcess::GetID
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetID
helpviewer_keywords:
- GetID method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetID method [.NET Framework debugging]
ms.assetid: b0ba8453-fa7e-4c14-93e5-335409cd4a47
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d752eb17b956e2367e8b191080a370506a61ff34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416661"
---
# <a name="icordebugprocessgetid-method"></a><span data-ttu-id="37752-102">Método ICorDebugProcess::GetID</span><span class="sxs-lookup"><span data-stu-id="37752-102">ICorDebugProcess::GetID Method</span></span>
<span data-ttu-id="37752-103">Obtém a ID de sistema operacional (SO) do processo.</span><span class="sxs-lookup"><span data-stu-id="37752-103">Gets the operating system (OS) ID of the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37752-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37752-104">Syntax</span></span>  
  
```  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37752-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="37752-105">Parameters</span></span>  
 `pdwProcessId`  
 <span data-ttu-id="37752-106">[out] A ID exclusiva do processo.</span><span class="sxs-lookup"><span data-stu-id="37752-106">[out] The unique ID of the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37752-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="37752-107">Requirements</span></span>  
 <span data-ttu-id="37752-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37752-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37752-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37752-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37752-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37752-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37752-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37752-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
