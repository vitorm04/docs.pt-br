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
ms.openlocfilehash: 77e801b048709949c384f642fc0d0ecb5d7eb512
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178380"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="859b9-102">Método ICorPublishProcess::GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="859b9-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="859b9-103">Obtém o caminho completo do executável para o processo referenciado por este [ICorPublishProcess](icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="859b9-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="859b9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="859b9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="859b9-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="859b9-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="859b9-106">[em] O tamanho `szName` da matriz.</span><span class="sxs-lookup"><span data-stu-id="859b9-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="859b9-107">[fora] O número de caracteres `szName` largos retornou na matriz.</span><span class="sxs-lookup"><span data-stu-id="859b9-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="859b9-108">[fora] Uma matriz para armazenar o nome, incluindo o caminho completo, do executável.</span><span class="sxs-lookup"><span data-stu-id="859b9-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="859b9-109">O nome está nulo.</span><span class="sxs-lookup"><span data-stu-id="859b9-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="859b9-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="859b9-110">Requirements</span></span>  
 <span data-ttu-id="859b9-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="859b9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="859b9-112">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="859b9-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="859b9-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="859b9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="859b9-114">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="859b9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="859b9-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="859b9-115">See also</span></span>

- [<span data-ttu-id="859b9-116">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="859b9-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
