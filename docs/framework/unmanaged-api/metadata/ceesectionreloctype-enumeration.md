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
# <a name="ceesectionreloctype-enumeration"></a>Enumeração CeeSectionRelocType
Fornece valores para influenciar o tipo de instrução de `reloc` emitido em uma chamada para [ICeeGen:: AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).  
  
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
|`srRelocAbsolute`|Gera apenas um `reloc`relativo à seção, enviando nada para uma seção. realocação.|  
|`srRelocHighLow`|Gera um `reloc` para um local de tamanho de ponteiro. Isso é transformado em BASED_HIGHLOW ou BASED_DIR64 dependendo da plataforma.|  
|`srRelocHighAdj`|Gera um `reloc` para os 16 bits superiores de um número de 32 bits, em que os 16 bits inferiores são incluídos na próxima palavra na tabela. realocação.|  
|`srRelocMapToken`|Gera uma realocação de mapa de token, enviando nada para uma seção. realocação.|  
|`srRelocRelative`|Indica que o valor é uma correção de endereço relativa.|  
|`srRelocFilePos`|Gera apenas um `reloc`relativo à seção, enviando nada para uma seção. realocação. Esse `reloc` é relativo à posição do arquivo da seção, não ao endereço virtual da seção.|  
|`srRelocCodeRelative`|Especifica uma correção de endereço relativa ao código.|  
|`srRelocIA64Imm64`|Gera um `reloc` para um endereço de 64 bits em uma instrução IA64 `movl`.|  
|`srRelocDir64`|Gera um `reloc` para um endereço de 64 bits.|  
|`srRelocIA64PcRel25`|Gere um `reloc` para um endereço de 25 bits relativo a um PC em uma instrução IA64 `br.call`.|  
|`srRelocIA64PcRel64`|Gera um `reloc` para um endereço relativo a um PC de 64 bits em uma instrução IA64 `brl.call`.|  
|`srRelocAbsoluteTagged`|Gera um `reloc`relativo a uma seção de 30 bits, usado para valores de ponteiros marcados.|  
|`srRelocSentinel`|Um valor de sentinela para ajudar a garantir que todas as adições a essa enumeração sejam refletidas na matriz de nome de `reloc` interno.|  
|`srNoBaseReloc`|Especifica não emitir um `reloc`base.|  
|`srRelocPtr`|Um valor que indica que o conteúdo de ajuste prévio da memória é um ponteiro em vez de um deslocamento de seção.|  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [Interface ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [Método AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
