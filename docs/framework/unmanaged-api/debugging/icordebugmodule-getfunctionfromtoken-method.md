---
title: Método ICorDebugModule::GetFunctionFromToken
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acffd24ae9d5aad5f48058eec036f912ee016289
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="fb667-102">Método ICorDebugModule::GetFunctionFromToken</span><span class="sxs-lookup"><span data-stu-id="fb667-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="fb667-103">Obtém a função que é especificada pelo token de metadados.</span><span class="sxs-lookup"><span data-stu-id="fb667-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb667-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb667-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb667-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fb667-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="fb667-106">[in] Um `mdMethodDef` token de metadados que faz referência a metadados de função.</span><span class="sxs-lookup"><span data-stu-id="fb667-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="fb667-107">[out] Um ponteiro para o endereço de um objeto de interface ICorDebugFunction que representa a função.</span><span class="sxs-lookup"><span data-stu-id="fb667-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb667-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb667-108">Remarks</span></span>  
 <span data-ttu-id="fb667-109">O `GetFunctionFromToken` método retorna um HRESULT CORDBG_E_FUNCTION_NOT_IL se o valor passado no `methodDef` não se refere a um método do Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="fb667-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb667-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb667-110">Requirements</span></span>  
 <span data-ttu-id="fb667-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb667-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb667-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb667-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb667-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb667-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb667-114">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb667-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
