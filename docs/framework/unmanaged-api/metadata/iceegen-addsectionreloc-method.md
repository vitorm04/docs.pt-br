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
ms.openlocfilehash: 7d50f7488c2b231ea66c12cc4903469d9e2337fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088373"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="83a25-102">Método ICeeGen::AddSectionReloc</span><span class="sxs-lookup"><span data-stu-id="83a25-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="83a25-103">Adiciona uma instrução de reloc a base de código.</span><span class="sxs-lookup"><span data-stu-id="83a25-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="83a25-104">Esse método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="83a25-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83a25-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83a25-105">Syntax</span></span>  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83a25-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="83a25-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="83a25-107">[in] A seção de código na memória ao qual adicionar uma instrução de reloc.</span><span class="sxs-lookup"><span data-stu-id="83a25-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="83a25-108">[in] O deslocamento da seção.</span><span class="sxs-lookup"><span data-stu-id="83a25-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="83a25-109">[in] A seção à qual `offset` refere-se.</span><span class="sxs-lookup"><span data-stu-id="83a25-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="83a25-110">[in] Um dos [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) valores, que indica o tipo da instrução de reloc a adicionar.</span><span class="sxs-lookup"><span data-stu-id="83a25-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83a25-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="83a25-111">Requirements</span></span>  
 <span data-ttu-id="83a25-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83a25-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83a25-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="83a25-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83a25-114">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="83a25-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83a25-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83a25-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83a25-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83a25-116">See also</span></span>

- [<span data-ttu-id="83a25-117">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="83a25-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
