---
title: "Método ICorPublishProcess::GetDisplayName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess.GetDisplayName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess::GetDisplayName
helpviewer_keywords:
- ICorPublishProcess::GetDisplayName method [.NET Framework debugging]
- GetDisplayName method, ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 7c0af9e9-a73f-41aa-a685-b21c439e059d
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98c751b29f1bffd8baa8b87548d588c6db98eed2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="694e3-102">Método ICorPublishProcess::GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="694e3-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="694e3-103">Obtém o caminho completo do executável para o processo referenciado por esse [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="694e3-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="694e3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="694e3-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="694e3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="694e3-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="694e3-106">[in] O tamanho do `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="694e3-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="694e3-107">[out] O número de caracteres largos retornado no `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="694e3-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="694e3-108">[out] Uma matriz para armazenar o nome, incluindo o caminho completo, do executável.</span><span class="sxs-lookup"><span data-stu-id="694e3-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="694e3-109">O nome é terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="694e3-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="694e3-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="694e3-110">Requirements</span></span>  
 <span data-ttu-id="694e3-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="694e3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="694e3-112">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="694e3-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="694e3-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="694e3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="694e3-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="694e3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="694e3-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="694e3-115">See Also</span></span>  
 [<span data-ttu-id="694e3-116">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="694e3-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
