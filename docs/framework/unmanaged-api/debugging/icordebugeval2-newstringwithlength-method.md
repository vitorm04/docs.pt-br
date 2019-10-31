---
title: Método ICorDebugEval2::NewStringWithLength
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
ms.openlocfilehash: 3836b6c08098d38516c8a25260fb28998a2317fe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084776"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="2ae2b-102">Método ICorDebugEval2::NewStringWithLength</span><span class="sxs-lookup"><span data-stu-id="2ae2b-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="2ae2b-103">Cria uma cadeia de caracteres do comprimento especificado, com o conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="2ae2b-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ae2b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ae2b-104">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ae2b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2ae2b-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="2ae2b-106">no Um ponteiro para o valor da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2ae2b-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="2ae2b-107">no Comprimento da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2ae2b-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ae2b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="2ae2b-108">Remarks</span></span>  
 <span data-ttu-id="2ae2b-109">Se espera-se que o caractere nulo à direita da cadeia de caracteres esteja na cadeia de caracteres gerenciada, o chamador do método `NewStringWithLength` deve garantir que o comprimento da cadeia de caracteres inclua o caractere nulo à direita.</span><span class="sxs-lookup"><span data-stu-id="2ae2b-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="2ae2b-110">A cadeia de caracteres é sempre criada no domínio do aplicativo no qual o thread está sendo executado no momento.</span><span class="sxs-lookup"><span data-stu-id="2ae2b-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ae2b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2ae2b-111">Requirements</span></span>  
 <span data-ttu-id="2ae2b-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ae2b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ae2b-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ae2b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ae2b-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ae2b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ae2b-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ae2b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
