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
ms.openlocfilehash: a2b76cb59a95082e0cf9c0884b8277cca3c8fe8d
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976064"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="1bb09-102">Método ICorDebugEval2::NewStringWithLength</span><span class="sxs-lookup"><span data-stu-id="1bb09-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="1bb09-103">Cria uma cadeia de caracteres do comprimento especificado, com o conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="1bb09-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bb09-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1bb09-104">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bb09-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1bb09-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="1bb09-106">no Um ponteiro para o valor da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1bb09-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="1bb09-107">no Comprimento da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1bb09-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bb09-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1bb09-108">Remarks</span></span>  
 <span data-ttu-id="1bb09-109">Se espera-se que o caractere nulo à direita da cadeia de caracteres esteja na cadeia de caracteres gerenciada `NewStringWithLength` , o chamador do método deve garantir que o comprimento da cadeia de caracteres inclua o caractere nulo à direita.</span><span class="sxs-lookup"><span data-stu-id="1bb09-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="1bb09-110">A cadeia de caracteres é sempre criada no domínio do aplicativo no qual o thread está sendo executado no momento.</span><span class="sxs-lookup"><span data-stu-id="1bb09-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bb09-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1bb09-111">Requirements</span></span>  
 <span data-ttu-id="1bb09-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bb09-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bb09-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1bb09-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1bb09-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bb09-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bb09-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bb09-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
