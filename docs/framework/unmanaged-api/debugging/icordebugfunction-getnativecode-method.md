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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb85c4b2c26c136a5f9fc05221a42c4bc99f37f9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470166"
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="3e2e0-102">Método ICorDebugFunction::GetNativeCode</span><span class="sxs-lookup"><span data-stu-id="3e2e0-102">ICorDebugFunction::GetNativeCode Method</span></span>
<span data-ttu-id="3e2e0-103">Obtém o código nativo para a função que é representada por esta instância de ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="3e2e0-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e2e0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e2e0-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e2e0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3e2e0-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="3e2e0-106">[out] Um ponteiro para a instância de ICorDebugCode que representa o código nativo para essa função, ou nulo, se essa função é o código do Microsoft intermediate language (MSIL) que não tenha sido just-in-time (JIT) compilado.</span><span class="sxs-lookup"><span data-stu-id="3e2e0-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e2e0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e2e0-107">Remarks</span></span>  
 <span data-ttu-id="3e2e0-108">Se a função que é representada por esse `ICorDebugFunction` instância tiver sido compilado por JIT mais de uma vez, como no caso de tipos genéricos, `GetNativeCode` retorna um objeto aleatório de código nativo.</span><span class="sxs-lookup"><span data-stu-id="3e2e0-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e2e0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3e2e0-109">Requirements</span></span>  
 <span data-ttu-id="3e2e0-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e2e0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e2e0-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e2e0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e2e0-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e2e0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e2e0-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e2e0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
