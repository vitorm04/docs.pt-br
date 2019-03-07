---
title: Método ICorDebugILFrame::GetArgument
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46852ed8ac53c3a7720edff4833f3dc3cce42bbb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475782"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="e14ba-102">Método ICorDebugILFrame::GetArgument</span><span class="sxs-lookup"><span data-stu-id="e14ba-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="e14ba-103">Obtém o valor do argumento especificado neste quadro de pilha Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="e14ba-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e14ba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e14ba-104">Syntax</span></span>  
  
```  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e14ba-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e14ba-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="e14ba-106">[in] O índice do argumento deste quadro de pilhas MSIL.</span><span class="sxs-lookup"><span data-stu-id="e14ba-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="e14ba-107">[out] Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor recuperado.</span><span class="sxs-lookup"><span data-stu-id="e14ba-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e14ba-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="e14ba-108">Remarks</span></span>  
 <span data-ttu-id="e14ba-109">O `GetArgument` método pode ser usado em um quadro de pilha MSIL ou em um quadro de compilado just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="e14ba-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e14ba-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e14ba-110">Requirements</span></span>  
 <span data-ttu-id="e14ba-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e14ba-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e14ba-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e14ba-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e14ba-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e14ba-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e14ba-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e14ba-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
