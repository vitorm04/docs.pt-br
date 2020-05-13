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
ms.openlocfilehash: 522e992e6d7e9a64f7590bbec0e9106e0e1f8f47
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212133"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="7bafc-102">Método ICorDebugMDA::GetDescription</span><span class="sxs-lookup"><span data-stu-id="7bafc-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="7bafc-103">Obtém uma cadeia de caracteres que contém a descrição do MDA (Assistente de depuração gerenciada) representado por [ICorDebugMDA](icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7bafc-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bafc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7bafc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bafc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7bafc-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="7bafc-106">no O tamanho do buffer de cadeia de caracteres que armazenará a descrição.</span><span class="sxs-lookup"><span data-stu-id="7bafc-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="7bafc-107">fora Um ponteiro para o número de bytes retornados no buffer de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7bafc-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="7bafc-108">fora Um buffer de cadeia de caracteres que contém a descrição do MDA.</span><span class="sxs-lookup"><span data-stu-id="7bafc-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bafc-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="7bafc-109">Remarks</span></span>  
 <span data-ttu-id="7bafc-110">A cadeia de caracteres pode ser de comprimento zero.</span><span class="sxs-lookup"><span data-stu-id="7bafc-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bafc-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7bafc-111">Requirements</span></span>  
 <span data-ttu-id="7bafc-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bafc-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bafc-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7bafc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7bafc-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bafc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bafc-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bafc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bafc-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="7bafc-116">See also</span></span>

- [<span data-ttu-id="7bafc-117">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="7bafc-117">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="7bafc-118">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="7bafc-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
