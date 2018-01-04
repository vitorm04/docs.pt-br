---
title: "Método ICorDebugType::GetFirstTypeParameter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetFirstTypeParameter
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e963553bfeac2d659de8fc460a938d2d523b53e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="60a1a-102">Método ICorDebugType::GetFirstTypeParameter</span><span class="sxs-lookup"><span data-stu-id="60a1a-102">ICorDebugType::GetFirstTypeParameter Method</span></span>
<span data-ttu-id="60a1a-103">Obtém um ponteiro de interface para um que representa a primeira ICorDebugType <xref:System.Type> parâmetro do tipo representado por esse `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="60a1a-103">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60a1a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60a1a-104">Syntax</span></span>  
  
```  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60a1a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="60a1a-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="60a1a-106">[out] Um ponteiro para o endereço de uma `ICorDebugType` objeto que representa o primeiro parâmetro.</span><span class="sxs-lookup"><span data-stu-id="60a1a-106">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60a1a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="60a1a-107">Remarks</span></span>  
 <span data-ttu-id="60a1a-108">`GetFirstTypeParameter`pode ser chamado em casos onde as informações adicionais sobre o tipo envolverem, no máximo, um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="60a1a-108">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="60a1a-109">Em particular, ele pode ser usado se o tipo for um ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ou ELEMENT_TYPE_PTR, conforme indicado pelo [Icordebugtype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="60a1a-109">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60a1a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="60a1a-110">Requirements</span></span>  
 <span data-ttu-id="60a1a-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60a1a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60a1a-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60a1a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60a1a-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60a1a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60a1a-114">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60a1a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
