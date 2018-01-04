---
title: "Método ICorDebugModule2::SetJMCStatus"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a461a9c05b18de45426247743c6e4ffca775025a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="57f65-102">Método ICorDebugModule2::SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="57f65-102">ICorDebugModule2::SetJMCStatus Method</span></span>
<span data-ttu-id="57f65-103">Define o status de apenas meu código (JMC) de todos os métodos de todas as classes neste ICorDebugModule2 ao valor especificado, exceto aqueles na `pTokens` matriz, que define como o valor oposto.</span><span class="sxs-lookup"><span data-stu-id="57f65-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57f65-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57f65-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57f65-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="57f65-105">Parameters</span></span>  
 `bIsJustMycode`  
 <span data-ttu-id="57f65-106">[in] Definido como `true` se o código é depurado; caso contrário, defina como `false`.</span><span class="sxs-lookup"><span data-stu-id="57f65-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="57f65-107">[in] O tamanho do `pTokens` matriz.</span><span class="sxs-lookup"><span data-stu-id="57f65-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="57f65-108">[in] Uma matriz de `mdToken` valores, cada um deles se refere a um método que terá seu status de JMC!`bIsJustMycode`.</span><span class="sxs-lookup"><span data-stu-id="57f65-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57f65-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="57f65-109">Remarks</span></span>  
 <span data-ttu-id="57f65-110">O status JMC de cada método é especificado no `pTokens` matriz é definida como o oposto do `bIsJustMycode` valor.</span><span class="sxs-lookup"><span data-stu-id="57f65-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="57f65-111">O status de todos os outros métodos neste módulo é definido como o `bIsJustMycode` valor.</span><span class="sxs-lookup"><span data-stu-id="57f65-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="57f65-112">O `SetJMCStatus` método apaga todas as configurações anteriores do JMC neste módulo.</span><span class="sxs-lookup"><span data-stu-id="57f65-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="57f65-113">O `SetJMCStatus` método retorna um HRESULT S_OK se todas as funções foram definidas com êxito.</span><span class="sxs-lookup"><span data-stu-id="57f65-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="57f65-114">Ele retorna um HRESULT CORDBG_E_FUNCTION_NOT_DEBUGGABLE se algumas funções que são marcados `true` não são depurável.</span><span class="sxs-lookup"><span data-stu-id="57f65-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57f65-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57f65-115">Requirements</span></span>  
 <span data-ttu-id="57f65-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57f65-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57f65-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57f65-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57f65-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57f65-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57f65-119">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57f65-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
