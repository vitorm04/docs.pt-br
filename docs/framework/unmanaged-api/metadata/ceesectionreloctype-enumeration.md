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
# <a name="ceesectionreloctype-enumeration"></a>Enumeração CeeSectionRelocType
Fornece valores para `reloc` influenciar o tipo de instrução emitida em uma chamada para [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
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
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`srRelocAbsolute`|Gera apenas um `reloc`parente de seção, enviando nada para uma seção .reloc.|  
|`srRelocHighLow`|Gera `reloc` um para um local do tamanho de um ponteiro. Isso é transformado em BASED_HIGHLOW ou BASED_DIR64 dependendo da plataforma.|  
|`srRelocHighAdj`|Gera `reloc` um para os 16 bits superiores de um número de 32 bits, onde os 16 bits inferiores são incluídos na próxima palavra na tabela .reloc.|  
|`srRelocMapToken`|Gera uma realocação de mapa de token, enviando nada para uma seção .reloc.|  
|`srRelocRelative`|Indica que o valor é uma correção de endereço relativo.|  
|`srRelocFilePos`|Gera apenas um `reloc`parente de seção, enviando nada para uma seção .reloc. Isso `reloc` é relativo à posição do arquivo da seção, não ao endereço virtual da seção.|  
|`srRelocCodeRelative`|Especifica uma correção de endereço relativo ao código.|  
|`srRelocIA64Imm64`|Gera `reloc` um endereço para 64 bits `movl` em uma instrução ia64.|  
|`srRelocDir64`|Gera `reloc` um para um endereço de 64 bits.|  
|`srRelocIA64PcRel25`|Gerar `reloc` um para um endereço relativo a PC de `br.call` 25 bits em uma instrução ia64.|  
|`srRelocIA64PcRel64`|Gera `reloc` um para um endereço relativo ao PC de `brl.call` 64 bits em uma instrução ia64.|  
|`srRelocAbsoluteTagged`|Gera um parente de seção de 30 bits, `reloc`usado para valores de ponteiro marcados.|  
|`srRelocSentinel`|Um valor sentinela para ajudar a garantir que quaisquer `reloc` adições a este enum sejam refletidas na matriz de nomes internos.|  
|`srNoBaseReloc`|Especifica para não emitir uma base `reloc`.|  
|`srRelocPtr`|Um valor indicando que o conteúdo pré-fixação da memória é um ponteiro em vez de um deslocamento de seção.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [Interface ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [Método AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
