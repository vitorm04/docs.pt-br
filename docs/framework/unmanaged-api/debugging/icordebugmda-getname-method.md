---
title: Método ICorDebugMDA::GetName
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetName
helpviewer_keywords:
- ICorDebugMDA::GetName method [.NET Framework debugging]
- GetName method, ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 885bf5e8-00b7-4cd7-9d8d-e720d47918c4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f62fa23d30a93f863cb2be0fa060bd2eba8dca1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141721"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="81581-102">Método ICorDebugMDA::GetName</span><span class="sxs-lookup"><span data-stu-id="81581-102">ICorDebugMDA::GetName Method</span></span>
<span data-ttu-id="81581-103">Obtém uma cadeia de caracteres que contém o nome do Assistente para depuração gerenciada (MDA) representado por [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="81581-103">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81581-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81581-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81581-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="81581-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="81581-106">[in] O tamanho do `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="81581-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="81581-107">[out] Um ponteiro para o comprimento do nome.</span><span class="sxs-lookup"><span data-stu-id="81581-107">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="81581-108">[out] Uma matriz na qual armazenar o nome.</span><span class="sxs-lookup"><span data-stu-id="81581-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81581-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="81581-109">Remarks</span></span>  
 <span data-ttu-id="81581-110">Nomes MDA são valores exclusivos.</span><span class="sxs-lookup"><span data-stu-id="81581-110">MDA names are unique values.</span></span> <span data-ttu-id="81581-111">O `GetName` método é uma alternativa conveniente de desempenho para obter o fluxo XML e extrair o nome do fluxo com base no esquema.</span><span class="sxs-lookup"><span data-stu-id="81581-111">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81581-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81581-112">Requirements</span></span>  
 <span data-ttu-id="81581-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81581-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81581-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81581-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81581-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81581-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81581-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81581-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81581-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81581-117">See also</span></span>

- [<span data-ttu-id="81581-118">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="81581-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="81581-119">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="81581-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
