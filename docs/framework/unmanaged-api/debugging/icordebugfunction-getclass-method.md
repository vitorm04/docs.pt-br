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
ms.openlocfilehash: 887d207aea3de9296107c041816606b2f5947406
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124025"
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="d7df2-102">Método ICorDebugFunction::GetClass</span><span class="sxs-lookup"><span data-stu-id="d7df2-102">ICorDebugFunction::GetClass Method</span></span>
<span data-ttu-id="d7df2-103">Obtém um objeto ICorDebugClass que representa a classe da qual essa função é membro.</span><span class="sxs-lookup"><span data-stu-id="d7df2-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7df2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7df2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7df2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d7df2-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="d7df2-106">fora Um ponteiro para o endereço do objeto `ICorDebugClass` que representa a classe, ou NULL, se essa função não for um membro de uma classe.</span><span class="sxs-lookup"><span data-stu-id="d7df2-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7df2-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7df2-107">Requirements</span></span>  
 <span data-ttu-id="d7df2-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7df2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7df2-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7df2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7df2-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7df2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7df2-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7df2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
