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
ms.openlocfilehash: 219aa27296dffa525bf3e2b836825437a8ce77b0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207651"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="e16b0-102">Método ICorDebugMDA::GetXML</span><span class="sxs-lookup"><span data-stu-id="e16b0-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="e16b0-103">Obtém o fluxo XML completo associado ao MDA (Assistente de depuração gerenciada) representado por [ICorDebugMDA](icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e16b0-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e16b0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e16b0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e16b0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e16b0-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="e16b0-106">no O tamanho da `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="e16b0-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e16b0-107">fora Um ponteiro para o comprimento do fluxo XML.</span><span class="sxs-lookup"><span data-stu-id="e16b0-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="e16b0-108">fora Uma matriz na qual armazenar o fluxo XML.</span><span class="sxs-lookup"><span data-stu-id="e16b0-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="e16b0-109">A matriz pode estar vazia.</span><span class="sxs-lookup"><span data-stu-id="e16b0-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e16b0-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="e16b0-110">Remarks</span></span>  
 <span data-ttu-id="e16b0-111">O `GetXML` método pode potencialmente afetar o desempenho, dependendo do tamanho do fluxo XML associado.</span><span class="sxs-lookup"><span data-stu-id="e16b0-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e16b0-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e16b0-112">Requirements</span></span>  
 <span data-ttu-id="e16b0-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e16b0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e16b0-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e16b0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e16b0-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e16b0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e16b0-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e16b0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e16b0-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="e16b0-117">See also</span></span>

- [<span data-ttu-id="e16b0-118">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="e16b0-118">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="e16b0-119">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="e16b0-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
