---
title: Método ICorDebugEval2::NewParameterizedObjectNoConstructor
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6feef7b1e1f09107cd2a57555df07bebec86effa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667022"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="fb6ff-102">Método ICorDebugEval2::NewParameterizedObjectNoConstructor</span><span class="sxs-lookup"><span data-stu-id="fb6ff-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>
<span data-ttu-id="fb6ff-103">Cria uma instância de um novo objeto de tipo parametrizado da classe especificada sem tentar chamar um método de construtor.</span><span class="sxs-lookup"><span data-stu-id="fb6ff-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb6ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb6ff-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb6ff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fb6ff-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="fb6ff-106">[in] Um ponteiro para um objeto ICorDebugClass que representa a classe do objeto a ser instanciado.</span><span class="sxs-lookup"><span data-stu-id="fb6ff-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="fb6ff-107">[in] O número de argumentos de tipo passado.</span><span class="sxs-lookup"><span data-stu-id="fb6ff-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="fb6ff-108">[in] Uma matriz de ponteiros, cada um deles aponta para um objeto de ICorDebugType que representa um argumento de tipo para o objeto de instância está sendo criado.</span><span class="sxs-lookup"><span data-stu-id="fb6ff-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb6ff-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb6ff-109">Remarks</span></span>  
 <span data-ttu-id="fb6ff-110">O `NewParameterizedObjectNoConstructor` método irá falhar se um número incorreto de argumentos de tipo ou os tipos de errado de argumentos de tipo são passados.</span><span class="sxs-lookup"><span data-stu-id="fb6ff-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb6ff-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb6ff-111">Requirements</span></span>  
 <span data-ttu-id="fb6ff-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb6ff-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb6ff-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb6ff-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb6ff-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb6ff-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb6ff-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb6ff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
