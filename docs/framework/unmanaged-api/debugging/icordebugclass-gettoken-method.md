---
title: Método ICorDebugClass::GetToken
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetToken
helpviewer_keywords:
- GetToken method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetToken method [.NET Framework debugging]
ms.assetid: ee5c848a-eac4-4462-b07a-07ccd76a75df
topic_type:
- apiref
ms.openlocfilehash: 3433f5f69927afb501c2596571f138e3a69fabb6
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894119"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="fa1ea-102">Método ICorDebugClass::GetToken</span><span class="sxs-lookup"><span data-stu-id="fa1ea-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="fa1ea-103">Obtém o `TypeDef` token de metadados que faz referência à definição dessa classe.</span><span class="sxs-lookup"><span data-stu-id="fa1ea-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa1ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fa1ea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa1ea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fa1ea-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="fa1ea-106">fora Um ponteiro para um `mdTypeDef` token que faz referência à definição dessa classe.</span><span class="sxs-lookup"><span data-stu-id="fa1ea-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa1ea-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fa1ea-107">Requirements</span></span>  
 <span data-ttu-id="fa1ea-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa1ea-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa1ea-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa1ea-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa1ea-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa1ea-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa1ea-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa1ea-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa1ea-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa1ea-112">See also</span></span>

- [<span data-ttu-id="fa1ea-113">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="fa1ea-113">Metadata Interfaces</span></span>](../metadata/metadata-interfaces.md)
