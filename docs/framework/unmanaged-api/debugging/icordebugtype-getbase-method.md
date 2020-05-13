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
ms.openlocfilehash: fc406f6e87e5b2be48c6fe7d5fc988774ac5cd11
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379985"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="a9d47-102">Método ICorDebugType::GetBase</span><span class="sxs-lookup"><span data-stu-id="a9d47-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="a9d47-103">Obtém um ponteiro de interface para um ICorDebugType que representa o tipo base, se houver um, do tipo representado por este `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="a9d47-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9d47-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9d47-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9d47-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a9d47-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="a9d47-106">fora Um ponteiro para o endereço de um `ICorDebugType` objeto que representa o tipo base.</span><span class="sxs-lookup"><span data-stu-id="a9d47-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9d47-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a9d47-107">Remarks</span></span>  
 <span data-ttu-id="a9d47-108">Pesquisar o tipo base de um tipo é útil para implementar a funcionalidade comum do depurador, como imprimir todos os campos de um objeto ou suas classes pai.</span><span class="sxs-lookup"><span data-stu-id="a9d47-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9d47-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a9d47-109">Requirements</span></span>  
 <span data-ttu-id="a9d47-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9d47-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9d47-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9d47-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9d47-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9d47-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9d47-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9d47-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
