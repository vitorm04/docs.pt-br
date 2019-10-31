---
title: Método ICorDebugModule::GetClassFromToken
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetClassFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetClassFromToken
helpviewer_keywords:
- GetClassFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetClassFromToken method [.NET Framework debugging]
ms.assetid: 622a4d3c-0425-4c54-a7e4-0735377cdad2
topic_type:
- apiref
ms.openlocfilehash: 790999093f874a4d81dd5db74ef012b1d997a12f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109641"
---
# <a name="icordebugmodulegetclassfromtoken-method"></a><span data-ttu-id="68d1d-102">Método ICorDebugModule::GetClassFromToken</span><span class="sxs-lookup"><span data-stu-id="68d1d-102">ICorDebugModule::GetClassFromToken Method</span></span>
<span data-ttu-id="68d1d-103">Obtém a classe especificada pelo token de metadados.</span><span class="sxs-lookup"><span data-stu-id="68d1d-103">Gets the class specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68d1d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68d1d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  mdTypeDef        typeDef,  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68d1d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="68d1d-105">Parameters</span></span>  
 `typedef`  
 <span data-ttu-id="68d1d-106">no Um `mdTypeDef` token de metadados que faz referência aos metadados de uma classe.</span><span class="sxs-lookup"><span data-stu-id="68d1d-106">[in] An `mdTypeDef` metadata token that references the metadata of a class.</span></span>  
  
 `ppClass`  
 <span data-ttu-id="68d1d-107">fora Um ponteiro para o endereço de um objeto ICorDebugClass que representa a classe.</span><span class="sxs-lookup"><span data-stu-id="68d1d-107">[out] A pointer to the address of an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68d1d-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="68d1d-108">Requirements</span></span>  
 <span data-ttu-id="68d1d-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68d1d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68d1d-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68d1d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68d1d-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68d1d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68d1d-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68d1d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
