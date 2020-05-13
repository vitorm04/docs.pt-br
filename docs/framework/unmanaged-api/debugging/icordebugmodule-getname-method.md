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
ms.openlocfilehash: 55342c803756aa10c2e7c835d9e1d58b439bb36c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212536"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="b1310-102">Método ICorDebugModule::GetName</span><span class="sxs-lookup"><span data-stu-id="b1310-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="b1310-103">Obtém o nome do arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="b1310-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1310-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1310-104">Syntax</span></span>  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1310-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1310-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="b1310-106">no O tamanho da `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="b1310-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b1310-107">no Um ponteiro para o comprimento do nome retornado.</span><span class="sxs-lookup"><span data-stu-id="b1310-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="b1310-108">fora Uma matriz que armazena o nome retornado.</span><span class="sxs-lookup"><span data-stu-id="b1310-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1310-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1310-109">Remarks</span></span>  
 <span data-ttu-id="b1310-110">O `GetName` método retornará um S_OK HRESULT se o nome do arquivo do módulo corresponder ao nome no disco.</span><span class="sxs-lookup"><span data-stu-id="b1310-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="b1310-111">`GetName`Retorna um S_FALSE HRESULT se o nome for criei, como para um módulo dinâmico ou na memória.</span><span class="sxs-lookup"><span data-stu-id="b1310-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1310-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1310-112">Requirements</span></span>  
 <span data-ttu-id="b1310-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1310-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1310-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1310-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1310-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1310-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1310-116">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1310-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1310-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="b1310-117">See also</span></span>
