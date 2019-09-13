---
title: Método ICorDebugModule::GetName
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7f62385031967c164915fd31735a6d962f557fa
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894994"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="66591-102">Método ICorDebugModule::GetName</span><span class="sxs-lookup"><span data-stu-id="66591-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="66591-103">Obtém o nome do arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="66591-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66591-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="66591-104">Syntax</span></span>  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66591-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="66591-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="66591-106">no O tamanho da `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="66591-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="66591-107">no Um ponteiro para o comprimento do nome retornado.</span><span class="sxs-lookup"><span data-stu-id="66591-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="66591-108">fora Uma matriz que armazena o nome retornado.</span><span class="sxs-lookup"><span data-stu-id="66591-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66591-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="66591-109">Remarks</span></span>  
 <span data-ttu-id="66591-110">O `GetName` método retorna um S_OK HRESULT se o nome do arquivo do módulo corresponder ao nome no disco.</span><span class="sxs-lookup"><span data-stu-id="66591-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="66591-111">`GetName`Retorna um "S_FALSE HRESULT" se o nome for criei, por exemplo, para um módulo dinâmico ou na memória.</span><span class="sxs-lookup"><span data-stu-id="66591-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66591-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="66591-112">Requirements</span></span>  
 <span data-ttu-id="66591-113">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66591-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66591-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66591-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66591-115">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66591-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66591-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66591-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66591-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66591-117">See also</span></span>
