---
title: Método ICeeGen::AddSectionReloc
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
ms.openlocfilehash: 129750644962cee3206b9e38cbeaa77d38dddd71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176104"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="13858-102">Método ICeeGen::AddSectionReloc</span><span class="sxs-lookup"><span data-stu-id="13858-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="13858-103">Adiciona uma instrução .reloc à base de código.</span><span class="sxs-lookup"><span data-stu-id="13858-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="13858-104">Este método é obsoleto e não deve ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="13858-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13858-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13858-105">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13858-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="13858-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="13858-107">[em] A seção de código de memória para adicionar uma instrução .reloc.</span><span class="sxs-lookup"><span data-stu-id="13858-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="13858-108">[em] O deslocamento da seção.</span><span class="sxs-lookup"><span data-stu-id="13858-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="13858-109">[em] A seção `offset` a que se refere.</span><span class="sxs-lookup"><span data-stu-id="13858-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="13858-110">[em] Um dos valores [de CeeSectionRelocType,](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) indicando o tipo de instrução .reloc a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="13858-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13858-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13858-111">Requirements</span></span>  
 <span data-ttu-id="13858-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13858-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13858-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="13858-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13858-114">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="13858-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="13858-115">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13858-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13858-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="13858-116">See also</span></span>

- [<span data-ttu-id="13858-117">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="13858-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
