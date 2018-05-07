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
ms.openlocfilehash: d4e9d03dcf4603f9470f8f2509050eb6f875746a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="corerrorifemitoutoforder-enumeration"></a>Enumeração CorErrorIfEmitOutOfOrder
Contém os valores de sinalizador que indicam as condições sob as quais uma mensagem de erro deve ser gerada quando metadados é emitido fora de ordem.  
  
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
|`MDErrorOutOfOrderAll`|Indica que o compilador deve gerar uma mensagem de erro quando um campo de propriedade, evento, método ou parâmetro é emitido fora de ordem.|  
|`MDMethodOutOfOrder`|Indica que o compilador deve gerar uma mensagem de erro quando um método é emitido fora de ordem.|  
|`MDFieldOutOfOrder`|Indica que o compilador deve gerar uma mensagem de erro quando um campo é emitido fora de ordem.|  
|`MDParamOutOfOrder`|Indica que o compilador deve gerar uma mensagem de erro quando um parâmetro é emitido fora de ordem.|  
|`MDPropertyOutOfOrder`|Indica que o compilador deve gerar uma mensagem de erro quando uma propriedade é emitida fora de ordem.|  
|`MDEventOutOfOrder`|Indica que o compilador deve gerar uma mensagem de erro quando um evento é emitido fora de ordem.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corhdr  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
