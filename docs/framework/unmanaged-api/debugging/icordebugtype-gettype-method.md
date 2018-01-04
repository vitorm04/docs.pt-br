---
title: "Método ICorDebugType::GetType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c07f9974d0178a1a7502a97d54d7103ee795425f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="3a77a-102">Método ICorDebugType::GetType</span><span class="sxs-lookup"><span data-stu-id="3a77a-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="3a77a-103">Obtém um valor de CorElementType que descreve o tipo nativo do common language runtime (CLR) <xref:System.Type> representado por esse ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="3a77a-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a77a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a77a-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a77a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3a77a-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="3a77a-106">[out] Um ponteiro para um valor de `CorElementType` enumeração que indica o CLR <xref:System.Type> que este `ICorDebugType` representa.</span><span class="sxs-lookup"><span data-stu-id="3a77a-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a77a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a77a-107">Remarks</span></span>  
 <span data-ttu-id="3a77a-108">Se o valor de `ty` é ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, o [: Getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) método pode ser chamado para obter o tipo instanciado para um tipo genérico; caso contrário, não chame `ICorDebugType::GetClass`.</span><span class="sxs-lookup"><span data-stu-id="3a77a-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a77a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a77a-109">Requirements</span></span>  
 <span data-ttu-id="3a77a-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a77a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a77a-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a77a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a77a-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a77a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a77a-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a77a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
