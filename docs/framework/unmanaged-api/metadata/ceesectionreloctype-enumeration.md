---
title: Enumeração CeeSectionRelocType
ms.date: 03/30/2017
api_name:
- CeeSectionRelocType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocType
helpviewer_keywords:
- CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type:
- apiref
ms.openlocfilehash: efce0c13944b383c42cbff6a6af4795293ee2989
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444161"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="adda3-102">Enumeração CeeSectionRelocType</span><span class="sxs-lookup"><span data-stu-id="adda3-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="adda3-103">Fornece valores para influenciar o tipo de instrução de `reloc` emitido em uma chamada para [ICeeGen:: AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span><span class="sxs-lookup"><span data-stu-id="adda3-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adda3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="adda3-104">Syntax</span></span>  
  
```cpp  
typedef enum  {  
    srRelocAbsolute,  
    srRelocHighLow          = 3,  
    srRelocHighAdj,       
    srRelocMapToken,  
    srRelocRelative,  
    srRelocFilePos,  
    srRelocCodeRelative,  
    srRelocIA64Imm64,  
    srRelocDir64,  
    srRelocIA64PcRel25,  
    srRelocIA64PcRel64,    srRelocAbsoluteTagged,    srRelocSentinel,    srNoBaseReloc       = 0x4000,  
    srRelocPtr          = 0x8000,  
    srRelocAbsolutePtr      = srRelocPtr + srRelocAbsolute,  
    srRelocHighLowPtr       = srRelocPtr + srRelocHighLow,  
    srRelocRelativePtr      = srRelocPtr + srRelocRelative,  
    srRelocIA64Imm64Ptr     = srRelocPtr + srRelocIA64Imm64,  
    srRelocDir64Ptr         = srRelocPtr + srRelocDir64  
    } CeeSectionRelocType;  
```  
  
## <a name="members"></a><span data-ttu-id="adda3-105">Membros</span><span class="sxs-lookup"><span data-stu-id="adda3-105">Members</span></span>  
  
|<span data-ttu-id="adda3-106">Membro</span><span class="sxs-lookup"><span data-stu-id="adda3-106">Member</span></span>|<span data-ttu-id="adda3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="adda3-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="adda3-108">Gera apenas um `reloc`relativo à seção, enviando nada para uma seção. realocação.</span><span class="sxs-lookup"><span data-stu-id="adda3-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="adda3-109">Gera um `reloc` para um local de tamanho de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="adda3-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="adda3-110">Isso é transformado em BASED_HIGHLOW ou BASED_DIR64 dependendo da plataforma.</span><span class="sxs-lookup"><span data-stu-id="adda3-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="adda3-111">Gera um `reloc` para os 16 bits superiores de um número de 32 bits, em que os 16 bits inferiores são incluídos na próxima palavra na tabela. realocação.</span><span class="sxs-lookup"><span data-stu-id="adda3-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="adda3-112">Gera uma realocação de mapa de token, enviando nada para uma seção. realocação.</span><span class="sxs-lookup"><span data-stu-id="adda3-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="adda3-113">Indica que o valor é uma correção de endereço relativa.</span><span class="sxs-lookup"><span data-stu-id="adda3-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="adda3-114">Gera apenas um `reloc`relativo à seção, enviando nada para uma seção. realocação.</span><span class="sxs-lookup"><span data-stu-id="adda3-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="adda3-115">Esse `reloc` é relativo à posição do arquivo da seção, não ao endereço virtual da seção.</span><span class="sxs-lookup"><span data-stu-id="adda3-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="adda3-116">Especifica uma correção de endereço relativa ao código.</span><span class="sxs-lookup"><span data-stu-id="adda3-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="adda3-117">Gera um `reloc` para um endereço de 64 bits em uma instrução IA64 `movl`.</span><span class="sxs-lookup"><span data-stu-id="adda3-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="adda3-118">Gera um `reloc` para um endereço de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="adda3-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="adda3-119">Gere um `reloc` para um endereço de 25 bits relativo a um PC em uma instrução IA64 `br.call`.</span><span class="sxs-lookup"><span data-stu-id="adda3-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="adda3-120">Gera um `reloc` para um endereço relativo a um PC de 64 bits em uma instrução IA64 `brl.call`.</span><span class="sxs-lookup"><span data-stu-id="adda3-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="adda3-121">Gera um `reloc`relativo a uma seção de 30 bits, usado para valores de ponteiros marcados.</span><span class="sxs-lookup"><span data-stu-id="adda3-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="adda3-122">Um valor de sentinela para ajudar a garantir que todas as adições a essa enumeração sejam refletidas na matriz de nome de `reloc` interno.</span><span class="sxs-lookup"><span data-stu-id="adda3-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="adda3-123">Especifica não emitir um `reloc`base.</span><span class="sxs-lookup"><span data-stu-id="adda3-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="adda3-124">Um valor que indica que o conteúdo de ajuste prévio da memória é um ponteiro em vez de um deslocamento de seção.</span><span class="sxs-lookup"><span data-stu-id="adda3-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="adda3-125">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="adda3-125">Requirements</span></span>  
 <span data-ttu-id="adda3-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adda3-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adda3-127">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="adda3-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="adda3-128">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="adda3-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="adda3-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adda3-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adda3-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="adda3-130">See also</span></span>

- [<span data-ttu-id="adda3-131">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="adda3-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="adda3-132">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="adda3-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [<span data-ttu-id="adda3-133">Método AddSectionReloc</span><span class="sxs-lookup"><span data-stu-id="adda3-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
