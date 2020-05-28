---
title: Método IMetaDataEmit::ApplyEditAndContinue
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.ApplyEditAndContinue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::ApplyEditAndContinue
helpviewer_keywords:
- ApplyEditAndContinue method [.NET Framework metadata]
- IMetaDataEmit::ApplyEditAndContinue method [.NET Framework metadata]
ms.assetid: 35991289-f389-495d-8caa-a6384fb1d557
topic_type:
- apiref
ms.openlocfilehash: 7ce9ac95c7183a7d47c367914d80f77c57dde0d7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005759"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="285e1-102">Método IMetaDataEmit::ApplyEditAndContinue</span><span class="sxs-lookup"><span data-stu-id="285e1-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="285e1-103">Atualiza o escopo do assembly atual com as alterações feitas nos metadados especificados.</span><span class="sxs-lookup"><span data-stu-id="285e1-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="285e1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="285e1-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="285e1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="285e1-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="285e1-106">\[no \] ponteiro para um objeto [IUnknown](/cpp/atl/iunknown) que representa os metadados delta do arquivo executável portátil (PE).</span><span class="sxs-lookup"><span data-stu-id="285e1-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="285e1-107">Os metadados delta são o bloco de metadados que inclui as alterações feitas na cópia dos metadados reais do módulo.</span><span class="sxs-lookup"><span data-stu-id="285e1-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="285e1-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="285e1-108">Requirements</span></span>  
 <span data-ttu-id="285e1-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="285e1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="285e1-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="285e1-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="285e1-111">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="285e1-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="285e1-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="285e1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="285e1-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="285e1-113">See also</span></span>

- [<span data-ttu-id="285e1-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="285e1-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="285e1-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="285e1-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
