---
title: Interface IAssemblyName
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName
helpviewer_keywords: IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1d11889ab9db408b6e703bbaec17fd0487f142a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblyname-interface"></a>Interface IAssemblyName
Fornece métodos para descrever e trabalhar com uma identidade exclusiva de assembly.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método clone](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|Cria uma cópia superficial deste `IAssemblyName` objeto.|  
|[Método Finalize](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|Permite que este `IAssemblyName` objeto para liberar recursos e executar outras operações de limpeza antes do destruidor é chamado.|  
|[Método GetDisplayName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|Obtém o nome legível do assembly referenciado por essa `IAssemblyName` objeto.|  
|[Método GetName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|Obtém o nome simple, não criptografado do assembly referenciado por essa `IAssemblyName` objeto.|  
|[Método GetProperty](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|Obtém um ponteiro para a propriedade referenciada pelo `PropertyId`.|  
|[Método GetVersion](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|Obtém as informações de versão do assembly referenciado por essa `IAssemblyName` objeto.|  
|[Método IsEqual](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|Determina se um especificado `IAssemblyName` objeto é igual a este `IAssemblyName`, com base nos sinalizadores de comparação especificado.|  
|[Método SetProperty](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|Define o valor da propriedade referenciada pelo `PropertyId`.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [Interface IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
