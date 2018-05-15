---
title: Método ICorDebugILFrame::GetLocalVariable
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetLocalVariable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3424646337c3f90f15d991f3f669a296bf11d8ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="5a65f-102">Método ICorDebugILFrame::GetLocalVariable</span><span class="sxs-lookup"><span data-stu-id="5a65f-102">ICorDebugILFrame::GetLocalVariable Method</span></span>
<span data-ttu-id="5a65f-103">Obtém o valor da variável local especificada nesse quadro de pilha Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="5a65f-103">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a65f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a65f-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a65f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5a65f-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="5a65f-106">[in] O índice da variável local deste quadro de pilhas MSIL.</span><span class="sxs-lookup"><span data-stu-id="5a65f-106">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="5a65f-107">[out] Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="5a65f-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a65f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="5a65f-108">Remarks</span></span>  
 <span data-ttu-id="5a65f-109">O `GetLocalVariable` método pode ser usado em um quadro de pilha MSIL ou em um quadro compilado just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="5a65f-109">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a65f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5a65f-110">Requirements</span></span>  
 <span data-ttu-id="5a65f-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a65f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a65f-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a65f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a65f-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a65f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a65f-114">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a65f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
