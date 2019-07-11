---
title: Enumeração CorSerializationType
ms.date: 03/30/2017
api_name:
- CorSerializationType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSerializationType
helpviewer_keywords:
- CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9b7138d403bc84ab377301b82d697fd137416c6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781587"
---
# <a name="corserializationtype-enumeration"></a>Enumeração CorSerializationType
Especifica como um objeto é serializado pelo common language runtime.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|A serialização do objeto é indefinida.|  
|`SERIALIZATION_TYPE_BOOLEAN`|O objeto é serializado como um tipo booleano|  
|`SERIALIZATION_TYPE_CHAR`|O objeto é serializado como um tipo de caractere.|  
|`SERIALIZATION_TYPE_I1`|O objeto é serializado como um inteiro de 1 byte com sinal.|  
|`SERIALIZATION_TYPE_U1`|O objeto é serializado como um inteiro de 1 byte sem sinal.|  
|`SERIALIZATION_TYPE_I2`|O objeto é serializado como um inteiro com sinal de 2 bytes.|  
|`SERIALIZATION_TYPE_U2`|O objeto é serializado como um inteiro sem sinal de 2 bytes.|  
|`SERIALIZATION_TYPE_I4`|O objeto é serializado como um inteiro com sinal de 4 bytes.|  
|`SERIALIZATION_TYPE_U4`|O objeto é serializado como um inteiro sem sinal de 4 bytes.|  
|`SERIALIZATION_TYPE_I8`|O objeto é serializado como um inteiro com sinal de 8 bytes.|  
|`SERIALIZATION_TYPE_U8`|O objeto é serializado como um inteiro sem sinal de 8 bytes.|  
|`SERIALIZATION_TYPE_R4`|O objeto é serializado como um ponto flutuante de 4 bytes.|  
|`SERIALIZATION_TYPE_R8`|O objeto é serializado como um ponto flutuante de 8 bytes.|  
|`SERIALIZATION_TYPE_STRING`|O objeto é serializado como um tipo de System. String.|  
|`SERIALIZATION_TYPE_SZARRAY`|O objeto é serializado como um unidimensionais, zero matriz de limite inferior.|  
|`SERIALIZATION_TYPE_TYPE`|O objeto é serializado como um tipo genérico.|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|O objeto é serializado como um objeto marcado.|  
|`SERIALIZATION_TYPE_FIELD`|O objeto é serializado como um campo.|  
|`SERIALIZATION_TYPE_PROPERTY`|O objeto é serializado como uma propriedade.|  
|`SERIALIZATION_TYPE_ENUM`|O objeto é serializado como uma enumeração.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
