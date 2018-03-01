---
title: "Enumeração CorMethodImpl"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodImpl
helpviewer_keywords:
- CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e82eb50e4850ffbb4d5fc67d9603a3128cf8bcf6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cormethodimpl-enumeration"></a>Enumeração CorMethodImpl
Contém valores que descrevem os recursos de implementação de método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`miCodeTypeMask`|Sinalizadores que descrevem o tipo de código.|  
|`miIL`|Especifica que a implementação do método Microsoft intermediate language (MSIL).|  
|`miNative`|Especifica que a implementação do método é nativa.|  
|`miOPTIL`|Especifica que a implementação do método OPTIL.|  
|`miRuntime`|Especifica que a implementação do método é fornecida pelo common language runtime.|  
|`miManagedMask`|Sinalizadores que indicam se o código é gerenciado ou não.|  
|`miUnmanaged`|Especifica que a implementação do método é não gerenciada.|  
|`miManaged`|Especifica que a implementação do método é gerenciada.|  
|`miForwardRef`|Especifica que o método está definido. Este sinalizador é usado principalmente em cenários de mesclagem.|  
|`miPreserveSig`|Especifica que a assinatura do método não pode ser desconfigurada para uma conversão de HRESULT.|  
|`miInternalCall`|Reservado para uso interno pelo common language runtime.|  
|`miSynchronized`|Especifica que o método de thread único por meio de seu corpo.|  
|`miNoInlining`|Especifica que o método não pode estar em linha.|  
|`miAggressiveInlining`|Especifica que o método deve ser embutido se possível.|  
|`miNoOptimization`|Especifica que o método não deve ser otimizado.|  
|`miMaxMethodImplVal`|O valor válido máximo para um `CorMethodImpl`.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corhdr  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
