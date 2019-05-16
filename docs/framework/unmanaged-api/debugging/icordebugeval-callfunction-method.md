---
title: Método ICorDebugEval::CallFunction
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65225281fe3abaa20e69e96f4cd4d2a4b03a87ce
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629936"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="fc36e-102">Método ICorDebugEval::CallFunction</span><span class="sxs-lookup"><span data-stu-id="fc36e-102">ICorDebugEval::CallFunction Method</span></span>

<span data-ttu-id="fc36e-103">Define uma chamada para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="fc36e-103">Sets up a call to the specified function.</span></span>

<span data-ttu-id="fc36e-104">Este método é obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="fc36e-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="fc36e-105">Use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="fc36e-105">Use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="fc36e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc36e-106">Syntax</span></span>

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a><span data-ttu-id="fc36e-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fc36e-107">Parameters</span></span>

`pFunction`\
<span data-ttu-id="fc36e-108">[in] Ponteiro para um objeto de ICorDebugFunction que especifica a função a ser chamado.</span><span class="sxs-lookup"><span data-stu-id="fc36e-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>

`nArgs`\
<span data-ttu-id="fc36e-109">[in] O número de argumentos da função.</span><span class="sxs-lookup"><span data-stu-id="fc36e-109">[in] The number of arguments for the function.</span></span>

`ppArgs`\
<span data-ttu-id="fc36e-110">[in] Uma matriz de ponteiros, cada um deles aponta para um objeto de ICorDebugValue que especifica um argumento a ser passado para a função.</span><span class="sxs-lookup"><span data-stu-id="fc36e-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc36e-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="fc36e-111">Remarks</span></span>

<span data-ttu-id="fc36e-112">Se a função é virtual, `CallFunction` executará a expedição virtual.</span><span class="sxs-lookup"><span data-stu-id="fc36e-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="fc36e-113">Se a função está em um domínio de aplicativo diferente, uma transição ocorrerá desde que todos os argumentos também estão no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fc36e-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>

## <a name="requirements"></a><span data-ttu-id="fc36e-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc36e-114">Requirements</span></span>

<span data-ttu-id="fc36e-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc36e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="fc36e-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc36e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="fc36e-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc36e-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="fc36e-118">**Versões do .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="fc36e-118">**.NET Framework Versions:** 1.1, 1.0</span></span>

## <a name="see-also"></a><span data-ttu-id="fc36e-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc36e-119">See also</span></span>

- [<span data-ttu-id="fc36e-120">Método CallParameterizedFunction</span><span class="sxs-lookup"><span data-stu-id="fc36e-120">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)
