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
ms.openlocfilehash: b263fed7db5cb2ef687da45f8cbc99a02e1e3ea2
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976129"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="1b1c5-102">Método ICorDebugEval::NewString</span><span class="sxs-lookup"><span data-stu-id="1b1c5-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="1b1c5-103">Aloca uma nova instância de cadeia de caracteres com o conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="1b1c5-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b1c5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b1c5-104">Syntax</span></span>  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b1c5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1b1c5-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="1b1c5-106">no Ponteiro para o conteúdo da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1b1c5-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b1c5-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b1c5-107">Remarks</span></span>  
 <span data-ttu-id="1b1c5-108">A cadeia de caracteres é sempre criada no domínio do aplicativo no qual o thread está sendo executado no momento.</span><span class="sxs-lookup"><span data-stu-id="1b1c5-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b1c5-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1b1c5-109">Requirements</span></span>  
 <span data-ttu-id="1b1c5-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b1c5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b1c5-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b1c5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b1c5-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b1c5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b1c5-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b1c5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
