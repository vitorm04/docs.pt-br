---
title: "Método ICorDebugFunction::GetILCode"
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
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ba960246c5aa1057df517d776819817d777402f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="4424f-102">Método ICorDebugFunction::GetILCode</span><span class="sxs-lookup"><span data-stu-id="4424f-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="4424f-103">Obtém a instância de ICorDebugCode que representa o código do Microsoft intermediate language (MSIL) associado ao objeto ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="4424f-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4424f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4424f-104">Syntax</span></span>  
  
```  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4424f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4424f-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="4424f-106">[out] Um ponteiro para a `ICorDebugCode` instância ou nulo, se a função não foi compilada na MSIL.</span><span class="sxs-lookup"><span data-stu-id="4424f-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4424f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4424f-107">Remarks</span></span>  
 <span data-ttu-id="4424f-108">Se editar e continuar foi permitido nesta função, o `GetILCode` método receberá o código MSIL correspondente para a versão editada desta função de código no common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="4424f-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4424f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4424f-109">Requirements</span></span>  
 <span data-ttu-id="4424f-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4424f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4424f-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4424f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4424f-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4424f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4424f-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4424f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
