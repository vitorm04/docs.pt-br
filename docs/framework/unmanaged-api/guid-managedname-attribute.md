---
title: Atributo GUID_ManagedName
ms.date: 03/30/2017
api_name:
- GUID_ManagedName
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GUID_ManagedName
helpviewer_keywords:
- GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type:
- apiref
ms.openlocfilehash: 9d30c8fe71a0dfff7de9bb2f43b325cbb8016a23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123048"
---
# <a name="guid_managedname-attribute"></a>Atributo GUID_ManagedName
Define um atributo de interface personalizado que especifica o nome do namespace gerenciado para uma biblioteca COM (Component Object Model).  
  
## <a name="syntax"></a>Sintaxe  
  
```idl
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a>Parâmetros  
 `value`  
 O nome do namespace gerenciado para a biblioteca.  
  
## <a name="definition"></a>Definição  
 `GUID_ManagedName` é definido em cor. h da seguinte maneira:  
  
```cpp
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a>Comentários  
 Um atributo de interface personalizado define os metadados de um objeto na biblioteca de tipos.  
  
 Use <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> ou <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> para recuperar o nome gerenciado do atributo.  
  
 Para obter mais informações, consulte [atributos de interface](/cpp/windows/attributes/interface-attributes) na C++ documentação de referência visual.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma definição de biblioteca usando o atributo `GUID_ManagedName`.  
  
```idl
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** Cor. h
