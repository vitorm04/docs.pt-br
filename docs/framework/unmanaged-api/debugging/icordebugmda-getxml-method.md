---
title: Método ICorDebugMDA::GetXML
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e78b8a2069671d0fe790956ca914225325a78bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228816"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="1b683-102">Método ICorDebugMDA::GetXML</span><span class="sxs-lookup"><span data-stu-id="1b683-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="1b683-103">Obtém o fluxo XML completo associado com o Assistente para depuração gerenciada (MDA) representado por [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="1b683-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b683-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b683-104">Syntax</span></span>  
  
```  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b683-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1b683-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="1b683-106">[in] O tamanho do `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="1b683-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1b683-107">[out] Um ponteiro para o comprimento do fluxo XML.</span><span class="sxs-lookup"><span data-stu-id="1b683-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="1b683-108">[out] Uma matriz na qual armazenar o fluxo XML.</span><span class="sxs-lookup"><span data-stu-id="1b683-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="1b683-109">A matriz pode estar vazia.</span><span class="sxs-lookup"><span data-stu-id="1b683-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b683-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b683-110">Remarks</span></span>  
 <span data-ttu-id="1b683-111">O `GetXML` método potencialmente pode afetar o desempenho, dependendo do tamanho do fluxo de XML associado.</span><span class="sxs-lookup"><span data-stu-id="1b683-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b683-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1b683-112">Requirements</span></span>  
 <span data-ttu-id="1b683-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b683-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b683-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b683-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b683-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b683-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1b683-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="1b683-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1b683-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b683-117">See also</span></span>

- [<span data-ttu-id="1b683-118">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="1b683-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="1b683-119">Diagnosticando erros com assistentes de depuração gerenciados</span><span class="sxs-lookup"><span data-stu-id="1b683-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
