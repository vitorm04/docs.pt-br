---
title: Método ICorDebugClass::GetModule
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetModule
helpviewer_keywords:
- GetModule method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetModule method [.NET Framework debugging]
ms.assetid: 87029cc4-e5e1-42d5-8b98-655bb7ece520
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e96d0d82b08449b4675ec7fd1517317006011ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989216"
---
# <a name="icordebugclassgetmodule-method"></a><span data-ttu-id="84899-102">Método ICorDebugClass::GetModule</span><span class="sxs-lookup"><span data-stu-id="84899-102">ICorDebugClass::GetModule Method</span></span>
<span data-ttu-id="84899-103">Obtém o módulo que define essa classe.</span><span class="sxs-lookup"><span data-stu-id="84899-103">Gets the module that defines this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84899-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84899-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule    **pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84899-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="84899-105">Parameters</span></span>  
 `pModule`  
 <span data-ttu-id="84899-106">[out] Um ponteiro para o endereço de um objeto ICorDebugModule que representa o módulo no qual essa classe é definida.</span><span class="sxs-lookup"><span data-stu-id="84899-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this class is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84899-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="84899-107">Requirements</span></span>  
 <span data-ttu-id="84899-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84899-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84899-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84899-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84899-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84899-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84899-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84899-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
