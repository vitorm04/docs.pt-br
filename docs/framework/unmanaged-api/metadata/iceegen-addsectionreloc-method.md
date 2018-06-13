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
ms.openlocfilehash: c281d03c6e3774938cfa6e4b4b3a541738b38489
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444337"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="57434-102">Método ICeeGen::AddSectionReloc</span><span class="sxs-lookup"><span data-stu-id="57434-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="57434-103">Adiciona uma instrução de .reloc para a base de código.</span><span class="sxs-lookup"><span data-stu-id="57434-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="57434-104">Esse método está obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="57434-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57434-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57434-105">Syntax</span></span>  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57434-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="57434-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="57434-107">[in] A seção de código na memória ao qual adicionar uma instrução .reloc.</span><span class="sxs-lookup"><span data-stu-id="57434-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="57434-108">[in] O deslocamento da seção.</span><span class="sxs-lookup"><span data-stu-id="57434-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="57434-109">[in] A seção à qual `offset` se refere.</span><span class="sxs-lookup"><span data-stu-id="57434-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="57434-110">[in] Uma da [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) valores, que indica o tipo de instrução .reloc para adicionar.</span><span class="sxs-lookup"><span data-stu-id="57434-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57434-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57434-111">Requirements</span></span>  
 <span data-ttu-id="57434-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57434-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57434-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="57434-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57434-114">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="57434-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="57434-115">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57434-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57434-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57434-116">See Also</span></span>  
 [<span data-ttu-id="57434-117">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="57434-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
