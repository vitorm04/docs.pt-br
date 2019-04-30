---
title: Método ICorDebugEval::NewString
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db609bdee7975b6c067271f99529e2cf2240f720
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989021"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="9fae9-102">Método ICorDebugEval::NewString</span><span class="sxs-lookup"><span data-stu-id="9fae9-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="9fae9-103">Aloca uma nova instância de cadeia de caracteres com o conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="9fae9-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fae9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9fae9-104">Syntax</span></span>  
  
```  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fae9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9fae9-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="9fae9-106">[in] Ponteiro para o conteúdo da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9fae9-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fae9-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="9fae9-107">Remarks</span></span>  
 <span data-ttu-id="9fae9-108">A cadeia de caracteres sempre é criada no domínio do aplicativo no qual o thread está em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="9fae9-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fae9-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9fae9-109">Requirements</span></span>  
 <span data-ttu-id="9fae9-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fae9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fae9-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9fae9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9fae9-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fae9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fae9-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fae9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
