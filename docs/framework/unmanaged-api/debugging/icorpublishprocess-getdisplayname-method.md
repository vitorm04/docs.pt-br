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
ms.openlocfilehash: 7f2e644340a2ec7fe807830422b927ce811ddcf9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790572"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="046d8-102">Método ICorPublishProcess::GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="046d8-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="046d8-103">Obtém o caminho completo do executável para o processo referenciado por este [ICorPublishProcess](icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="046d8-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="046d8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="046d8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="046d8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="046d8-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="046d8-106">no O tamanho da matriz de `szName`.</span><span class="sxs-lookup"><span data-stu-id="046d8-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="046d8-107">fora O número de caracteres largos retornados na matriz de `szName`.</span><span class="sxs-lookup"><span data-stu-id="046d8-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="046d8-108">fora Uma matriz para armazenar o nome, incluindo o caminho completo do executável.</span><span class="sxs-lookup"><span data-stu-id="046d8-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="046d8-109">O nome é encerrado em nulo.</span><span class="sxs-lookup"><span data-stu-id="046d8-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="046d8-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="046d8-110">Requirements</span></span>  
 <span data-ttu-id="046d8-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="046d8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="046d8-112">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="046d8-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="046d8-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="046d8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="046d8-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="046d8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="046d8-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="046d8-115">See also</span></span>

- [<span data-ttu-id="046d8-116">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="046d8-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
