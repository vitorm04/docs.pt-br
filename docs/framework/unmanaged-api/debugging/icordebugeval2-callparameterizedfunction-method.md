---
title: Método ICorDebugEval2::CallParameterizedFunction
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CallParameterizedFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type:
- apiref
ms.openlocfilehash: b521c96d26202119dad6fedb61cbd9da8b3c2e52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137633"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a><span data-ttu-id="dc1b2-102">Método ICorDebugEval2::CallParameterizedFunction</span><span class="sxs-lookup"><span data-stu-id="dc1b2-102">ICorDebugEval2::CallParameterizedFunction Method</span></span>
<span data-ttu-id="dc1b2-103">Define uma chamada para o ICorDebugFunction especificado, que pode ser aninhado dentro de uma classe cujo construtor usa <xref:System.Type> parâmetros ou pode levar <xref:System.Type> parâmetros.</span><span class="sxs-lookup"><span data-stu-id="dc1b2-103">Sets up a call to the specified ICorDebugFunction, which can be nested inside a class whose constructor takes <xref:System.Type> parameters, or can itself take <xref:System.Type> parameters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc1b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dc1b2-104">Syntax</span></span>  
  
```cpp  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc1b2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc1b2-105">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="dc1b2-106">no Um ponteiro para um objeto `ICorDebugFunction` que representa a função a ser chamada.</span><span class="sxs-lookup"><span data-stu-id="dc1b2-106">[in] A pointer to an `ICorDebugFunction` object that represents the function to be called.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="dc1b2-107">no O número de argumentos que a função usa.</span><span class="sxs-lookup"><span data-stu-id="dc1b2-107">[in] The number of arguments that the function takes.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="dc1b2-108">no Uma matriz de ponteiros, cada um dos quais aponta para um objeto ICorDebugType que representa um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="dc1b2-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a function argument.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="dc1b2-109">no O número de valores passados na função.</span><span class="sxs-lookup"><span data-stu-id="dc1b2-109">[in] The number of values passed in the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="dc1b2-110">no Uma matriz de ponteiros, cada um dos quais aponta para um objeto ICorDebugValue que representa um valor passado em um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="dc1b2-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents a value passed in a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc1b2-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="dc1b2-111">Remarks</span></span>  
 <span data-ttu-id="dc1b2-112">`CallParameterizedFunction` é como [ICorDebugEval:: CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) , exceto que a função pode estar dentro de uma classe com parâmetros de tipo, ela própria pode pegar parâmetros de tipo ou ambos.</span><span class="sxs-lookup"><span data-stu-id="dc1b2-112">`CallParameterizedFunction` is like [ICorDebugEval::CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) except that the function may be inside a class with type parameters, may itself take type parameters, or both.</span></span> <span data-ttu-id="dc1b2-113">Os argumentos de tipo devem ser fornecidos primeiro para a classe e, em seguida, para a função.</span><span class="sxs-lookup"><span data-stu-id="dc1b2-113">The type arguments should be given first for the class, and then for the function.</span></span>  
  
 <span data-ttu-id="dc1b2-114">Se a função estiver em um domínio de aplicativo diferente, ocorrerá uma transição.</span><span class="sxs-lookup"><span data-stu-id="dc1b2-114">If the function is in a different application domain, a transition will occur.</span></span> <span data-ttu-id="dc1b2-115">No entanto, todos os argumentos Type e Value devem estar no domínio do aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="dc1b2-115">However, all type and value arguments must be in the target application domain.</span></span>  
  
 <span data-ttu-id="dc1b2-116">A avaliação de função pode ser executada somente em cenários limitados.</span><span class="sxs-lookup"><span data-stu-id="dc1b2-116">Function evaluation can be performed only in limited scenarios.</span></span> <span data-ttu-id="dc1b2-117">Se `CallParameterizedFunction` ou `ICorDebugEval::CallFunction` falhar, o HRESULT retornado indicará o motivo mais geral possível para a falha.</span><span class="sxs-lookup"><span data-stu-id="dc1b2-117">If `CallParameterizedFunction` or `ICorDebugEval::CallFunction` fails, the returned HRESULT will indicate the most general possible reason for failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc1b2-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dc1b2-118">Requirements</span></span>  
 <span data-ttu-id="dc1b2-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc1b2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc1b2-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc1b2-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc1b2-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc1b2-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc1b2-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc1b2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
