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
ms.openlocfilehash: e32ce10b708afa5741d83cbd05f14accb4b2014f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754672"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="5e4bd-102">Método ICorDebugFunction::GetILCode</span><span class="sxs-lookup"><span data-stu-id="5e4bd-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="5e4bd-103">Obtém a instância de ICorDebugCode que representa o código do Microsoft intermediate language (MSIL) associado a este objeto ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="5e4bd-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e4bd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e4bd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e4bd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5e4bd-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="5e4bd-106">[out] Um ponteiro para o `ICorDebugCode` da instância ou nulo, se a função não foi compilada em MSIL.</span><span class="sxs-lookup"><span data-stu-id="5e4bd-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e4bd-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5e4bd-107">Remarks</span></span>  
 <span data-ttu-id="5e4bd-108">Se editar e continuar foi permitido nesta função, o `GetILCode` método obterá o código MSIL correspondente à versão editada dessa função do código no common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="5e4bd-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e4bd-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5e4bd-109">Requirements</span></span>  
 <span data-ttu-id="5e4bd-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e4bd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e4bd-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e4bd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e4bd-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e4bd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e4bd-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e4bd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
