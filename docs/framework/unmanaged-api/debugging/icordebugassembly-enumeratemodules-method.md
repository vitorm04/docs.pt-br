---
title: Método ICorDebugAssembly::EnumerateModules
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.EnumerateModules
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::EnumerateModules
helpviewer_keywords:
- ICorDebugAssembly::EnumerateModules method [.NET Framework debugging]
- EnumerateModules method [.NET Framework debugging]
ms.assetid: c7ba51a1-0dd5-4452-b471-232febe0f897
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ada2e0e81c9e022e152e01472839d5d506332fac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402376"
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="d84a2-102">Método ICorDebugAssembly::EnumerateModules</span><span class="sxs-lookup"><span data-stu-id="d84a2-102">ICorDebugAssembly::EnumerateModules Method</span></span>
<span data-ttu-id="d84a2-103">Obtém um enumerador para os módulos contidos no `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="d84a2-103">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d84a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d84a2-104">Syntax</span></span>  
  
```  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d84a2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d84a2-105">Parameters</span></span>  
 `ppModules`  
 <span data-ttu-id="d84a2-106">[out] Um ponteiro para o endereço da interface ICorDebugModuleEnum que é o enumerador.</span><span class="sxs-lookup"><span data-stu-id="d84a2-106">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d84a2-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d84a2-107">Requirements</span></span>  
 <span data-ttu-id="d84a2-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d84a2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d84a2-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d84a2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d84a2-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d84a2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d84a2-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d84a2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
