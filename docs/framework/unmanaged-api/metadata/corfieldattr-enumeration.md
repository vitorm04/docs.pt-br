---
title: "Enumeração CorFieldAttr"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorFieldAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorFieldAttr
helpviewer_keywords: CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b199764ea0fb2d02b01d7cf04d1fa8fad743109f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corfieldattr-enumeration"></a>Enumeração CorFieldAttr
Contém valores que descrevem os metadados sobre um campo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`fdFieldAccessMask`|Especifica informações de acessibilidade.|  
|`fdPrivateScope`|Especifica que o campo não pode ser referenciado.|  
|`fdPrivate`|Especifica que o campo é acessível somente por seu tipo pai.|  
|`fdFamANDAssem`|Especifica que o campo é acessível por classes derivadas em seu assembly.|  
|`fdAssembly`|Especifica que o campo é acessível por todos os tipos em seu assembly.|  
|`fdFamily`|Especifica que o campo é acessível somente por seu tipo e classes derivadas.|  
|`fdFamORAssem`|Especifica que o campo é acessível por classes derivadas e de todos os tipos em seu assembly.|  
|`fdPublic`|Especifica que o campo é acessível por todos os tipos com visibilidade desse escopo.|  
|`fdStatic`|Especifica que o campo é um membro de seu tipo, em vez de um membro de instância.|  
|`fdInitOnly`|Especifica que o campo não pode ser alterado depois que ele é inicializado.|  
|`fdLiteral`|Especifica que o valor do campo é uma constante de tempo de compilação.|  
|`fdNotSerialized`|Especifica que o campo não é serializado ao seu tipo é remoto.|  
|`fdSpecialName`|Especifica que o campo é especial, e que descreve seu nome como.|  
|`fdPinvokeImpl`|Especifica que a implementação de campo é encaminhada por meio de PInvoke.|  
|`fdReservedMask`|Reservado para uso interno pelo common language runtime.|  
|`fdRTSpecialName`|Especifica que os metadados de tempo de execução de linguagem comum APIs interno deve verificar a codificação do nome.|  
|`fdHasFieldMarshal`|Especifica que o campo contém informações de marshaling.|  
|`fdHasDefault`|Especifica que o campo tem um valor padrão.|  
|`fdHasFieldRVA`|Especifica que o campo tem um endereço virtual relativo.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corhdr  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
