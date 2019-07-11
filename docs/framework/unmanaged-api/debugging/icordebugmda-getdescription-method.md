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
ms.openlocfilehash: da57ecf0c153d902322798e1927c995a34cb93d2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761994"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="af9e9-102">Método ICorDebugMDA::GetDescription</span><span class="sxs-lookup"><span data-stu-id="af9e9-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="af9e9-103">Obtém uma cadeia de caracteres que contém a descrição do Assistente para depuração gerenciada (MDA) representado por [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="af9e9-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af9e9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af9e9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af9e9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="af9e9-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="af9e9-106">[in] O tamanho do buffer de cadeia de caracteres que armazenará a descrição.</span><span class="sxs-lookup"><span data-stu-id="af9e9-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="af9e9-107">[out] Um ponteiro para o número de bytes retornados no buffer de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="af9e9-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="af9e9-108">[out] Um buffer de cadeia de caracteres que contém a descrição do que o MDA.</span><span class="sxs-lookup"><span data-stu-id="af9e9-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af9e9-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="af9e9-109">Remarks</span></span>  
 <span data-ttu-id="af9e9-110">A cadeia de caracteres pode ser zero em comprimento.</span><span class="sxs-lookup"><span data-stu-id="af9e9-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af9e9-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af9e9-111">Requirements</span></span>  
 <span data-ttu-id="af9e9-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af9e9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af9e9-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af9e9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af9e9-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af9e9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af9e9-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af9e9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af9e9-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af9e9-116">See also</span></span>

- [<span data-ttu-id="af9e9-117">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="af9e9-117">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="af9e9-118">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="af9e9-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
