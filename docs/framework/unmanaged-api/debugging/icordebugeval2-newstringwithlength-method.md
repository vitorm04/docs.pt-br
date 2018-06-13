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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b3b77a0ffc7af3b3640d1b255bd3be522f45a7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413544"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="655a6-102">Método ICorDebugEval2::NewStringWithLength</span><span class="sxs-lookup"><span data-stu-id="655a6-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="655a6-103">Cria uma cadeia de caracteres de comprimento especificado, com o conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="655a6-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="655a6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="655a6-104">Syntax</span></span>  
  
```  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="655a6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="655a6-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="655a6-106">[in] Um ponteiro para o valor de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="655a6-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="655a6-107">[in] Comprimento da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="655a6-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="655a6-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="655a6-108">Remarks</span></span>  
 <span data-ttu-id="655a6-109">Se a cadeia de caracteres da direita caractere nulo deve estar na cadeia de caracteres gerenciada, o chamador de `NewStringWithLength` método deve garantir que o comprimento da cadeia de caracteres inclui o caractere nulo à direita.</span><span class="sxs-lookup"><span data-stu-id="655a6-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="655a6-110">A cadeia de caracteres sempre é criada no domínio do aplicativo no qual o thread está em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="655a6-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="655a6-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="655a6-111">Requirements</span></span>  
 <span data-ttu-id="655a6-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="655a6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="655a6-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="655a6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="655a6-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="655a6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="655a6-115">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="655a6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
