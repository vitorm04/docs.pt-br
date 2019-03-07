---
title: Método IMetaDataEmit::Save
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Save
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90ddc540115a60154953ac6e8cb931103a650752
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492407"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="5fa31-102">Método IMetaDataEmit::Save</span><span class="sxs-lookup"><span data-stu-id="5fa31-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="5fa31-103">Salva todos os metadados no escopo atual para o arquivo no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="5fa31-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fa31-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5fa31-104">Syntax</span></span>  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fa31-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5fa31-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="5fa31-106">[in] O nome do arquivo para salvar.</span><span class="sxs-lookup"><span data-stu-id="5fa31-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="5fa31-107">Se esse valor for nulo, a cópia na memória será salvo até o último local que foi usado.</span><span class="sxs-lookup"><span data-stu-id="5fa31-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="5fa31-108">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="5fa31-108">[in] Reserved.</span></span> <span data-ttu-id="5fa31-109">Deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="5fa31-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fa31-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5fa31-110">Requirements</span></span>  
 <span data-ttu-id="5fa31-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fa31-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fa31-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5fa31-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5fa31-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5fa31-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5fa31-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fa31-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fa31-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fa31-115">See also</span></span>
- [<span data-ttu-id="5fa31-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="5fa31-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5fa31-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="5fa31-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
