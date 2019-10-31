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
ms.openlocfilehash: 6964c931307a40f384ad8a8e355cab0aad575ec6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125766"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="55a42-102">Método ICorDebugClass::GetToken</span><span class="sxs-lookup"><span data-stu-id="55a42-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="55a42-103">Obtém o token de metadados `TypeDef` que faz referência à definição dessa classe.</span><span class="sxs-lookup"><span data-stu-id="55a42-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55a42-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55a42-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55a42-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="55a42-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="55a42-106">fora Um ponteiro para um `mdTypeDef` token que faz referência à definição dessa classe.</span><span class="sxs-lookup"><span data-stu-id="55a42-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55a42-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="55a42-107">Requirements</span></span>  
 <span data-ttu-id="55a42-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55a42-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55a42-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55a42-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55a42-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55a42-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55a42-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55a42-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55a42-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55a42-112">See also</span></span>

- [<span data-ttu-id="55a42-113">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="55a42-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
