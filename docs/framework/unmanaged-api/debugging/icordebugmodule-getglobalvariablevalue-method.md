---
title: Método ICorDebugModule::GetGlobalVariableValue
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetGlobalVariableValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetGlobalVariableValue
helpviewer_keywords:
- ICorDebugModule::GetGlobalVariableValue method [.NET Framework debugging]
- GetGlobalVariableValue method [.NET Framework debugging]
ms.assetid: bbc0881c-6a59-41a0-b5ee-2f3d1b71684c
topic_type:
- apiref
ms.openlocfilehash: 7e32f3f4f6613d34e2b40946ed3eadb8eb0a7c1f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212562"
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a><span data-ttu-id="98684-102">Método ICorDebugModule::GetGlobalVariableValue</span><span class="sxs-lookup"><span data-stu-id="98684-102">ICorDebugModule::GetGlobalVariableValue Method</span></span>
<span data-ttu-id="98684-103">Obtém o valor da variável global especificada.</span><span class="sxs-lookup"><span data-stu-id="98684-103">Gets the value of the specified global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98684-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98684-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98684-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="98684-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="98684-106">no Um `mdFieldDef` token que faz referência aos metadados que descrevem a variável global.</span><span class="sxs-lookup"><span data-stu-id="98684-106">[in] An `mdFieldDef` token that references the metadata describing the global variable.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="98684-107">fora Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor da variável global especificada.</span><span class="sxs-lookup"><span data-stu-id="98684-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified global variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98684-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="98684-108">Requirements</span></span>  
 <span data-ttu-id="98684-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98684-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98684-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98684-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98684-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98684-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98684-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98684-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
