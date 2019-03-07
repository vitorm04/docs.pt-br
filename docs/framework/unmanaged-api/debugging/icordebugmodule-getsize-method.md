---
title: Método ICorDebugModule::GetSize
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetSize method [.NET Framework debugging]
ms.assetid: 5c68375d-145d-46ef-a7c8-2dc4257472de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 540288f83de9c3c6ff2111330c77ded48abd6d5f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479110"
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="9965a-102">Método ICorDebugModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="9965a-102">ICorDebugModule::GetSize Method</span></span>
<span data-ttu-id="9965a-103">Obtém o tamanho, em bytes, do módulo.</span><span class="sxs-lookup"><span data-stu-id="9965a-103">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9965a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9965a-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9965a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9965a-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="9965a-106">[out] O tamanho do módulo em bytes.</span><span class="sxs-lookup"><span data-stu-id="9965a-106">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="9965a-107">Se o módulo foi produzido pelo gerador de imagem nativa (NGen.exe), o tamanho do módulo será zero.</span><span class="sxs-lookup"><span data-stu-id="9965a-107">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9965a-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9965a-108">Requirements</span></span>  
 <span data-ttu-id="9965a-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9965a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9965a-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9965a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9965a-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9965a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9965a-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9965a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
