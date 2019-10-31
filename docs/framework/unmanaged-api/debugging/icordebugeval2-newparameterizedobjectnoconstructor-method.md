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
ms.openlocfilehash: 770a9280d27c84b950e00e71328c9b28e61c9e7c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084802"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="2d458-102">Método ICorDebugEval2::NewParameterizedObjectNoConstructor</span><span class="sxs-lookup"><span data-stu-id="2d458-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>
<span data-ttu-id="2d458-103">Cria uma instância de um novo objeto de tipo com parâmetros da classe especificada sem tentar chamar um método de construtor.</span><span class="sxs-lookup"><span data-stu-id="2d458-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d458-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d458-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d458-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2d458-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="2d458-106">no Um ponteiro para um objeto ICorDebugClass que representa a classe do objeto a ser instanciado.</span><span class="sxs-lookup"><span data-stu-id="2d458-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="2d458-107">no O número de argumentos de tipo passado.</span><span class="sxs-lookup"><span data-stu-id="2d458-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="2d458-108">no Uma matriz de ponteiros, cada um dos quais aponta para um objeto ICorDebugType que representa um argumento de tipo para o objeto que está sendo instanciado.</span><span class="sxs-lookup"><span data-stu-id="2d458-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d458-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2d458-109">Remarks</span></span>  
 <span data-ttu-id="2d458-110">O método `NewParameterizedObjectNoConstructor` falhará se um número incorreto de argumentos de tipo ou os tipos incorretos de argumentos de tipo forem passados.</span><span class="sxs-lookup"><span data-stu-id="2d458-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d458-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2d458-111">Requirements</span></span>  
 <span data-ttu-id="2d458-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d458-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d458-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d458-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d458-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d458-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d458-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d458-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
