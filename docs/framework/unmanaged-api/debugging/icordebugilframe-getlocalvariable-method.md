---
title: "Método ICorDebugILFrame::GetLocalVariable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9694ee2e27d8789b661abc7393a480411c2b0191
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="9e9f2-102">Método ICorDebugILFrame::GetLocalVariable</span><span class="sxs-lookup"><span data-stu-id="9e9f2-102">ICorDebugILFrame::GetLocalVariable Method</span></span>
<span data-ttu-id="9e9f2-103">Obtém o valor da variável local especificada nesse quadro de pilha Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="9e9f2-103">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e9f2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e9f2-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e9f2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9e9f2-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="9e9f2-106">[in] O índice da variável local deste quadro de pilhas MSIL.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-106">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="9e9f2-107">[out] Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e9f2-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e9f2-108">Remarks</span></span>  
 <span data-ttu-id="9e9f2-109">O `GetLocalVariable` método pode ser usado em um quadro de pilha MSIL ou em um quadro compilado just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="9e9f2-109">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e9f2-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e9f2-110">Requirements</span></span>  
 <span data-ttu-id="9e9f2-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e9f2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e9f2-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e9f2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e9f2-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e9f2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e9f2-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e9f2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
