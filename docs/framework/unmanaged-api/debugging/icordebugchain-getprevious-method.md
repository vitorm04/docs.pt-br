---
title: Método ICorDebugChain::GetPrevious
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetPrevious
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fdcdf23dfee01e8bad1c95adb4de66f270d5e00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645260"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="fec13-102">Método ICorDebugChain::GetPrevious</span><span class="sxs-lookup"><span data-stu-id="fec13-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="fec13-103">Obtém a cadeia anterior de quadros do thread.</span><span class="sxs-lookup"><span data-stu-id="fec13-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fec13-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fec13-104">Syntax</span></span>  
  
```  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fec13-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fec13-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="fec13-106">[out] Um ponteiro para o endereço de um objeto ICorDebugChain que representa a cadeia anterior de quadros para este thread.</span><span class="sxs-lookup"><span data-stu-id="fec13-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="fec13-107">Se essa cadeia é a primeira cadeia, `ppChain` é nulo.</span><span class="sxs-lookup"><span data-stu-id="fec13-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fec13-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fec13-108">Requirements</span></span>  
 <span data-ttu-id="fec13-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fec13-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fec13-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fec13-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fec13-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fec13-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fec13-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fec13-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
