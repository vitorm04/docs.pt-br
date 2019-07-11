---
title: Método ICorDebugFunction::GetClass
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 218818097846709ec92e20f33a0707314edd562a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754733"
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="f4516-102">Método ICorDebugFunction::GetClass</span><span class="sxs-lookup"><span data-stu-id="f4516-102">ICorDebugFunction::GetClass Method</span></span>
<span data-ttu-id="f4516-103">Obtém um objeto ICorDebugClass que representa essa função é um membro da classe.</span><span class="sxs-lookup"><span data-stu-id="f4516-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4516-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f4516-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4516-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4516-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="f4516-106">[out] Um ponteiro para o endereço do `ICorDebugClass` objeto que representa a classe, ou nulo, se essa função não é um membro de uma classe.</span><span class="sxs-lookup"><span data-stu-id="f4516-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4516-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4516-107">Requirements</span></span>  
 <span data-ttu-id="f4516-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4516-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4516-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4516-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4516-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4516-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4516-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4516-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
