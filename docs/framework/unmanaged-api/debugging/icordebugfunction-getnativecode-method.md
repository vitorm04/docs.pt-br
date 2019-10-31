---
title: Método ICorDebugFunction::GetNativeCode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
ms.openlocfilehash: 5bb41b2b49922475550997f18832b391522e2f26
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137866"
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="e7fd0-102">Método ICorDebugFunction::GetNativeCode</span><span class="sxs-lookup"><span data-stu-id="e7fd0-102">ICorDebugFunction::GetNativeCode Method</span></span>
<span data-ttu-id="e7fd0-103">Obtém o código nativo para a função que é representada por essa instância de ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="e7fd0-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7fd0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e7fd0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7fd0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e7fd0-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="e7fd0-106">fora Um ponteiro para a instância ICorDebugCode que representa o código nativo para essa função, ou NULL, se essa função for um código MSIL (Microsoft Intermediate Language) que não tenha sido compilado JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="e7fd0-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7fd0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e7fd0-107">Remarks</span></span>  
 <span data-ttu-id="e7fd0-108">Se a função representada por essa instância de `ICorDebugFunction` tiver sido compilada por JIT mais de uma vez, como no caso de tipos genéricos, `GetNativeCode` retornará um objeto de código nativo aleatório.</span><span class="sxs-lookup"><span data-stu-id="e7fd0-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7fd0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e7fd0-109">Requirements</span></span>  
 <span data-ttu-id="e7fd0-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7fd0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7fd0-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7fd0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7fd0-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7fd0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7fd0-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7fd0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
