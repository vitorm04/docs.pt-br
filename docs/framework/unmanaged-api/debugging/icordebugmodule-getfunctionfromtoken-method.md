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
ms.openlocfilehash: a33b6ff308f3444496e5a1cb2e04f28e80305db5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212571"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="4fb03-102">Método ICorDebugModule::GetFunctionFromToken</span><span class="sxs-lookup"><span data-stu-id="4fb03-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="4fb03-103">Obtém a função que é especificada pelo token de metadados.</span><span class="sxs-lookup"><span data-stu-id="4fb03-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fb03-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4fb03-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fb03-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4fb03-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="4fb03-106">no Um `mdMethodDef` token de metadados que faz referência aos metadados da função.</span><span class="sxs-lookup"><span data-stu-id="4fb03-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="4fb03-107">fora Um ponteiro para o endereço de um objeto de interface ICorDebugFunction que representa a função.</span><span class="sxs-lookup"><span data-stu-id="4fb03-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fb03-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="4fb03-108">Remarks</span></span>  
 <span data-ttu-id="4fb03-109">O `GetFunctionFromToken` método retornará um CORDBG_E_FUNCTION_NOT_IL HRESULT se o valor passado `methodDef` não se referir a um método MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="4fb03-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fb03-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4fb03-110">Requirements</span></span>  
 <span data-ttu-id="4fb03-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fb03-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fb03-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4fb03-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fb03-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fb03-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fb03-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fb03-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
