---
title: Método ICorDebugFunction::GetILCode
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac34fbca56c8a0f00ee3a7e0f898b8ee03287b11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="67842-102">Método ICorDebugFunction::GetILCode</span><span class="sxs-lookup"><span data-stu-id="67842-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="67842-103">Obtém a instância de ICorDebugCode que representa o código do Microsoft intermediate language (MSIL) associado ao objeto ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="67842-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67842-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="67842-104">Syntax</span></span>  
  
```  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67842-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="67842-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="67842-106">[out] Um ponteiro para a `ICorDebugCode` instância ou nulo, se a função não foi compilada na MSIL.</span><span class="sxs-lookup"><span data-stu-id="67842-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67842-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="67842-107">Remarks</span></span>  
 <span data-ttu-id="67842-108">Se editar e continuar foi permitido nesta função, o `GetILCode` método receberá o código MSIL correspondente para a versão editada desta função de código no common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="67842-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67842-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="67842-109">Requirements</span></span>  
 <span data-ttu-id="67842-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67842-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67842-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67842-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67842-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67842-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67842-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67842-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
