---
title: Método ICorDebugType::GetBase
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d04bc67013a2227f295ac3a41be027b9f9b04e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946273"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="10658-102">Método ICorDebugType::GetBase</span><span class="sxs-lookup"><span data-stu-id="10658-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="10658-103">Obtém um ponteiro de interface para um que representa o tipo base, se houver, do tipo representado por este ICorDebugType `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="10658-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10658-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10658-104">Syntax</span></span>  
  
```  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10658-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="10658-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="10658-106">[out] Um ponteiro para o endereço de um `ICorDebugType` objeto que representa o tipo base.</span><span class="sxs-lookup"><span data-stu-id="10658-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10658-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="10658-107">Remarks</span></span>  
 <span data-ttu-id="10658-108">Procurar o tipo base para um tipo é útil para implementar a funcionalidade comum do depurador, como a impressão de todos os campos de um objeto ou suas classes pai.</span><span class="sxs-lookup"><span data-stu-id="10658-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10658-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="10658-109">Requirements</span></span>  
 <span data-ttu-id="10658-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10658-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10658-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10658-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10658-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10658-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10658-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10658-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
