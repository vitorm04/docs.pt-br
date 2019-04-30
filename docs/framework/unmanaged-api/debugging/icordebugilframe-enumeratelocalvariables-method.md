---
title: Método ICorDebugILFrame::EnumerateLocalVariables
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cc9601105d05740e6db0a41bae521bd9a276d74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988644"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="6226c-102">Método ICorDebugILFrame::EnumerateLocalVariables</span><span class="sxs-lookup"><span data-stu-id="6226c-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="6226c-103">Obtém um enumerador para as variáveis locais neste quadro.</span><span class="sxs-lookup"><span data-stu-id="6226c-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6226c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6226c-104">Syntax</span></span>  
  
```  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6226c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6226c-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="6226c-106">[out] Um ponteiro para o endereço de um objeto ICorDebugValueEnum que é o enumerador para as variáveis locais neste quadro.</span><span class="sxs-lookup"><span data-stu-id="6226c-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6226c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="6226c-107">Remarks</span></span>  
 <span data-ttu-id="6226c-108">`EnumerateLocalVariables` Obtém um enumerador que pode listar as variáveis locais disponíveis no quadro de chamada que é representado por esse objeto ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="6226c-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="6226c-109">A lista pode não incluir todas as variáveis locais na função em execução, porque alguns deles podem não estar ativas.</span><span class="sxs-lookup"><span data-stu-id="6226c-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6226c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6226c-110">Requirements</span></span>  
 <span data-ttu-id="6226c-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6226c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6226c-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6226c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6226c-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6226c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6226c-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6226c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
