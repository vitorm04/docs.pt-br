---
title: Método ICorDebugModule::GetAssembly
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetAssembly
helpviewer_keywords:
- ICorDebugModule::GetAssembly method [.NET Framework debugging]
- GetAssembly method [.NET Framework debugging]
ms.assetid: 989762c4-3d15-4485-b8ee-69e0fa8ec895
topic_type:
- apiref
ms.openlocfilehash: 29c9d9dde4776ef729c0bbae7b644171a265e3ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137461"
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="2d436-102">Método ICorDebugModule::GetAssembly</span><span class="sxs-lookup"><span data-stu-id="2d436-102">ICorDebugModule::GetAssembly Method</span></span>
<span data-ttu-id="2d436-103">Obtém o assembly recipiente para este módulo.</span><span class="sxs-lookup"><span data-stu-id="2d436-103">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d436-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d436-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d436-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2d436-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="2d436-106">fora Um ponteiro para um objeto ICorDebugAssembly que representa o assembly que contém este módulo.</span><span class="sxs-lookup"><span data-stu-id="2d436-106">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d436-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2d436-107">Requirements</span></span>  
 <span data-ttu-id="2d436-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d436-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d436-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d436-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d436-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d436-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d436-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d436-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
