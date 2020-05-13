---
title: Método ICorDebugType::GetType
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
ms.openlocfilehash: ac42c6254182ea775377a448a54d527b234c97dc
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379919"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="92e19-102">Método ICorDebugType::GetType</span><span class="sxs-lookup"><span data-stu-id="92e19-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="92e19-103">Obtém um valor de CorElementType que descreve o tipo nativo do Common Language Runtime (CLR) <xref:System.Type> representado por esse ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="92e19-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92e19-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92e19-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92e19-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="92e19-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="92e19-106">fora Um ponteiro para um valor da `CorElementType` enumeração que indica o CLR <xref:System.Type> que isso `ICorDebugType` representa.</span><span class="sxs-lookup"><span data-stu-id="92e19-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92e19-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="92e19-107">Remarks</span></span>  
 <span data-ttu-id="92e19-108">Se o valor de `ty` for ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, o método [ICorDebugType:: GetClass](icordebugtype-getclass-method.md) poderá ser chamado para obter o tipo não instanciado para um tipo genérico; caso contrário, não chame `ICorDebugType::GetClass` .</span><span class="sxs-lookup"><span data-stu-id="92e19-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92e19-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92e19-109">Requirements</span></span>  
 <span data-ttu-id="92e19-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92e19-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92e19-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92e19-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92e19-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92e19-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92e19-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92e19-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
