---
title: "Método ICorDebugThread::GetHandle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c7a932d04fef438e19176af565c92e0673339e02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="67187-102">Método ICorDebugThread::GetHandle</span><span class="sxs-lookup"><span data-stu-id="67187-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="67187-103">Obtém o identificador atual para a parte ativa deste ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="67187-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67187-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="67187-104">Syntax</span></span>  
  
```  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67187-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="67187-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="67187-106">[out] Um ponteiro para um HTHREAD que é o identificador da parte ativa desse thread.</span><span class="sxs-lookup"><span data-stu-id="67187-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67187-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="67187-107">Remarks</span></span>  
 <span data-ttu-id="67187-108">O identificador pode alterar como o processo é executado e pode ser diferente para diferentes partes do thread.</span><span class="sxs-lookup"><span data-stu-id="67187-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="67187-109">Esse identificador é de propriedade pela API de depuração.</span><span class="sxs-lookup"><span data-stu-id="67187-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="67187-110">O depurador deve duplicar antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="67187-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67187-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="67187-111">Requirements</span></span>  
 <span data-ttu-id="67187-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67187-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67187-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67187-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67187-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67187-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67187-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67187-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
