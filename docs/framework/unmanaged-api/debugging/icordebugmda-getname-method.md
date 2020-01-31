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
ms.openlocfilehash: 522ac2fd448abaaba48d4d5c20551e8029b35fd4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793237"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="b642c-102">Método ICorDebugMDA::GetName</span><span class="sxs-lookup"><span data-stu-id="b642c-102">ICorDebugMDA::GetName Method</span></span>
<span data-ttu-id="b642c-103">Obtém uma cadeia de caracteres que contém o nome do MDA (Assistente de depuração gerenciada) representado por [ICorDebugMDA](icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b642c-103">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b642c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b642c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b642c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b642c-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="b642c-106">no O tamanho da matriz de `szName`.</span><span class="sxs-lookup"><span data-stu-id="b642c-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b642c-107">fora Um ponteiro para o comprimento do nome.</span><span class="sxs-lookup"><span data-stu-id="b642c-107">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="b642c-108">fora Uma matriz na qual armazenar o nome.</span><span class="sxs-lookup"><span data-stu-id="b642c-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b642c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b642c-109">Remarks</span></span>  
 <span data-ttu-id="b642c-110">Os nomes de MDA são valores exclusivos.</span><span class="sxs-lookup"><span data-stu-id="b642c-110">MDA names are unique values.</span></span> <span data-ttu-id="b642c-111">O método `GetName` é uma alternativa de desempenho conveniente para obter o fluxo XML e extrair o nome do fluxo com base no esquema.</span><span class="sxs-lookup"><span data-stu-id="b642c-111">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b642c-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b642c-112">Requirements</span></span>  
 <span data-ttu-id="b642c-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b642c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b642c-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b642c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b642c-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b642c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b642c-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b642c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b642c-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="b642c-117">See also</span></span>

- [<span data-ttu-id="b642c-118">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="b642c-118">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="b642c-119">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="b642c-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
