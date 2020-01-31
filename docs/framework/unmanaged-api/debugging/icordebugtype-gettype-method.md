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
ms.openlocfilehash: 25ffbf73fbefbb3c584450283c3080dfc11ee598
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791249"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="98cc3-102">Método ICorDebugType::GetType</span><span class="sxs-lookup"><span data-stu-id="98cc3-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="98cc3-103">Obtém um valor de CorElementType que descreve o tipo nativo do Common Language Runtime (CLR) <xref:System.Type> representado por esse ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="98cc3-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98cc3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98cc3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98cc3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="98cc3-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="98cc3-106">fora Um ponteiro para um valor da enumeração `CorElementType` que indica o CLR <xref:System.Type> que esse `ICorDebugType` representa.</span><span class="sxs-lookup"><span data-stu-id="98cc3-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98cc3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="98cc3-107">Remarks</span></span>  
 <span data-ttu-id="98cc3-108">Se o valor de `ty` for ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, o método [ICorDebugType:: GetClass](icordebugtype-getclass-method.md) poderá ser chamado para obter o tipo não instanciado para um tipo genérico; caso contrário, não chame `ICorDebugType::GetClass`.</span><span class="sxs-lookup"><span data-stu-id="98cc3-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98cc3-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="98cc3-109">Requirements</span></span>  
 <span data-ttu-id="98cc3-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98cc3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98cc3-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98cc3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98cc3-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98cc3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98cc3-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98cc3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
