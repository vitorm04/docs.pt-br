---
title: "Método ICorDebugFunction::GetModule"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetModule
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetModule
helpviewer_keywords:
- ICorDebugFunction::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 5031a5d3-2564-412a-9007-e36d4631308a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 23c1cb74742f5ae2bc6bae22b2f94966f7dbc2f8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="d624d-102">Método ICorDebugFunction::GetModule</span><span class="sxs-lookup"><span data-stu-id="d624d-102">ICorDebugFunction::GetModule Method</span></span>
<span data-ttu-id="d624d-103">Obtém o módulo no qual a função é definida.</span><span class="sxs-lookup"><span data-stu-id="d624d-103">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d624d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d624d-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d624d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d624d-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="d624d-106">[out] Um ponteiro para o endereço de um objeto ICorDebugModule que representa o módulo no qual a função é definida.</span><span class="sxs-lookup"><span data-stu-id="d624d-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d624d-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d624d-107">Requirements</span></span>  
 <span data-ttu-id="d624d-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d624d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d624d-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d624d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d624d-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d624d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d624d-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d624d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
