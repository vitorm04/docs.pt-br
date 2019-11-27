---
title: Enumeração CorAttributeTargets
ms.date: 03/30/2017
api_name:
- CorAttributeTargets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAttributeTargets
helpviewer_keywords:
- CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type:
- apiref
ms.openlocfilehash: 5f83cb96e39b257a1d35786130cd5ed31d071de7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443874"
---
# <a name="corattributetargets-enumeration"></a>Enumeração CorAttributeTargets
{1&gt;Especifica os elementos do aplicativo no qual ele é válido para aplicar um atributo.&lt;1}  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =   
        catAssembly | catModule | catClass | catStruct |   
        catEnum | catConstructor | catMethod | catProperty |   
        catField | catEvent | catInterface | catParameter |   
        catDelegate | catGenericParameter,  
  
    catClassMembers        =   
        catClass | catStruct | catEnum | catConstructor |   
        catMethod | catProperty | catField | catEvent |   
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a>Membros  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`catAssembly`|O atributo pode ser aplicado a um assembly.|  
|`catModule`|O atributo pode ser aplicado a um módulo executável portátil (. dll ou. exe).|  
|`catClass`|O atributo pode ser aplicado a uma classe.|  
|`catStruct`|Atributo pode ser aplicado a uma estrutura; ou seja, um tipo de valor.|  
|`catEnum`|O atributo pode ser aplicado a uma enumeração.|  
|`catConstructor`|O atributo pode ser aplicado a um construtor.|  
|`catMethod`|O atributo pode ser aplicado a um método.|  
|`catProperty`|O atributo pode ser aplicado a uma propriedade.|  
|`catField`|O atributo pode ser aplicado a um campo.|  
|`catEvent`|O atributo pode ser aplicado a um evento.|  
|`catInterface`|O atributo pode ser aplicado a uma interface.|  
|`catParameter`|O atributo pode ser aplicado a um parâmetro.|  
|`catDelegate`|O atributo pode ser aplicado a um delegado.|  
|`catGenericParameter`|O atributo pode ser aplicado a um parâmetro genérico.|  
|`catAll`|O atributo pode ser aplicado a qualquer elemento de aplicativo.|  
|`catClassMembers`|O atributo pode ser aplicado a um membro de uma classe.|  
  
## <a name="remarks"></a>Comentários  
 Os valores de enumeração de `CorAttributeTargets` podem ser combinados com uma operação OR bit a bit para obter a combinação preferida.  
  
 O `CorAttributeTargets` paraleliza a enumeração de <xref:System.AttributeTargets?displayProperty=nameWithType> gerenciada.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
