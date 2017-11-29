---
title: "Método ICorDebugILFrame::EnumerateLocalVariables"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.EnumerateLocalVariables
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fb4e6bead1bb4933f8f9af4ffb1bfb9157a028c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="c3521-102">Método ICorDebugILFrame::EnumerateLocalVariables</span><span class="sxs-lookup"><span data-stu-id="c3521-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="c3521-103">Obtém um enumerador para as variáveis locais nesse quadro.</span><span class="sxs-lookup"><span data-stu-id="c3521-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3521-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3521-104">Syntax</span></span>  
  
```  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3521-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3521-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="c3521-106">[out] Um ponteiro para o endereço de um objeto de ICorDebugValueEnum que é o enumerador para as variáveis locais nesse quadro.</span><span class="sxs-lookup"><span data-stu-id="c3521-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3521-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3521-107">Remarks</span></span>  
 <span data-ttu-id="c3521-108">`EnumerateLocalVariables`Obtém um enumerador que pode listar as variáveis locais disponíveis no quadro de chamada que é representado pelo objeto ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="c3521-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="c3521-109">A lista pode não incluir todas as variáveis locais na função em execução, porque alguns deles não podem estar ativa.</span><span class="sxs-lookup"><span data-stu-id="c3521-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3521-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3521-110">Requirements</span></span>  
 <span data-ttu-id="c3521-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3521-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3521-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3521-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3521-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3521-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3521-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3521-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
