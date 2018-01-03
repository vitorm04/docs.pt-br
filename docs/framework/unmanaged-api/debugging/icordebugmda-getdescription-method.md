---
title: "Método ICorDebugMDA::GetDescription"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMDA.GetDescription
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMDA::GetDescription
helpviewer_keywords:
- GetDescription method [.NET Framework debugging]
- ICorDebugMDA::GetDescription method [.NET Framework debugging]
ms.assetid: 01d1b481-ca67-4712-8744-d342ec0df639
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d527f22693ca912d33d56ae4f0ffeddb9de38ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="c81e3-102">Método ICorDebugMDA::GetDescription</span><span class="sxs-lookup"><span data-stu-id="c81e3-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="c81e3-103">Obtém uma cadeia de caracteres que contém a descrição do Assistente de depuração gerenciado (MDA) representado por [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c81e3-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c81e3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c81e3-104">Syntax</span></span>  
  
```  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c81e3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c81e3-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="c81e3-106">[in] O tamanho do buffer de cadeia de caracteres que armazenará a descrição.</span><span class="sxs-lookup"><span data-stu-id="c81e3-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c81e3-107">[out] Um ponteiro para o número de bytes retornados no buffer de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c81e3-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="c81e3-108">[out] Um buffer de cadeia de caracteres que contém a descrição do MDA.</span><span class="sxs-lookup"><span data-stu-id="c81e3-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c81e3-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c81e3-109">Remarks</span></span>  
 <span data-ttu-id="c81e3-110">A cadeia de caracteres pode ser zero em comprimento.</span><span class="sxs-lookup"><span data-stu-id="c81e3-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c81e3-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c81e3-111">Requirements</span></span>  
 <span data-ttu-id="c81e3-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c81e3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c81e3-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c81e3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c81e3-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c81e3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c81e3-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c81e3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c81e3-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c81e3-116">See Also</span></span>  
 [<span data-ttu-id="c81e3-117">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="c81e3-117">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="c81e3-118">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="c81e3-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
