---
title: Método ICorPublishProcess::GetDisplayName
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetDisplayName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetDisplayName
helpviewer_keywords:
- ICorPublishProcess::GetDisplayName method [.NET Framework debugging]
- GetDisplayName method, ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 7c0af9e9-a73f-41aa-a685-b21c439e059d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6e7aa845f104ef734f039d46e1eeaba5fd01c73
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221763"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="150cd-102">Método ICorPublishProcess::GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="150cd-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="150cd-103">Obtém o caminho completo do executável para o processo referenciado por este [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="150cd-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="150cd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="150cd-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="150cd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="150cd-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="150cd-106">[in] O tamanho do `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="150cd-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="150cd-107">[out] O número de caracteres largos retornado no `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="150cd-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="150cd-108">[out] Uma matriz para armazenar o nome, incluindo o caminho completo, do executável.</span><span class="sxs-lookup"><span data-stu-id="150cd-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="150cd-109">O nome é terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="150cd-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="150cd-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="150cd-110">Requirements</span></span>  
 <span data-ttu-id="150cd-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="150cd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="150cd-112">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="150cd-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="150cd-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="150cd-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="150cd-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="150cd-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="150cd-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="150cd-115">See also</span></span>

- [<span data-ttu-id="150cd-116">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="150cd-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
