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
ms.openlocfilehash: cff527aa7cde6a13667d47d030a0ef7db96ad5ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122339"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="2176b-102">Método ICorDebugType::GetBase</span><span class="sxs-lookup"><span data-stu-id="2176b-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="2176b-103">Obtém um ponteiro de interface para um ICorDebugType que representa o tipo base, se houver um, do tipo representado por esse `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="2176b-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2176b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2176b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2176b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2176b-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="2176b-106">fora Um ponteiro para o endereço de um objeto de `ICorDebugType` que representa o tipo base.</span><span class="sxs-lookup"><span data-stu-id="2176b-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2176b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2176b-107">Remarks</span></span>  
 <span data-ttu-id="2176b-108">Pesquisar o tipo base de um tipo é útil para implementar a funcionalidade comum do depurador, como imprimir todos os campos de um objeto ou suas classes pai.</span><span class="sxs-lookup"><span data-stu-id="2176b-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2176b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2176b-109">Requirements</span></span>  
 <span data-ttu-id="2176b-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2176b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2176b-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2176b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2176b-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2176b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2176b-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2176b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
