---
title: Método ICorDebugEval2::CreateValueForType
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
ms.openlocfilehash: 8632799b68ae8f92835d1774472bc1432d886f3b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793478"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="c0b2f-102">Método ICorDebugEval2::CreateValueForType</span><span class="sxs-lookup"><span data-stu-id="c0b2f-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="c0b2f-103">Obtém um ponteiro para um novo ICorDebugValue do tipo especificado, com um valor inicial de zero ou NULL.</span><span class="sxs-lookup"><span data-stu-id="c0b2f-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0b2f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0b2f-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0b2f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c0b2f-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="c0b2f-106">no Ponteiro para um objeto ICorDebugType que representa o tipo.</span><span class="sxs-lookup"><span data-stu-id="c0b2f-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c0b2f-107">fora Ponteiro para o endereço de um objeto de `ICorDebugValue` que representa o valor.</span><span class="sxs-lookup"><span data-stu-id="c0b2f-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0b2f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c0b2f-108">Remarks</span></span>  
 <span data-ttu-id="c0b2f-109">`CreateValueForType` generaliza [ICorDebugEval:: CreateValue](icordebugeval-createvalue-method.md) permitindo que você especifique um tipo de objeto arbitrário, incluindo tipos construídos, como `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="c0b2f-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="c0b2f-110">A única finalidade desse método é gerar um valor que possa ser passado para uma avaliação de função.</span><span class="sxs-lookup"><span data-stu-id="c0b2f-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="c0b2f-111">O tipo deve ser uma classe ou um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="c0b2f-111">The type must be a class or a value type.</span></span> <span data-ttu-id="c0b2f-112">Você não pode usar esse método para criar valores de matriz ou de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c0b2f-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0b2f-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="c0b2f-113">Requirements</span></span>  
 <span data-ttu-id="c0b2f-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0b2f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0b2f-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0b2f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0b2f-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0b2f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0b2f-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0b2f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
