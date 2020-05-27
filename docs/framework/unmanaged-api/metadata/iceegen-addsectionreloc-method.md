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
ms.openlocfilehash: 2f66d34fcfdd8c61dcc92817ec1a928ac5b603fc
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008892"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="1a5af-102">Método ICeeGen::AddSectionReloc</span><span class="sxs-lookup"><span data-stu-id="1a5af-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="1a5af-103">Adiciona uma instrução. realocação à base de código.</span><span class="sxs-lookup"><span data-stu-id="1a5af-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="1a5af-104">Este método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="1a5af-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a5af-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1a5af-105">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a5af-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1a5af-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="1a5af-107">no A seção de código na memória à qual adicionar uma instrução. realocação.</span><span class="sxs-lookup"><span data-stu-id="1a5af-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="1a5af-108">no O deslocamento da seção.</span><span class="sxs-lookup"><span data-stu-id="1a5af-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="1a5af-109">no A seção à qual `offset` se refere.</span><span class="sxs-lookup"><span data-stu-id="1a5af-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="1a5af-110">no Um dos valores de [CeeSectionRelocType](ceesectionreloctype-enumeration.md) , indicando o tipo de instrução. realocação a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="1a5af-110">[in] One of the [CeeSectionRelocType](ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a5af-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1a5af-111">Requirements</span></span>  
 <span data-ttu-id="1a5af-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a5af-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a5af-113">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1a5af-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1a5af-114">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1a5af-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1a5af-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a5af-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a5af-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="1a5af-116">See also</span></span>

- [<span data-ttu-id="1a5af-117">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="1a5af-117">ICeeGen Interface</span></span>](iceegen-interface.md)
