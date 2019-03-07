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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e74d625cadb2febe45aa4c000e5b63f96aada55
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494097"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="5df3f-102">Método ICeeGen::AddSectionReloc</span><span class="sxs-lookup"><span data-stu-id="5df3f-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="5df3f-103">Adiciona uma instrução de reloc a base de código.</span><span class="sxs-lookup"><span data-stu-id="5df3f-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="5df3f-104">Esse método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="5df3f-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5df3f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5df3f-105">Syntax</span></span>  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5df3f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5df3f-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="5df3f-107">[in] A seção de código na memória ao qual adicionar uma instrução de reloc.</span><span class="sxs-lookup"><span data-stu-id="5df3f-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="5df3f-108">[in] O deslocamento da seção.</span><span class="sxs-lookup"><span data-stu-id="5df3f-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="5df3f-109">[in] A seção à qual `offset` refere-se.</span><span class="sxs-lookup"><span data-stu-id="5df3f-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="5df3f-110">[in] Um dos [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) valores, que indica o tipo da instrução de reloc a adicionar.</span><span class="sxs-lookup"><span data-stu-id="5df3f-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5df3f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5df3f-111">Requirements</span></span>  
 <span data-ttu-id="5df3f-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5df3f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5df3f-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5df3f-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5df3f-114">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5df3f-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5df3f-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5df3f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5df3f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5df3f-116">See also</span></span>
- [<span data-ttu-id="5df3f-117">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="5df3f-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
