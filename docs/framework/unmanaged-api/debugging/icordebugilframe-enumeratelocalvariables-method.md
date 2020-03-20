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
ms.openlocfilehash: c071a7ddb7d8d3f0e6487ab85284c45f9a7f0372
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178840"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="f4e10-102">Método ICorDebugILFrame::EnumerateLocalVariables</span><span class="sxs-lookup"><span data-stu-id="f4e10-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="f4e10-103">Obtém um enumerador para as variáveis locais neste quadro.</span><span class="sxs-lookup"><span data-stu-id="f4e10-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4e10-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f4e10-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLocalVariables(
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4e10-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4e10-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="f4e10-106">[out] Um ponteiro para o endereço de um objeto ICorDebugValueEnum que é o enumerador das variáveis locais neste quadro.</span><span class="sxs-lookup"><span data-stu-id="f4e10-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4e10-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f4e10-107">Remarks</span></span>  
 <span data-ttu-id="f4e10-108">`EnumerateLocalVariables`obtém um enumerador que pode listar as variáveis locais disponíveis no quadro de chamadas que é representado por este objeto ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="f4e10-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="f4e10-109">A lista pode não incluir todas as variáveis locais na função em execução, porque algumas delas podem não estar ativas.</span><span class="sxs-lookup"><span data-stu-id="f4e10-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4e10-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4e10-110">Requirements</span></span>  
 <span data-ttu-id="f4e10-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4e10-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4e10-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4e10-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4e10-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4e10-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4e10-114">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4e10-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
