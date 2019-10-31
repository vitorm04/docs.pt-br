---
title: Método ICorDebugHandleValue::Dispose
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.Dispose
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::Dispose
helpviewer_keywords:
- ICorDebugHandleValue::Dispose method [.NET Framework debugging]
- Dispose method [.NET Framework debugging]
ms.assetid: c1542811-0a7f-4235-bcfd-b24370d6f24b
topic_type:
- apiref
ms.openlocfilehash: 957035591090fb5a6a615662c4840ff16509ee20
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138500"
---
# <a name="icordebughandlevaluedispose-method"></a><span data-ttu-id="7e2b0-102">Método ICorDebugHandleValue::Dispose</span><span class="sxs-lookup"><span data-stu-id="7e2b0-102">ICorDebugHandleValue::Dispose Method</span></span>
<span data-ttu-id="7e2b0-103">Libera o identificador referenciado por este objeto ICorDebugHandleValue sem liberar explicitamente o ponteiro de interface.</span><span class="sxs-lookup"><span data-stu-id="7e2b0-103">Releases the handle referenced by this ICorDebugHandleValue object without explicitly releasing the interface pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e2b0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e2b0-104">Syntax</span></span>  
  
```cpp  
HRESULT Dispose ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="7e2b0-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e2b0-105">Requirements</span></span>  
 <span data-ttu-id="7e2b0-106">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e2b0-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e2b0-107">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e2b0-107">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e2b0-108">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e2b0-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e2b0-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e2b0-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
