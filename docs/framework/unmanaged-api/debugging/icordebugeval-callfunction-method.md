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
ms.openlocfilehash: 86d48461c601b53d4461331a11a0e0ac7ddc6e7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412535"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="0e9c2-102">Método ICorDebugEval::CallFunction</span><span class="sxs-lookup"><span data-stu-id="0e9c2-102">ICorDebugEval::CallFunction Method</span></span>
<span data-ttu-id="0e9c2-103">Configura uma chamada para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="0e9c2-103">Sets up a call to the specified function.</span></span>  
  
 <span data-ttu-id="0e9c2-104">Este método está obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="0e9c2-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="0e9c2-105">Use [Icordebugeval2](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="0e9c2-105">Use [ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e9c2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e9c2-106">Syntax</span></span>  
  
```  
HRESULT CallFunction (  
    [in] ICorDebugFunction  *pFunction,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e9c2-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0e9c2-107">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="0e9c2-108">[in] Ponteiro para um objeto de ICorDebugFunction que especifica a função a ser chamado.</span><span class="sxs-lookup"><span data-stu-id="0e9c2-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="0e9c2-109">[in] O número de argumentos para a função.</span><span class="sxs-lookup"><span data-stu-id="0e9c2-109">[in] The number of arguments for the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="0e9c2-110">[in] Uma matriz de ponteiros, cada um deles aponta para um objeto de ICorDebugValue que especifica um argumento a ser passado para a função.</span><span class="sxs-lookup"><span data-stu-id="0e9c2-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e9c2-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="0e9c2-111">Remarks</span></span>  
 <span data-ttu-id="0e9c2-112">Se a função é virtual, `CallFunction` executará expedição virtual.</span><span class="sxs-lookup"><span data-stu-id="0e9c2-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="0e9c2-113">Se a função está em um domínio de aplicativo diferente, ocorrerá uma transição desde que todos os argumentos também estão no domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0e9c2-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e9c2-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0e9c2-114">Requirements</span></span>  
 <span data-ttu-id="0e9c2-115">**Plataformas:** WindowSee [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e9c2-115">**Platforms:** WindowSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e9c2-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e9c2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e9c2-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e9c2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e9c2-118">**Versões do .NET framework:** 1.1 e 1.0</span><span class="sxs-lookup"><span data-stu-id="0e9c2-118">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e9c2-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e9c2-119">See Also</span></span>  
 [<span data-ttu-id="0e9c2-120">Método CallParameterizedFunction</span><span class="sxs-lookup"><span data-stu-id="0e9c2-120">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)
