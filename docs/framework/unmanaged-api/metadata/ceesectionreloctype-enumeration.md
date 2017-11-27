---
title: "Enumeração CeeSectionRelocType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CeeSectionRelocType
api_location: mscoree.dll
api_type: COM
f1_keywords: CeeSectionRelocType
helpviewer_keywords: CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d78b6b3867cb168e4ebf93c07f17a911e1955832
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="71591-102">Enumeração CeeSectionRelocType</span><span class="sxs-lookup"><span data-stu-id="71591-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="71591-103">Fornece valores para influenciar o tipo de `reloc` instrução emitida em uma chamada para [: Addsectionreloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span><span class="sxs-lookup"><span data-stu-id="71591-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71591-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71591-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="71591-105">Membros</span><span class="sxs-lookup"><span data-stu-id="71591-105">Members</span></span>  
  
|<span data-ttu-id="71591-106">Membro</span><span class="sxs-lookup"><span data-stu-id="71591-106">Member</span></span>|<span data-ttu-id="71591-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="71591-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="71591-108">Gera apenas um seção relativo `reloc`, enviando nada em uma seção de .reloc.</span><span class="sxs-lookup"><span data-stu-id="71591-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="71591-109">Gera um `reloc` para um local de tamanho de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="71591-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="71591-110">Isso é transformado em BASED_HIGHLOW ou BASED_DIR64 dependendo da plataforma.</span><span class="sxs-lookup"><span data-stu-id="71591-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="71591-111">Gera um `reloc` os primeiros 16 bits de um número de 32 bits, onde inferior 16 bits são incluídos na próxima palavra na tabela .reloc.</span><span class="sxs-lookup"><span data-stu-id="71591-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="71591-112">Gera uma realocação de mapa de tokens, nada será enviado em uma seção .reloc.</span><span class="sxs-lookup"><span data-stu-id="71591-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="71591-113">Indica que o valor é um endereço relativo de ajuste.</span><span class="sxs-lookup"><span data-stu-id="71591-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="71591-114">Gera apenas um seção relativo `reloc`, enviando nada em uma seção de .reloc.</span><span class="sxs-lookup"><span data-stu-id="71591-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="71591-115">Isso `reloc` é relativo a posição do arquivo da seção endereço virtual não da seção.</span><span class="sxs-lookup"><span data-stu-id="71591-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="71591-116">Especifica um endereço relativo ao código de ajuste.</span><span class="sxs-lookup"><span data-stu-id="71591-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="71591-117">Gera um `reloc` para um endereço de 64 bits em um ia64 `movl` instrução.</span><span class="sxs-lookup"><span data-stu-id="71591-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="71591-118">Gera um `reloc` para um endereço de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="71591-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="71591-119">Gerar um `reloc` para um endereço de PC relativo 25 bits em um ia64 `br.call` instrução.</span><span class="sxs-lookup"><span data-stu-id="71591-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="71591-120">Gera um `reloc` para um endereço de relativo ao computador de 64 bits em um ia64 `brl.call` instrução.</span><span class="sxs-lookup"><span data-stu-id="71591-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="71591-121">Gera um seção relativo de 30 bits `reloc`, usado para valores de ponteiro marcado.</span><span class="sxs-lookup"><span data-stu-id="71591-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="71591-122">Um valor de sentinela para garantir que quaisquer adições para este enum são refletidas em interno `reloc` matriz de nome.</span><span class="sxs-lookup"><span data-stu-id="71591-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="71591-123">Especifica que não emitir uma base de `reloc`.</span><span class="sxs-lookup"><span data-stu-id="71591-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="71591-124">Um valor que indica que o conteúdo de pré-ajuste de memória é um ponteiro em vez de uma seção de deslocamento.</span><span class="sxs-lookup"><span data-stu-id="71591-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="71591-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="71591-125">Requirements</span></span>  
 <span data-ttu-id="71591-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71591-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71591-127">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="71591-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="71591-128">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="71591-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="71591-129">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71591-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71591-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71591-130">See Also</span></span>  
 [<span data-ttu-id="71591-131">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="71591-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="71591-132">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="71591-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 [<span data-ttu-id="71591-133">Método AddSectionReloc</span><span class="sxs-lookup"><span data-stu-id="71591-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
