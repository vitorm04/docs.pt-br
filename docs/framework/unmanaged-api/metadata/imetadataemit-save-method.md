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
ms.openlocfilehash: 7ece16d8dcdc685db960a485cd19261f6b9f2fbe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757598"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="8850d-102">Método IMetaDataEmit::Save</span><span class="sxs-lookup"><span data-stu-id="8850d-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="8850d-103">Salva todos os metadados no escopo atual para o arquivo no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="8850d-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8850d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8850d-104">Syntax</span></span>  
  
```cpp  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8850d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8850d-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="8850d-106">[in] O nome do arquivo para salvar.</span><span class="sxs-lookup"><span data-stu-id="8850d-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="8850d-107">Se esse valor for nulo, a cópia na memória será salvo até o último local que foi usado.</span><span class="sxs-lookup"><span data-stu-id="8850d-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="8850d-108">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="8850d-108">[in] Reserved.</span></span> <span data-ttu-id="8850d-109">Deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="8850d-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8850d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8850d-110">Requirements</span></span>  
 <span data-ttu-id="8850d-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8850d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8850d-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8850d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8850d-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8850d-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8850d-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8850d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8850d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8850d-115">See also</span></span>

- [<span data-ttu-id="8850d-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="8850d-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="8850d-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="8850d-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
