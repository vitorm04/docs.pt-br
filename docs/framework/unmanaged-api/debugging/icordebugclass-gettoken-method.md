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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6dc245a53c9ec7cbe56e20313abc4269e33f45c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582312"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="ee85c-102">Método ICorDebugClass::GetToken</span><span class="sxs-lookup"><span data-stu-id="ee85c-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="ee85c-103">Obtém o `TypeDef` token de metadados que faz referência a definição dessa classe.</span><span class="sxs-lookup"><span data-stu-id="ee85c-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee85c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ee85c-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee85c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee85c-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="ee85c-106">[out] Um ponteiro para um `mdTypeDef` token que faz referência a definição dessa classe.</span><span class="sxs-lookup"><span data-stu-id="ee85c-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee85c-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ee85c-107">Requirements</span></span>  
 <span data-ttu-id="ee85c-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee85c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee85c-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee85c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee85c-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee85c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee85c-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee85c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee85c-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee85c-112">See also</span></span>
- [<span data-ttu-id="ee85c-113">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="ee85c-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
