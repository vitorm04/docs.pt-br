---
title: "Método ICorDebugEval2::CallParameterizedFunction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.CallParameterizedFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 055ded7f3309ff1011d1ca390daf353cba870376
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2callparameterizedfunction-method"></a><span data-ttu-id="c28d3-102">Método ICorDebugEval2::CallParameterizedFunction</span><span class="sxs-lookup"><span data-stu-id="c28d3-102">ICorDebugEval2::CallParameterizedFunction Method</span></span>
<span data-ttu-id="c28d3-103">Configura uma chamada para o ICorDebugFunction especificado, que pode ser aninhado dentro de uma classe cujo construtor obtém <xref:System.Type> parâmetros, ou podem ser próprio levar <xref:System.Type> parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c28d3-103">Sets up a call to the specified ICorDebugFunction, which can be nested inside a class whose constructor takes <xref:System.Type> parameters, or can itself take <xref:System.Type> parameters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c28d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c28d3-104">Syntax</span></span>  
  
```  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c28d3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c28d3-105">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="c28d3-106">[in] Um ponteiro para um `ICorDebugFunction` objeto que representa a função a ser chamado.</span><span class="sxs-lookup"><span data-stu-id="c28d3-106">[in] A pointer to an `ICorDebugFunction` object that represents the function to be called.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="c28d3-107">[in] O número de argumentos que usa a função.</span><span class="sxs-lookup"><span data-stu-id="c28d3-107">[in] The number of arguments that the function takes.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="c28d3-108">[in] Uma matriz de ponteiros, cada um deles aponta para um objeto ICorDebugType que representa um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="c28d3-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a function argument.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="c28d3-109">[in] O número de valores passados na função.</span><span class="sxs-lookup"><span data-stu-id="c28d3-109">[in] The number of values passed in the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="c28d3-110">[in] Uma matriz de ponteiros, cada um deles aponta para um objeto ICorDebugValue que representa um valor passado um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="c28d3-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents a value passed in a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c28d3-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="c28d3-111">Remarks</span></span>  
 <span data-ttu-id="c28d3-112">`CallParameterizedFunction`é como [: CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) exceto que a função pode ser dentro de uma classe com parâmetros de tipo, se levará de parâmetros de tipo, ou ambos.</span><span class="sxs-lookup"><span data-stu-id="c28d3-112">`CallParameterizedFunction` is like [ICorDebugEval::CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) except that the function may be inside a class with type parameters, may itself take type parameters, or both.</span></span> <span data-ttu-id="c28d3-113">Os argumentos de tipo devem ser fornecidos pela primeira vez para a classe e, em seguida, para a função.</span><span class="sxs-lookup"><span data-stu-id="c28d3-113">The type arguments should be given first for the class, and then for the function.</span></span>  
  
 <span data-ttu-id="c28d3-114">Se a função está em um domínio de aplicativo diferente, ocorrerá uma transição.</span><span class="sxs-lookup"><span data-stu-id="c28d3-114">If the function is in a different application domain, a transition will occur.</span></span> <span data-ttu-id="c28d3-115">No entanto, todos os argumentos de tipo e o valor devem ser no domínio de aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="c28d3-115">However, all type and value arguments must be in the target application domain.</span></span>  
  
 <span data-ttu-id="c28d3-116">Avaliação de função pode ser executada somente em cenários limitados.</span><span class="sxs-lookup"><span data-stu-id="c28d3-116">Function evaluation can be performed only in limited scenarios.</span></span> <span data-ttu-id="c28d3-117">Se `CallParameterizedFunction` ou `ICorDebugEval::CallFunction` falhar, o HRESULT retornado indicará o mais geral possível motivo da falha.</span><span class="sxs-lookup"><span data-stu-id="c28d3-117">If `CallParameterizedFunction` or `ICorDebugEval::CallFunction` fails, the returned HRESULT will indicate the most general possible reason for failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c28d3-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c28d3-118">Requirements</span></span>  
 <span data-ttu-id="c28d3-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c28d3-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c28d3-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c28d3-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c28d3-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c28d3-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c28d3-122">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c28d3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
