---
title: Método ICorDebugModule::GetProcess
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetProcess method [.NET Framework debugging]
ms.assetid: 5e13446c-0271-446c-924a-9072c0e6eeae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97cecd66462cf6a88012b13dec82dbf617891dd5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987994"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="12837-102">Método ICorDebugModule::GetProcess</span><span class="sxs-lookup"><span data-stu-id="12837-102">ICorDebugModule::GetProcess Method</span></span>
<span data-ttu-id="12837-103">Obtém o processo que contém esse módulo.</span><span class="sxs-lookup"><span data-stu-id="12837-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12837-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12837-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12837-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="12837-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="12837-106">[out] Um ponteiro para o endereço de um objeto ICorDebugProcess que representa o processo que contém esse módulo.</span><span class="sxs-lookup"><span data-stu-id="12837-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12837-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="12837-107">Requirements</span></span>  
 <span data-ttu-id="12837-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12837-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12837-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12837-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12837-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12837-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12837-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12837-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
