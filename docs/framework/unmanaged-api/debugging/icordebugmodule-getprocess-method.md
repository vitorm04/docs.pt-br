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
ms.openlocfilehash: 50722bb855c8bc8bcfdc1b405a5bbc2fa057c52c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129527"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="8daef-102">Método ICorDebugModule::GetProcess</span><span class="sxs-lookup"><span data-stu-id="8daef-102">ICorDebugModule::GetProcess Method</span></span>
<span data-ttu-id="8daef-103">Obtém o processo de contenção deste módulo.</span><span class="sxs-lookup"><span data-stu-id="8daef-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8daef-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8daef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8daef-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8daef-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="8daef-106">fora Um ponteiro para o endereço de um objeto ICorDebugProcess que representa o processo que contém este módulo.</span><span class="sxs-lookup"><span data-stu-id="8daef-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8daef-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8daef-107">Requirements</span></span>  
 <span data-ttu-id="8daef-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8daef-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8daef-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8daef-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8daef-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8daef-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8daef-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8daef-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
