---
title: Método ICorDebugCode::GetVersionNumber
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetVersionNumber
helpviewer_keywords:
- GetVersionNumber method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetVersionNumber method [.NET Framework debugging]
ms.assetid: c8e02518-679f-4e9f-8a28-ba4a89a3876f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b6fd6e8043f1c62da8994b43a9b9af45fb2e3c0
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700818"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="43c41-102">Método ICorDebugCode::GetVersionNumber</span><span class="sxs-lookup"><span data-stu-id="43c41-102">ICorDebugCode::GetVersionNumber Method</span></span>

<span data-ttu-id="43c41-103">Obtém o número baseado em um que identifica a versão do código que esse "ICorDebugCode" representa.</span><span class="sxs-lookup"><span data-stu-id="43c41-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>

## <a name="syntax"></a><span data-ttu-id="43c41-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43c41-104">Syntax</span></span>

```cpp
HRESULT GetVersionNumber (
    [out] ULONG32    *nVersion
);
```

## <a name="parameters"></a><span data-ttu-id="43c41-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="43c41-105">Parameters</span></span>

 `nVersion`  
 <span data-ttu-id="43c41-106">fora Um ponteiro para o número de versão do código.</span><span class="sxs-lookup"><span data-stu-id="43c41-106">[out] A pointer to the version number of the code.</span></span>

## <a name="remarks"></a><span data-ttu-id="43c41-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="43c41-107">Remarks</span></span>

 <span data-ttu-id="43c41-108">O número de versão é incrementado cada vez que uma operação de "Editar e continuar" (EnC) é executada no código.</span><span class="sxs-lookup"><span data-stu-id="43c41-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>

## <a name="requirements"></a><span data-ttu-id="43c41-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="43c41-109">Requirements</span></span>

 <span data-ttu-id="43c41-110">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43c41-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43c41-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43c41-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43c41-112">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43c41-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43c41-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43c41-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
