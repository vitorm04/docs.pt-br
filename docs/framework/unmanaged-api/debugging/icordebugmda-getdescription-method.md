---
title: Método ICorDebugMDA::GetDescription
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetDescription
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetDescription
helpviewer_keywords:
- GetDescription method [.NET Framework debugging]
- ICorDebugMDA::GetDescription method [.NET Framework debugging]
ms.assetid: 01d1b481-ca67-4712-8744-d342ec0df639
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fdace527194228dd6004a991950a80d23275650
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413290"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="0677b-102">Método ICorDebugMDA::GetDescription</span><span class="sxs-lookup"><span data-stu-id="0677b-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="0677b-103">Obtém uma cadeia de caracteres que contém a descrição do Assistente de depuração gerenciado (MDA) representado por [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0677b-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0677b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0677b-104">Syntax</span></span>  
  
```  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0677b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0677b-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="0677b-106">[in] O tamanho do buffer de cadeia de caracteres que armazenará a descrição.</span><span class="sxs-lookup"><span data-stu-id="0677b-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0677b-107">[out] Um ponteiro para o número de bytes retornados no buffer de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0677b-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="0677b-108">[out] Um buffer de cadeia de caracteres que contém a descrição do MDA.</span><span class="sxs-lookup"><span data-stu-id="0677b-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0677b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="0677b-109">Remarks</span></span>  
 <span data-ttu-id="0677b-110">A cadeia de caracteres pode ser zero em comprimento.</span><span class="sxs-lookup"><span data-stu-id="0677b-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0677b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0677b-111">Requirements</span></span>  
 <span data-ttu-id="0677b-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0677b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0677b-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0677b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0677b-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0677b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0677b-115">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0677b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0677b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0677b-116">See Also</span></span>  
 [<span data-ttu-id="0677b-117">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="0677b-117">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="0677b-118">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="0677b-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
