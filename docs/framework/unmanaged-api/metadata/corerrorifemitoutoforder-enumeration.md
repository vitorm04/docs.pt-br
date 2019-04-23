---
title: Enumeração CorErrorIfEmitOutOfOrder
ms.date: 03/30/2017
api_name:
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 628ca1b555d80319312450d784981cfed1bda947
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160440"
---
# <a name="corerrorifemitoutoforder-enumeration"></a>Enumeração CorErrorIfEmitOutOfOrder
Contém valores de sinalizador para indicam as condições sob as quais uma mensagem de erro deve ser gerada quando metadados é emitido fora de ordem.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|Indica o comportamento padrão, que não geram mensagens de erro.|  
|`MDErrorOutOfOrderNone`|Indica que o compilador não deve gerar mensagens de erro.|  
|`MDErrorOutOfOrderAll`|Indica que o compilador deve gerar uma mensagem de erro quando um campo, a propriedade, o evento, o método ou parâmetro é emitido fora de ordem.|  
|`MDMethodOutOfOrder`|Indica que o compilador deve gerar uma mensagem de erro quando um método é emitido fora de ordem.|  
|`MDFieldOutOfOrder`|Indica que o compilador deve gerar uma mensagem de erro quando um campo é emitido fora de ordem.|  
|`MDParamOutOfOrder`|Indica que o compilador deve gerar uma mensagem de erro quando um parâmetro é emitido fora de ordem.|  
|`MDPropertyOutOfOrder`|Indica que o compilador deve gerar uma mensagem de erro quando uma propriedade é emitida fora de ordem.|  
|`MDEventOutOfOrder`|Indica que o compilador deve gerar uma mensagem de erro quando um evento é emitido fora de ordem.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
