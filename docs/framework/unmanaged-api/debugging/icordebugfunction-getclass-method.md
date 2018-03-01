---
title: "Método ICorDebugFunction::GetClass"
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
- ICorDebugFunction.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetClass
helpviewer_keywords:
- GetClass method, ICorDebugFunction interface [.NET Framework debugging]
- ICorDebugFunction::GetClass method [.NET Framework debugging]
ms.assetid: 27967230-144f-40d3-9e23-961d0241abd9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4607b5c71311eeccc9df778a45ca30a305b90aa9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="f9a4b-102">Método ICorDebugFunction::GetClass</span><span class="sxs-lookup"><span data-stu-id="f9a4b-102">ICorDebugFunction::GetClass Method</span></span>
<span data-ttu-id="f9a4b-103">Obtém um objeto ICorDebugClass que representa essa função é um membro da classe.</span><span class="sxs-lookup"><span data-stu-id="f9a4b-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9a4b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9a4b-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9a4b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f9a4b-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="f9a4b-106">[out] Um ponteiro para o endereço do `ICorDebugClass` objeto que representa a classe, ou nulo, se essa função não é um membro de uma classe.</span><span class="sxs-lookup"><span data-stu-id="f9a4b-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9a4b-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f9a4b-107">Requirements</span></span>  
 <span data-ttu-id="f9a4b-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9a4b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9a4b-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9a4b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9a4b-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9a4b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9a4b-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9a4b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
