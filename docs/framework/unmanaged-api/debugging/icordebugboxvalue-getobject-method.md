---
title: Método ICorDebugBoxValue::GetObject
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cfc8800915009912716ec2ed9044a633a8ad0582
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="b1d96-102">Método ICorDebugBoxValue::GetObject</span><span class="sxs-lookup"><span data-stu-id="b1d96-102">ICorDebugBoxValue::GetObject Method</span></span>
<span data-ttu-id="b1d96-103">Obtém o valor Demarcado.</span><span class="sxs-lookup"><span data-stu-id="b1d96-103">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1d96-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1d96-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1d96-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1d96-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="b1d96-106">[out] Um ponteiro para o endereço de um objeto ICorDebugObjectValue que representa o valor Demarcado.</span><span class="sxs-lookup"><span data-stu-id="b1d96-106">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1d96-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1d96-107">Requirements</span></span>  
 <span data-ttu-id="b1d96-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1d96-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1d96-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1d96-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1d96-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1d96-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1d96-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1d96-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
