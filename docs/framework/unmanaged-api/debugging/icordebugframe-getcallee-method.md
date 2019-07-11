---
title: Método ICorDebugFrame::GetCallee
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10a5247632f242a4b4e0d33cf7fa7233d1b1e13b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754205"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="7074a-102">Método ICorDebugFrame::GetCallee</span><span class="sxs-lookup"><span data-stu-id="7074a-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="7074a-103">Obtém um ponteiro para o objeto ICorDebugFrame na cadeia de atual deste quadro de chamada.</span><span class="sxs-lookup"><span data-stu-id="7074a-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7074a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7074a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7074a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7074a-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="7074a-106">[out] Um ponteiro para o endereço de um `ICorDebugFrame` objeto que representa o quadro de chamada.</span><span class="sxs-lookup"><span data-stu-id="7074a-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="7074a-107">Esse valor será nulo se o quadro de chamada é o quadro mais interno da cadeia atual.</span><span class="sxs-lookup"><span data-stu-id="7074a-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7074a-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7074a-108">Requirements</span></span>  
 <span data-ttu-id="7074a-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7074a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7074a-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7074a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7074a-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7074a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7074a-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7074a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
