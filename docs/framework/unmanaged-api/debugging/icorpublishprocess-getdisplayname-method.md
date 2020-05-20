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
ms.openlocfilehash: dc76274d3b0acbbe0b03eb141d2b3e6ff9063afb
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421118"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="e1398-102">Método ICorPublishProcess::GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="e1398-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="e1398-103">Obtém o caminho completo do executável para o processo referenciado por este [ICorPublishProcess](icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e1398-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1398-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e1398-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1398-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1398-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="e1398-106">no O tamanho da `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="e1398-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e1398-107">fora O número de caracteres largos retornados na `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="e1398-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="e1398-108">fora Uma matriz para armazenar o nome, incluindo o caminho completo do executável.</span><span class="sxs-lookup"><span data-stu-id="e1398-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="e1398-109">O nome é encerrado em nulo.</span><span class="sxs-lookup"><span data-stu-id="e1398-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1398-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e1398-110">Requirements</span></span>  
 <span data-ttu-id="e1398-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1398-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1398-112">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="e1398-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e1398-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1398-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1398-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1398-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1398-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="e1398-115">See also</span></span>

- [<span data-ttu-id="e1398-116">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="e1398-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
