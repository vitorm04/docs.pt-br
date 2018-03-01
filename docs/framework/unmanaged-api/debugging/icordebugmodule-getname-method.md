---
title: "Método ICorDebugModule::GetName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 64be936277b0ebe04248ae2913a882b628ee363f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="82535-102">Método ICorDebugModule::GetName</span><span class="sxs-lookup"><span data-stu-id="82535-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="82535-103">Obtém o nome do arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="82535-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82535-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82535-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82535-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="82535-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="82535-106">[in] O tamanho do `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="82535-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="82535-107">[in] Um ponteiro para o comprimento do nome retornado.</span><span class="sxs-lookup"><span data-stu-id="82535-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="82535-108">[out] Uma matriz que armazena o nome retornado.</span><span class="sxs-lookup"><span data-stu-id="82535-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82535-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="82535-109">Remarks</span></span>  
 <span data-ttu-id="82535-110">O `GetName` método retorna um HRESULT S_OK se o nome de arquivo do módulo corresponde ao nome no disco.</span><span class="sxs-lookup"><span data-stu-id="82535-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="82535-111">`GetName`Retorna um HRESULT S_FALSE se o nome for fabricadas, como para um módulo dinâmico ou na memória.</span><span class="sxs-lookup"><span data-stu-id="82535-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82535-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82535-112">Requirements</span></span>  
 <span data-ttu-id="82535-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82535-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82535-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82535-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82535-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82535-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82535-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82535-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82535-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82535-117">See Also</span></span>  
    
 
