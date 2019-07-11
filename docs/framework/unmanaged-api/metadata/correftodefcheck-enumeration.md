---
title: Enumeração CorRefToDefCheck
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ae87dd4538a9a8e88591f498c0ce77b51bfa852
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781614"
---
# <a name="correftodefcheck-enumeration"></a>Enumeração CorRefToDefCheck
Especifica sinalizadores para controlar quais itens referenciados são convertidos em suas definições para otimizar o código.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`MDRefToDefDefault`|Especifica que as referências de tipo e membro devem ser convertidas em definições. Esse é o valor padrão (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).|  
|`MDRefToDefAll`|Especifica que todos os itens referenciados devem ser convertidos em definições.|  
|`MDRefToDefNone`|Especifica que nenhum item referenciado deve ser convertido para definições.|  
|`MDTypeRefToDef`|Especifica que somente as referências de tipo devem ser convertidas para definições de tipo.|  
|`MDMemberRefToDef`|Especifica que somente as referências de membro devem ser convertidas em definições. Ou seja, as referências de membro devem ser convertidas em definições de método ou definições de campo.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
