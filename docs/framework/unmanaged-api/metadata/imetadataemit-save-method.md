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
ms.openlocfilehash: a6d97d3e4a93985f9b2de3ed9785eff5f7f46c36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444673"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="ff366-102">Método IMetaDataEmit::Save</span><span class="sxs-lookup"><span data-stu-id="ff366-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="ff366-103">Salva todos os metadados no escopo atual para o arquivo no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="ff366-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff366-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff366-104">Syntax</span></span>  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff366-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ff366-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="ff366-106">[in] O nome do arquivo para salvar.</span><span class="sxs-lookup"><span data-stu-id="ff366-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="ff366-107">Se esse valor for nulo, a cópia na memória serão salvas para o último local que foi usado.</span><span class="sxs-lookup"><span data-stu-id="ff366-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="ff366-108">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="ff366-108">[in] Reserved.</span></span> <span data-ttu-id="ff366-109">Deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="ff366-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff366-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ff366-110">Requirements</span></span>  
 <span data-ttu-id="ff366-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff366-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff366-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ff366-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff366-113">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ff366-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff366-114">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff366-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff366-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff366-115">See Also</span></span>  
 [<span data-ttu-id="ff366-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="ff366-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ff366-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="ff366-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
