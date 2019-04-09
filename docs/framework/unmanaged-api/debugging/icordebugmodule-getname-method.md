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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176638"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="e72bd-102">Método ICorDebugModule::GetName</span><span class="sxs-lookup"><span data-stu-id="e72bd-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="e72bd-103">Obtém o nome do arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="e72bd-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e72bd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e72bd-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e72bd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e72bd-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="e72bd-106">[in] O tamanho do `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="e72bd-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e72bd-107">[in] Um ponteiro para o comprimento do nome retornado.</span><span class="sxs-lookup"><span data-stu-id="e72bd-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="e72bd-108">[out] Uma matriz que armazena o nome retornado.</span><span class="sxs-lookup"><span data-stu-id="e72bd-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e72bd-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e72bd-109">Remarks</span></span>  
 <span data-ttu-id="e72bd-110">O `GetName` método retornará um S_OK HRESULT, se o nome de arquivo do módulo corresponde ao nome no disco.</span><span class="sxs-lookup"><span data-stu-id="e72bd-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> `GetName` <span data-ttu-id="e72bd-111">Retorna um HRESULT S_FALSE se o nome for fabricadas, por exemplo, para um módulo dinâmico ou na memória.</span><span class="sxs-lookup"><span data-stu-id="e72bd-111">returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e72bd-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e72bd-112">Requirements</span></span>  
 <span data-ttu-id="e72bd-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e72bd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e72bd-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e72bd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e72bd-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e72bd-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e72bd-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e72bd-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e72bd-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e72bd-117">See also</span></span>
