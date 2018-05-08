---
title: Enumeração CorPEKind
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5869eb16bd768d58a6f27a83f2d8d51914a8aed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="corpekind-enumeration"></a>Enumeração CorPEKind
Contém valores que descrevem um arquivo PE (executável portátil), conforme retornado de uma chamada para [Imetadataimport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`peNot`|Indica que isso não é um arquivo PE.|  
|`peILOnly`|Indica que esse arquivo PE contém somente código gerenciado.|  
|`pe32BitRequired`|Indica que esse arquivo PE faz chamadas de Win32.|  
|`pe32Plus`|Indica que esse arquivo PE é executado em uma plataforma de 64 bits.|  
|`pe32Unmanaged`|Indica que esse arquivo PE é o código nativo.|  
|pe32BitPreferred|Indica que esse arquivo PE é plataforma neutra e prefere ser carregado em um ambiente de 32 bits.|  
  
## <a name="remarks"></a>Comentários  
 Esses valores podem ser usados em combinações de bit a bit.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corhdr  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
