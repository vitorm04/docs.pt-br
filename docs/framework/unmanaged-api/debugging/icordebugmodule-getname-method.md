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
ms.openlocfilehash: b39467c067e50f2d553b35a41b0f783e0fc82156
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988007"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="0b755-102">Método ICorDebugModule::GetName</span><span class="sxs-lookup"><span data-stu-id="0b755-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="0b755-103">Obtém o nome do arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="0b755-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b755-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b755-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b755-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b755-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="0b755-106">[in] O tamanho do `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="0b755-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0b755-107">[in] Um ponteiro para o comprimento do nome retornado.</span><span class="sxs-lookup"><span data-stu-id="0b755-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="0b755-108">[out] Uma matriz que armazena o nome retornado.</span><span class="sxs-lookup"><span data-stu-id="0b755-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b755-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="0b755-109">Remarks</span></span>  
 <span data-ttu-id="0b755-110">O `GetName` método retornará um S_OK HRESULT, se o nome de arquivo do módulo corresponde ao nome no disco.</span><span class="sxs-lookup"><span data-stu-id="0b755-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="0b755-111">`GetName` Retorna um HRESULT S_FALSE se o nome for fabricadas, por exemplo, para um módulo dinâmico ou na memória.</span><span class="sxs-lookup"><span data-stu-id="0b755-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b755-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0b755-112">Requirements</span></span>  
 <span data-ttu-id="0b755-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b755-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b755-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b755-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b755-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b755-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b755-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b755-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b755-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b755-117">See also</span></span>
