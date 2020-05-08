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
ms.openlocfilehash: 1cf0080945ad78565fae3fedb454ceba7825cb4a
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976233"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="7e2ca-102">Método ICorDebugEval::CallFunction</span><span class="sxs-lookup"><span data-stu-id="7e2ca-102">ICorDebugEval::CallFunction Method</span></span>

<span data-ttu-id="7e2ca-103">Define uma chamada para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="7e2ca-103">Sets up a call to the specified function.</span></span>

<span data-ttu-id="7e2ca-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="7e2ca-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="7e2ca-105">Use [ICorDebugEval2:: CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="7e2ca-105">Use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="7e2ca-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e2ca-106">Syntax</span></span>

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a><span data-ttu-id="7e2ca-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7e2ca-107">Parameters</span></span>

`pFunction`\
<span data-ttu-id="7e2ca-108">no Ponteiro para um objeto ICorDebugFunction que especifica a função a ser chamada.</span><span class="sxs-lookup"><span data-stu-id="7e2ca-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>

`nArgs`\
<span data-ttu-id="7e2ca-109">no O número de argumentos para a função.</span><span class="sxs-lookup"><span data-stu-id="7e2ca-109">[in] The number of arguments for the function.</span></span>

`ppArgs`\
<span data-ttu-id="7e2ca-110">no Uma matriz de ponteiros, cada um dos quais aponta para um objeto ICorDebugValue que especifica um argumento a ser passado para a função.</span><span class="sxs-lookup"><span data-stu-id="7e2ca-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="7e2ca-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="7e2ca-111">Remarks</span></span>

<span data-ttu-id="7e2ca-112">Se a função for virtual, `CallFunction` executará o despacho virtual.</span><span class="sxs-lookup"><span data-stu-id="7e2ca-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="7e2ca-113">Se a função estiver em um domínio de aplicativo diferente, uma transição ocorrerá contanto que todos os argumentos também estejam nesse domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7e2ca-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>

## <a name="requirements"></a><span data-ttu-id="7e2ca-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e2ca-114">Requirements</span></span>

<span data-ttu-id="7e2ca-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e2ca-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="7e2ca-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e2ca-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="7e2ca-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e2ca-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="7e2ca-118">**Versões do .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="7e2ca-118">**.NET Framework Versions:** 1.1, 1.0</span></span>

## <a name="see-also"></a><span data-ttu-id="7e2ca-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e2ca-119">See also</span></span>

- [<span data-ttu-id="7e2ca-120">Método CallParameterizedFunction</span><span class="sxs-lookup"><span data-stu-id="7e2ca-120">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)
