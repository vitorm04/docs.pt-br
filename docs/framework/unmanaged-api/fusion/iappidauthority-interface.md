---
title: Interface IAppIdAuthority
ms.date: 03/30/2017
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 724ee01e91f1e9f4e34d2262610152a977ed4f53
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206649"
---
# <a name="iappidauthority-interface"></a>Interface IAppIdAuthority
Fornece métodos que geram e comparam chaves para as identidades de aplicativo e referências.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|Obtém um valor que indica se os dois especificada [IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) instâncias são iguais. Você pode passar o valor do sinalizador IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION para ignorar as informações de sua respectiva versão.|  
|`IAppIdAuthority::AreReferencesEqual`|Obtém um valor que indica se os dois especificada [IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) instâncias são iguais. Você pode passar o valor do sinalizador IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION para ignorar as informações de sua respectiva versão.|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|Obtém um valor que indica se as duas definições de cadeia de caracteres especificada são iguais. Você pode passar o valor do sinalizador IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION para ignorar as informações de sua respectiva versão.|  
|`IAppIdAuthority::AreTextualReferencesEqual`|Obtém um valor que indica se as duas referências de cadeia de caracteres especificada são iguais. Você pode passar o valor do sinalizador IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION para ignorar as informações de sua respectiva versão.|  
|`IAppIdAuthority::CreateDefinition`|Obtém um ponteiro de interface para um recém-gerado `IDefinitionAppId` instância que representa o assembly no escopo atual.|  
|`IAppIdAuthority::CreateReference`|Obtém um ponteiro de interface recém-criado para um `IReferenceAppId` que representa o assembly no escopo atual.|  
|`IAppIdAuthority::DefinitionToText`|Obtém uma versão de cadeia de caracteres especificada `IDefinitionAppId`, usando os valores de sinalizador especificado.|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|Obtém um valor que indica se a especificada `IDefinitionAppId` e `IReferenceAppId` representam o mesmo assembly.|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|Obtém um valor que indica se a cadeia de caracteres da definição especificada e a cadeia de caracteres de referência representam o mesmo assembly.|  
|`IAppIdAuthority::GenerateDefinitionKey`|Obtém uma chave de cadeia de caracteres que representa a `IDefinitionAppId` instância.|  
|`IAppIdAuthority::GenerateReferenceKey`|Obtém uma chave de cadeia de caracteres que representa a `IReferenceAppId` instância.|  
|`IAppIdAuthority::HashDefinition`|Obtém uma chave de hash especificado `IDefinitionAppId` instância.|  
|`IAppIdAuthority::HashReference`|Obtém uma chave de hash especificado `IReferenceAppId` instância.|  
|`IAppIdAuthority::ReferenceToText`|Obtém uma versão de cadeia de caracteres especificada `IReferenceAppId`, usando os valores de sinalizador especificado.|  
|`IAppIdAuthority::TextToDefinition`|Obtém um ponteiro de interface para um `IDefinitionAppId` instância que representa o assembly referenciado pela chave de cadeia de caracteres especificada.|  
|`IAppIdAuthority::TextToReference`|Obtém um ponteiro de interface para um `IReferenceAppId` instância que representa o assembly referenciado pela chave de cadeia de caracteres especificada.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolation.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
