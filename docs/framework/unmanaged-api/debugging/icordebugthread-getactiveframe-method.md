---
title: Método ICorDebugThread::GetActiveFrame
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveFrame
helpviewer_keywords:
- ICorDebugThread::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 8d6d3a1a-fef6-4f2f-a22c-3bdd30d70e07
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 051491173bbcef3d87d9a3dbe854eece46c49e0d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468774"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="86d27-102">Método ICorDebugThread::GetActiveFrame</span><span class="sxs-lookup"><span data-stu-id="86d27-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="86d27-103">Obtém um ponteiro de interface para o quadro ativo (mais recente) neste objeto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="86d27-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86d27-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86d27-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86d27-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="86d27-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="86d27-106">[out] Um ponteiro para o endereço de um objeto de interface ICorDebugFrame que representa um quadro.</span><span class="sxs-lookup"><span data-stu-id="86d27-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86d27-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="86d27-107">Remarks</span></span>  
 <span data-ttu-id="86d27-108">O `ppFrame` parâmetro será nulo se nenhum quadro estiver ativo no momento.</span><span class="sxs-lookup"><span data-stu-id="86d27-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86d27-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="86d27-109">Requirements</span></span>  
 <span data-ttu-id="86d27-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86d27-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86d27-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86d27-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86d27-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86d27-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86d27-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86d27-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
