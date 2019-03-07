---
title: Método ICorDebugModule2::SetJMCStatus
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d20c640d6a6a43b7bde4c7d46df470c7bc8c5aa2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499518"
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="425ba-102">Método ICorDebugModule2::SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="425ba-102">ICorDebugModule2::SetJMCStatus Method</span></span>
<span data-ttu-id="425ba-103">Define o status de apenas My Code (JMC) de todos os métodos de todas as classes nesse ICorDebugModule2 ao valor especificado, exceto aqueles no `pTokens` matriz, que define como o valor oposto.</span><span class="sxs-lookup"><span data-stu-id="425ba-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="425ba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="425ba-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="425ba-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="425ba-105">Parameters</span></span>  
 `bIsJustMycode`  
 <span data-ttu-id="425ba-106">[in] Definido como `true` se o código deve ser depurado; caso contrário, definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="425ba-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="425ba-107">[in] O tamanho do `pTokens` matriz.</span><span class="sxs-lookup"><span data-stu-id="425ba-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="425ba-108">[in] Uma matriz de `mdToken` valores, cada um deles se refere a um método que terá o status JMC definido como!`bIsJustMycode`.</span><span class="sxs-lookup"><span data-stu-id="425ba-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="425ba-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="425ba-109">Remarks</span></span>  
 <span data-ttu-id="425ba-110">O status JMC de cada método que é especificado na `pTokens` matriz é definida como o oposto do `bIsJustMycode` valor.</span><span class="sxs-lookup"><span data-stu-id="425ba-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="425ba-111">O status de todos os outros métodos neste módulo é definido como o `bIsJustMycode` valor.</span><span class="sxs-lookup"><span data-stu-id="425ba-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="425ba-112">O `SetJMCStatus` método apaga todas as configurações anteriores de JMC neste módulo.</span><span class="sxs-lookup"><span data-stu-id="425ba-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="425ba-113">O `SetJMCStatus` método retornará um S_OK HRESULT se todas as funções foram definidas com êxito.</span><span class="sxs-lookup"><span data-stu-id="425ba-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="425ba-114">Ele retorna um HRESULT CORDBG_E_FUNCTION_NOT_DEBUGGABLE se algumas funções que são marcados `true` não são depurável.</span><span class="sxs-lookup"><span data-stu-id="425ba-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="425ba-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="425ba-115">Requirements</span></span>  
 <span data-ttu-id="425ba-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="425ba-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="425ba-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="425ba-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="425ba-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="425ba-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="425ba-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="425ba-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
