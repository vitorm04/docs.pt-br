---
title: CorElementType Enumeration1
ms.date: 03/30/2017
api_name:
- CorElementType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorElementType
helpviewer_keywords:
- CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5112c3c8d5fef6efada4bffdfa575716503515e6
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041350"
---
# <a name="corelementtype-enumeration1"></a>CorElementType Enumeration1
Especifica um common language runtime <xref:System.Type>, um modificador de tipo ou informações sobre um tipo em uma assinatura de tipo de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorElementType {  
    ELEMENT_TYPE_END            = 0x0,  
    ELEMENT_TYPE_VOID           = 0x1,  
    ELEMENT_TYPE_BOOLEAN        = 0x2,  
    ELEMENT_TYPE_CHAR           = 0x3,  
    ELEMENT_TYPE_I1             = 0x4,  
    ELEMENT_TYPE_U1             = 0x5,  
    ELEMENT_TYPE_I2             = 0x6,  
    ELEMENT_TYPE_U2             = 0x7,  
    ELEMENT_TYPE_I4             = 0x8,  
    ELEMENT_TYPE_U4             = 0x9,  
    ELEMENT_TYPE_I8             = 0xa,  
    ELEMENT_TYPE_U8             = 0xb,  
    ELEMENT_TYPE_R4             = 0xc,  
    ELEMENT_TYPE_R8             = 0xd,  
    ELEMENT_TYPE_STRING         = 0xe,  
  
    ELEMENT_TYPE_PTR            = 0xf,  
    ELEMENT_TYPE_BYREF          = 0x10,  
  
    ELEMENT_TYPE_VALUETYPE      = 0x11,  
    ELEMENT_TYPE_CLASS          = 0x12,  
    ELEMENT_TYPE_VAR            = 0x13,  
    ELEMENT_TYPE_ARRAY          = 0x14,  
    ELEMENT_TYPE_GENERICINST    = 0x15,  
    ELEMENT_TYPE_TYPEDBYREF     = 0x16,  
  
    ELEMENT_TYPE_I              = 0x18,  
    ELEMENT_TYPE_U              = 0x19,  
    ELEMENT_TYPE_FNPTR          = 0x1B,  
    ELEMENT_TYPE_OBJECT         = 0x1C,  
    ELEMENT_TYPE_SZARRAY        = 0x1D,  
    ELEMENT_TYPE_MVAR           = 0x1e,  
  
    ELEMENT_TYPE_CMOD_REQD      = 0x1F,  
    ELEMENT_TYPE_CMOD_OPT       = 0x20,  
  
    ELEMENT_TYPE_INTERNAL       = 0x21,  
    ELEMENT_TYPE_MAX            = 0x22,  
  
    ELEMENT_TYPE_MODIFIER       = 0x40,  
    ELEMENT_TYPE_SENTINEL       = 0x01 | ELEMENT_TYPE_MODIFIER,  
    ELEMENT_TYPE_PINNED         = 0x05 | ELEMENT_TYPE_MODIFIER  
  
} CorElementType;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`ELEMENT_TYPE_END`|Usado internamente.|  
|`ELEMENT_TYPE_VOID`|Um tipo void.|  
|`ELEMENT_TYPE_BOOLEAN`|Um tipo booleano|  
|`ELEMENT_TYPE_CHAR`|Um tipo de caractere.|  
|`ELEMENT_TYPE_I1`|Um inteiro de 1 byte com sinal.|  
|`ELEMENT_TYPE_U1`|Um inteiro de 1 byte sem sinal.|  
|`ELEMENT_TYPE_I2`|Um inteiro com sinal de 2 bytes.|  
|`ELEMENT_TYPE_U2`|Um inteiro sem sinal de 2 bytes.|  
|`ELEMENT_TYPE_I4`|Um inteiro com sinal de 4 bytes.|  
|`ELEMENT_TYPE_U4`|Um inteiro sem sinal de 4 bytes.|  
|`ELEMENT_TYPE_I8`|Um inteiro com sinal de 8 bytes.|  
|`ELEMENT_TYPE_U8`|Um inteiro sem sinal de 8 bytes.|  
|`ELEMENT_TYPE_R4`|Um ponto flutuante de 4 bytes.|  
|`ELEMENT_TYPE_R8`|Um ponto flutuante de 8 bytes.|  
|`ELEMENT_TYPE_STRING`|Um tipo de System. String.|  
|`ELEMENT_TYPE_PTR`|Um modificador de tipo de ponteiro.|  
|`ELEMENT_TYPE_BYREF`|Um modificador de tipo de referência.|  
|`ELEMENT_TYPE_VALUETYPE`|Um modificador de tipo de valor.|  
|`ELEMENT_TYPE_CLASS`|Um modificador de tipo de classe.|  
|`ELEMENT_TYPE_VAR`|Um modificador de tipo de variável de classe.|  
|`ELEMENT_TYPE_ARRAY`|Um modificador de tipo de matriz multidimensional.|  
|`ELEMENT_TYPE_GENERICINST`|Um modificador de tipo para tipos genéricos.|  
|`ELEMENT_TYPE_TYPEDBYREF`|Uma referência com tipo.|  
|`ELEMENT_TYPE_I`|Tamanho de um inteiro nativo.|  
|`ELEMENT_TYPE_U`|Tamanho de um inteiro sem sinal de nativo.|  
|`ELEMENT_TYPE_FNPTR`|Um ponteiro para uma função.|  
|`ELEMENT_TYPE_OBJECT`|Um tipo de System. Object.|  
|`ELEMENT_TYPE_SZARRAY`|Um unidimensionais, zero modificador de tipo de matriz de limite inferior.|  
|`ELEMENT_TYPE_MVAR`|Um modificador de tipo de variável do método.|  
|`ELEMENT_TYPE_CMOD_REQD`|Uma linguagem C necessário modificador.|  
|`ELEMENT_TYPE_CMOD_OPT`|Um modificador opcional do idioma de C.|  
|`ELEMENT_TYPE_INTERNAL`|Usado internamente.|  
|`ELEMENT_TYPE_MAX`|Um tipo inválido.|  
|`ELEMENT_TYPE_MODIFIER`|Usado internamente.|  
|`ELEMENT_TYPE_SENTINEL`|Um modificador de tipo que é uma Sentinela para obter uma lista de um número variável de parâmetros.|  
|`ELEMENT_TYPE_PINNED`|Usado internamente.|  
  
