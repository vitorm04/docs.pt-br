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
ms.openlocfilehash: 1b19ce5e9f795fd9ff4dd15e10256a150063a314
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128036"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="2af9f-102">Método ICorDebugMDA::GetName</span><span class="sxs-lookup"><span data-stu-id="2af9f-102">ICorDebugMDA::GetName Method</span></span>
<span data-ttu-id="2af9f-103">Obtém uma cadeia de caracteres que contém o nome do MDA (Assistente de depuração gerenciada) representado por [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="2af9f-103">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2af9f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2af9f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2af9f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2af9f-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="2af9f-106">no O tamanho da matriz de `szName`.</span><span class="sxs-lookup"><span data-stu-id="2af9f-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="2af9f-107">fora Um ponteiro para o comprimento do nome.</span><span class="sxs-lookup"><span data-stu-id="2af9f-107">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="2af9f-108">fora Uma matriz na qual armazenar o nome.</span><span class="sxs-lookup"><span data-stu-id="2af9f-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2af9f-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2af9f-109">Remarks</span></span>  
 <span data-ttu-id="2af9f-110">Os nomes de MDA são valores exclusivos.</span><span class="sxs-lookup"><span data-stu-id="2af9f-110">MDA names are unique values.</span></span> <span data-ttu-id="2af9f-111">O método `GetName` é uma alternativa de desempenho conveniente para obter o fluxo XML e extrair o nome do fluxo com base no esquema.</span><span class="sxs-lookup"><span data-stu-id="2af9f-111">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2af9f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2af9f-112">Requirements</span></span>  
 <span data-ttu-id="2af9f-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2af9f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2af9f-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2af9f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2af9f-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2af9f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2af9f-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2af9f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2af9f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2af9f-117">See also</span></span>

- [<span data-ttu-id="2af9f-118">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="2af9f-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="2af9f-119">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="2af9f-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
