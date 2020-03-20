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
ms.openlocfilehash: 76f18336808e6832b2ded94349efd7948f23a1ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175688"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="95076-102">Método IMetaDataEmit::Save</span><span class="sxs-lookup"><span data-stu-id="95076-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="95076-103">Salva todos os metadados no escopo atual para o arquivo no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="95076-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95076-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95076-104">Syntax</span></span>  
  
```cpp  
HRESULT Save (
    [in]  LPCWSTR     szFile,
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95076-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="95076-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="95076-106">[em] O nome do arquivo para salvar.</span><span class="sxs-lookup"><span data-stu-id="95076-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="95076-107">Se esse valor for nulo, a cópia na memória será salva no último local usado.</span><span class="sxs-lookup"><span data-stu-id="95076-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="95076-108">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="95076-108">[in] Reserved.</span></span> <span data-ttu-id="95076-109">Deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="95076-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95076-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="95076-110">Requirements</span></span>  
 <span data-ttu-id="95076-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95076-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95076-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="95076-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="95076-113">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="95076-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95076-114">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95076-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95076-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="95076-115">See also</span></span>

- [<span data-ttu-id="95076-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="95076-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="95076-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="95076-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
