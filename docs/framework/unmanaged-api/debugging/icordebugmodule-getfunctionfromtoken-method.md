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
ms.openlocfilehash: cb966a918c63b4fbc00dcf52819b9384427dfdaa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129582"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="9c675-102">Método ICorDebugModule::GetFunctionFromToken</span><span class="sxs-lookup"><span data-stu-id="9c675-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="9c675-103">Obtém a função que é especificada pelo token de metadados.</span><span class="sxs-lookup"><span data-stu-id="9c675-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c675-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c675-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c675-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9c675-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="9c675-106">no Um `mdMethodDef` token de metadados que faz referência aos metadados da função.</span><span class="sxs-lookup"><span data-stu-id="9c675-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="9c675-107">fora Um ponteiro para o endereço de um objeto de interface ICorDebugFunction que representa a função.</span><span class="sxs-lookup"><span data-stu-id="9c675-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c675-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="9c675-108">Remarks</span></span>  
 <span data-ttu-id="9c675-109">O método `GetFunctionFromToken` retornará um HRESULT CORDBG_E_FUNCTION_NOT_IL se o valor passado em `methodDef` não se referir a um método MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="9c675-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c675-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9c675-110">Requirements</span></span>  
 <span data-ttu-id="9c675-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c675-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c675-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c675-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c675-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c675-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c675-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c675-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
