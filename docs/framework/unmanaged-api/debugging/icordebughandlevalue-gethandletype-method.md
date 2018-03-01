---
title: "Método ICorDebugHandleValue::GetHandleType"
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
- ICorDebugHandleValue.GetHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::GetHandleType
helpviewer_keywords:
- GetHandleType method [.NET Framework debugging]
- ICorDebugHandleValue::GetHandleType method [.NET Framework debugging]
ms.assetid: d5e7b12d-835a-4e86-ae2f-d658d4f1c67c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b41e7c14fd0abdd957f0661345a6372074f2ed7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="b4be9-102">Método ICorDebugHandleValue::GetHandleType</span><span class="sxs-lookup"><span data-stu-id="b4be9-102">ICorDebugHandleValue::GetHandleType Method</span></span>
<span data-ttu-id="b4be9-103">Obtém um valor que indica o tipo de identificador referenciada por este objeto ICorDebugHandleValue.</span><span class="sxs-lookup"><span data-stu-id="b4be9-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4be9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4be9-104">Syntax</span></span>  
  
```  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4be9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b4be9-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="b4be9-106">[out] Um ponteiro para um valor da enumeração CorDebugHandleType que indica o tipo desse identificador.</span><span class="sxs-lookup"><span data-stu-id="b4be9-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4be9-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b4be9-107">Requirements</span></span>  
 <span data-ttu-id="b4be9-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4be9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4be9-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4be9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4be9-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4be9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4be9-111">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4be9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
