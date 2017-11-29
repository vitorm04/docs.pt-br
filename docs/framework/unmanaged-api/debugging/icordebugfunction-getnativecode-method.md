---
title: "Método ICorDebugFunction::GetNativeCode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetNativeCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2fccfaeb346d59f5cf565f47a9a64e732706adad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="d0647-102">Método ICorDebugFunction::GetNativeCode</span><span class="sxs-lookup"><span data-stu-id="d0647-102">ICorDebugFunction::GetNativeCode Method</span></span>
<span data-ttu-id="d0647-103">Obtém o código nativo para a função que é representada por esta instância de ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="d0647-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0647-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0647-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0647-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d0647-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="d0647-106">[out] Um ponteiro para a instância de ICorDebugCode que representa o código nativo para essa função, ou nulo, se essa função é o código do Microsoft intermediate language (MSIL) que não tenha sido just-in-time (JIT) compilado.</span><span class="sxs-lookup"><span data-stu-id="d0647-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0647-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0647-107">Remarks</span></span>  
 <span data-ttu-id="d0647-108">Se a função que é representada por esse `ICorDebugFunction` instância foi compilada por JIT mais de uma vez, como no caso de tipos genéricos, `GetNativeCode` retorna um objeto aleatório de código nativo.</span><span class="sxs-lookup"><span data-stu-id="d0647-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0647-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d0647-109">Requirements</span></span>  
 <span data-ttu-id="d0647-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0647-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0647-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0647-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0647-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0647-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0647-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0647-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
