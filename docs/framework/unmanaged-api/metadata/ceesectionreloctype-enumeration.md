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
ms.openlocfilehash: 44a84e0752eecc1c694f3b8cf6e568b72b7d0f5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176208"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="0e410-102">Enumeração CeeSectionRelocType</span><span class="sxs-lookup"><span data-stu-id="0e410-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="0e410-103">Fornece valores para `reloc` influenciar o tipo de instrução emitida em uma chamada para [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span><span class="sxs-lookup"><span data-stu-id="0e410-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e410-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e410-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="0e410-105">Membros</span><span class="sxs-lookup"><span data-stu-id="0e410-105">Members</span></span>  
  
|<span data-ttu-id="0e410-106">Membro</span><span class="sxs-lookup"><span data-stu-id="0e410-106">Member</span></span>|<span data-ttu-id="0e410-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0e410-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="0e410-108">Gera apenas um `reloc`parente de seção, enviando nada para uma seção .reloc.</span><span class="sxs-lookup"><span data-stu-id="0e410-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="0e410-109">Gera `reloc` um para um local do tamanho de um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="0e410-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="0e410-110">Isso é transformado em BASED_HIGHLOW ou BASED_DIR64 dependendo da plataforma.</span><span class="sxs-lookup"><span data-stu-id="0e410-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="0e410-111">Gera `reloc` um para os 16 bits superiores de um número de 32 bits, onde os 16 bits inferiores são incluídos na próxima palavra na tabela .reloc.</span><span class="sxs-lookup"><span data-stu-id="0e410-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="0e410-112">Gera uma realocação de mapa de token, enviando nada para uma seção .reloc.</span><span class="sxs-lookup"><span data-stu-id="0e410-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="0e410-113">Indica que o valor é uma correção de endereço relativo.</span><span class="sxs-lookup"><span data-stu-id="0e410-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="0e410-114">Gera apenas um `reloc`parente de seção, enviando nada para uma seção .reloc.</span><span class="sxs-lookup"><span data-stu-id="0e410-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="0e410-115">Isso `reloc` é relativo à posição do arquivo da seção, não ao endereço virtual da seção.</span><span class="sxs-lookup"><span data-stu-id="0e410-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="0e410-116">Especifica uma correção de endereço relativo ao código.</span><span class="sxs-lookup"><span data-stu-id="0e410-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="0e410-117">Gera `reloc` um endereço para 64 bits `movl` em uma instrução ia64.</span><span class="sxs-lookup"><span data-stu-id="0e410-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="0e410-118">Gera `reloc` um para um endereço de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="0e410-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="0e410-119">Gerar `reloc` um para um endereço relativo a PC de `br.call` 25 bits em uma instrução ia64.</span><span class="sxs-lookup"><span data-stu-id="0e410-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="0e410-120">Gera `reloc` um para um endereço relativo ao PC de `brl.call` 64 bits em uma instrução ia64.</span><span class="sxs-lookup"><span data-stu-id="0e410-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="0e410-121">Gera um parente de seção de 30 bits, `reloc`usado para valores de ponteiro marcados.</span><span class="sxs-lookup"><span data-stu-id="0e410-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="0e410-122">Um valor sentinela para ajudar a garantir que quaisquer `reloc` adições a este enum sejam refletidas na matriz de nomes internos.</span><span class="sxs-lookup"><span data-stu-id="0e410-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="0e410-123">Especifica para não emitir uma base `reloc`.</span><span class="sxs-lookup"><span data-stu-id="0e410-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="0e410-124">Um valor indicando que o conteúdo pré-fixação da memória é um ponteiro em vez de um deslocamento de seção.</span><span class="sxs-lookup"><span data-stu-id="0e410-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e410-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0e410-125">Requirements</span></span>  
 <span data-ttu-id="0e410-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e410-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e410-127">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0e410-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e410-128">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0e410-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0e410-129">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e410-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e410-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="0e410-130">See also</span></span>

- [<span data-ttu-id="0e410-131">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="0e410-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="0e410-132">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="0e410-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [<span data-ttu-id="0e410-133">Método AddSectionReloc</span><span class="sxs-lookup"><span data-stu-id="0e410-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
