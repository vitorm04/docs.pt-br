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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: babd7d87f1bb6f238c347d68814a3ecdaef64b40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ceesectionreloctype-enumeration"></a>Enumeração CeeSectionRelocType
Fornece valores para influenciar o tipo de `reloc` instrução emitida em uma chamada para [: Addsectionreloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
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
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`srRelocAbsolute`|Gera apenas um seção relativo `reloc`, enviando nada em uma seção de .reloc.|  
|`srRelocHighLow`|Gera um `reloc` para um local de tamanho de ponteiro. Isso é transformado em BASED_HIGHLOW ou BASED_DIR64 dependendo da plataforma.|  
|`srRelocHighAdj`|Gera um `reloc` os primeiros 16 bits de um número de 32 bits, onde inferior 16 bits são incluídos na próxima palavra na tabela .reloc.|  
|`srRelocMapToken`|Gera uma realocação de mapa de tokens, nada será enviado em uma seção .reloc.|  
|`srRelocRelative`|Indica que o valor é um endereço relativo de ajuste.|  
|`srRelocFilePos`|Gera apenas um seção relativo `reloc`, enviando nada em uma seção de .reloc. Isso `reloc` é relativo a posição do arquivo da seção endereço virtual não da seção.|  
|`srRelocCodeRelative`|Especifica um endereço relativo ao código de ajuste.|  
|`srRelocIA64Imm64`|Gera um `reloc` para um endereço de 64 bits em um ia64 `movl` instrução.|  
|`srRelocDir64`|Gera um `reloc` para um endereço de 64 bits.|  
|`srRelocIA64PcRel25`|Gerar um `reloc` para um endereço de PC relativo 25 bits em um ia64 `br.call` instrução.|  
|`srRelocIA64PcRel64`|Gera um `reloc` para um endereço de relativo ao computador de 64 bits em um ia64 `brl.call` instrução.|  
|`srRelocAbsoluteTagged`|Gera um seção relativo de 30 bits `reloc`, usado para valores de ponteiro marcado.|  
|`srRelocSentinel`|Um valor de sentinela para garantir que quaisquer adições para este enum são refletidas em interno `reloc` matriz de nome.|  
|`srNoBaseReloc`|Especifica que não emitir uma base de `reloc`.|  
|`srRelocPtr`|Um valor que indica que o conteúdo de pré-ajuste de memória é um ponteiro em vez de uma seção de deslocamento.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [Interface ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 [Método AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
