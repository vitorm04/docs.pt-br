---
title: "Método ICorDebugBoxValue::GetObject"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBoxValue.GetObject
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 072e5d3ee444444ff9288ffc4243f4a61355f1a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="e4c2f-102">Método ICorDebugBoxValue::GetObject</span><span class="sxs-lookup"><span data-stu-id="e4c2f-102">ICorDebugBoxValue::GetObject Method</span></span>
<span data-ttu-id="e4c2f-103">Obtém o valor Demarcado.</span><span class="sxs-lookup"><span data-stu-id="e4c2f-103">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4c2f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4c2f-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4c2f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e4c2f-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="e4c2f-106">[out] Um ponteiro para o endereço de um objeto ICorDebugObjectValue que representa o valor Demarcado.</span><span class="sxs-lookup"><span data-stu-id="e4c2f-106">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4c2f-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4c2f-107">Requirements</span></span>  
 <span data-ttu-id="e4c2f-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4c2f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4c2f-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4c2f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4c2f-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4c2f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4c2f-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4c2f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
