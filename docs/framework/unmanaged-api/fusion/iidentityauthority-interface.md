---
title: Interface IIdentityAuthority
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IIdentityAuthority
api_location: fusion.dll
api_type: COM
f1_keywords: IIdentityAuthority
helpviewer_keywords: IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 322b15252271472b5bee1dfc6a843079cebbe0b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iidentityauthority-interface"></a>Interface IIdentityAuthority
Gerencia chaves de identidade para objetos de código.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|Obtém um valor que indica se os dois especificada [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instâncias são iguais.|  
|`IIdentityAuthority::AreReferencesEqual`|Obtém um valor que indica se os dois especificada [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instâncias são iguais.|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|Obtém um valor que indica se as duas representações de identidade de definição de cadeia de caracteres especificada são iguais.|  
|`IIdentityAuthority::AreTextualReferencesEqual`|Obtém um valor que indica se as duas representações de identidade de referência de cadeia de caracteres especificada são iguais.|  
|`IIdentityAuthority::CreateDefinition`|Obtém um ponteiro para um novo `IDefinitionIdentity` instância que representa o objeto de código no escopo atual.|  
|`IIdentityAuthority::CreateReference`|Obtém um ponteiro para um novo `IReferenceIdentity` instância que representa o objeto de código no escopo atual.|  
|`IIdentityAuthority::DefinitionToText`|Obtém uma versão de cadeia de caracteres formatada especificada `IDefinitionIdentity`.|  
|`IIdentityAuthority::DefinitionToTextBuffer`|Preenche o buffer de caractere largo especificado com uma versão de cadeia de caracteres especificada `IDefinitionIdentity`.|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|Obtém um valor que indica se o especificado `IDefinitionIdentity` e `IReferenceIdentity` instâncias façam referência ao mesmo objeto de código.|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Obtém um valor que indica se as cadeias de caracteres especificadas se referem ao mesmo objeto de código.|  
|`IIdentityAuthority::GenerateDefinitionKey`|Obtém um ponteiro para uma chave de cadeia de caracteres recém-criado especificado `IDefinitionIdentity`.|  
|`IIdentityAuthority::GenerateReferenceKey`|Obtém um ponteiro para uma chave de cadeia de caracteres recém-criado especificado `IReferenceIdentity`.|  
|`IIdentityAuthority::HashDefinition`|Obtém um valor de hash especificado `IDefinitionIdentity`.|  
|`IIdentityAuthority::HashReference`|Obtém um valor de hash especificado `IreferenceIdentity`.|  
|`IIdentityAuthority::ReferenceToText`|Obtém uma versão de cadeia de caracteres formatada especificada `IReferenceIdentity`.|  
|`IIdentityAuthority::ReferenceToTextBuffer`|Preenche o buffer de caractere largo especificado com uma versão de cadeia de caracteres especificada `IReferenceIdentity`.|  
|`IIdentityAuthority::TextToDefinition`|Obtém um ponteiro de interface para um `IDefinitionIdentity` cadeia de caracteres formatada de instância gerada especificado.|  
|`IIdentityAuthority::TextToReference`|Obtém um ponteiro de interface para um `IReferenceIdentity` cadeia de caracteres formatada de instância gerada especificado.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolation.h  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