## <a name="remarks"></a>Comentários  
 Os modificadores de tipo formam a base para representar tipos mais complexos. Um `CorElementType` valor do modificador de tipo é aplicado ao valor que vem imediatamente a seguir na assinatura de tipo. O valor que segue o `CorElementType` valor do modificador de tipo pode ser um `CorElementType` valor de tipo simples, um token de metadados ou outro valor, conforme especificado na tabela a seguir.  
  
> [!NOTE]
>  Todos os números (*número*, *argumento contagem*, *token de metadados*, *classificação*, *contagem*e *vinculado*) são armazenadas como inteiros compactados. Ver [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) no site da ECMA para obter detalhes.  
  
|Modificador de tipo|Formatar|  
|-------------------|------------|  
|`ELEMENT_TYPE_PTR`|ELEMENT_TYPE_PTR < um `CorElementType` valor >|  
|`ELEMENT_TYPE_BYREF`|ELEMENT_TYPE_BYREF < um `CorElementType` valor >|  
|`ELEMENT_TYPE_VALUETYPE`|ELEMENT_TYPE_VALUETYPE < um `mdTypeDef` token de metadados >|  
|`ELEMENT_TYPE_CLASS`|ELEMENT_TYPE_CLASS < um `mdTypeDef` token de metadados >|  
|`ELEMENT_TYPE_VAR`|ELEMENT_TYPE_VAR \<número >|  
|`ELEMENT_TYPE_ARRAY`|ELEMENT_TYPE_ARRAY < uma `CorElementType` valor > \<classificação > \<count1 > \<bound1 >... \<countN > \<boundN >|  
|`ELEMENT_TYPE_GENERICINST`|ELEMENT_TYPE_GENERICINST < uma `mdTypeDef` token de metadados > \<argumento contagem > \<arg1 >... \<argN >|  
|`ELEMENT_TYPE_FNPTR`|ELEMENT_TYPE_FNPTR \<assinatura completa para a função, incluindo a convenção de chamada >|  
|`ELEMENT_TYPE_SZARRAY`|ELEMENT_TYPE_SZARRAY < um `CorElementType` valor >|  
|`ELEMENT_TYPE_MVAR`|ELEMENT_TYPE_MVAR \<número >|  
|`ELEMENT_TYPE_CMOD_REQD`|ELEMENT_TYPE _ < uma `mdTypeRef` ou `mdTypeDef` token de metadados >|  
|`ELEMENT_TYPE_CMOD_OPT`|E_T_CMOD_OPT < uma `mdTypeRef` ou `mdTypeDef` token de metadados >|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** corhdr. H  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
