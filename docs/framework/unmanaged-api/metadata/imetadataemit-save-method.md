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
ms.openlocfilehash: 49e45085b0fbca10e490f11ce588f68aa8237b46
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139068"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="03722-102">Método IMetaDataEmit::Save</span><span class="sxs-lookup"><span data-stu-id="03722-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="03722-103">Salva todos os metadados no escopo atual para o arquivo no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="03722-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03722-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03722-104">Syntax</span></span>  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03722-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="03722-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="03722-106">[in] O nome do arquivo para salvar.</span><span class="sxs-lookup"><span data-stu-id="03722-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="03722-107">Se esse valor for nulo, a cópia na memória será salvo até o último local que foi usado.</span><span class="sxs-lookup"><span data-stu-id="03722-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="03722-108">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="03722-108">[in] Reserved.</span></span> <span data-ttu-id="03722-109">Deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="03722-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03722-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03722-110">Requirements</span></span>  
 <span data-ttu-id="03722-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03722-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03722-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="03722-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03722-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="03722-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="03722-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="03722-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="03722-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03722-115">See also</span></span>

- [<span data-ttu-id="03722-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="03722-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="03722-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="03722-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
