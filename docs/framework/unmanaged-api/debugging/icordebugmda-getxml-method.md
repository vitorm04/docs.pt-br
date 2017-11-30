---
title: "Método ICorDebugMDA::GetXML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMDA.GetXML
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c9f1ad3ac70f001feebb0b28eec13cb45ca2c866
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="c3722-102">Método ICorDebugMDA::GetXML</span><span class="sxs-lookup"><span data-stu-id="c3722-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="c3722-103">Obtém o fluxo XML completo associado com o Assistente de depuração gerenciado (MDA) representado por [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c3722-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3722-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3722-104">Syntax</span></span>  
  
```  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3722-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3722-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="c3722-106">[in] O tamanho do `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="c3722-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c3722-107">[out] Um ponteiro para o comprimento do fluxo XML.</span><span class="sxs-lookup"><span data-stu-id="c3722-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="c3722-108">[out] Uma matriz na qual deseja armazenar o fluxo XML.</span><span class="sxs-lookup"><span data-stu-id="c3722-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="c3722-109">A matriz pode estar vazia.</span><span class="sxs-lookup"><span data-stu-id="c3722-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3722-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3722-110">Remarks</span></span>  
 <span data-ttu-id="c3722-111">O `GetXML` método pode afetar potencialmente o desempenho, dependendo do tamanho do fluxo XML associado.</span><span class="sxs-lookup"><span data-stu-id="c3722-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3722-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3722-112">Requirements</span></span>  
 <span data-ttu-id="c3722-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3722-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3722-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3722-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3722-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3722-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3722-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3722-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3722-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3722-117">See Also</span></span>  
 [<span data-ttu-id="c3722-118">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="c3722-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="c3722-119">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="c3722-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
