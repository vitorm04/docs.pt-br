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
ms.openlocfilehash: 6fd7694901534ad6897bbf78239081af6314e4bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="ac729-102">Método ICorDebugILFrame::EnumerateLocalVariables</span><span class="sxs-lookup"><span data-stu-id="ac729-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="ac729-103">Obtém um enumerador para as variáveis locais nesse quadro.</span><span class="sxs-lookup"><span data-stu-id="ac729-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac729-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac729-104">Syntax</span></span>  
  
```  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac729-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac729-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="ac729-106">[out] Um ponteiro para o endereço de um objeto de ICorDebugValueEnum que é o enumerador para as variáveis locais nesse quadro.</span><span class="sxs-lookup"><span data-stu-id="ac729-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac729-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac729-107">Remarks</span></span>  
 <span data-ttu-id="ac729-108">`EnumerateLocalVariables` Obtém um enumerador que pode listar as variáveis locais disponíveis no quadro de chamada que é representado pelo objeto ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="ac729-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="ac729-109">A lista pode não incluir todas as variáveis locais na função em execução, porque alguns deles não podem estar ativa.</span><span class="sxs-lookup"><span data-stu-id="ac729-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac729-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac729-110">Requirements</span></span>  
 <span data-ttu-id="ac729-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac729-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac729-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac729-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac729-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac729-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac729-114">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac729-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
