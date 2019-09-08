---
title: Interface IIdentityAuthority
ms.date: 03/30/2017
api_name:
- IIdentityAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IIdentityAuthority
helpviewer_keywords:
- IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7421e0d0e1a1f0e1a5fbe0d0eb7d5a0ab2a48b9a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796429"
---
# <a name="iidentityauthority-interface"></a>Interface IIdentityAuthority

Gerencia chaves de identidade para objetos de código.

## <a name="methods"></a>Métodos

|Método|Descrição|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|Obtém um valor que indica se as duas instâncias de [IDefinitionIdentity](idefinitionidentity-interface.md) especificadas são iguais.|
|`IIdentityAuthority::AreReferencesEqual`|Obtém um valor que indica se as duas instâncias de [IReferenceIdentity](ireferenceidentity-interface.md) especificadas são iguais.|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|Obtém um valor que indica se as duas representações de identidade de definição de cadeia de caracteres especificadas são iguais.|
|`IIdentityAuthority::AreTextualReferencesEqual`|Obtém um valor que indica se as duas representações de identidade de referência de cadeia de caracteres especificadas são iguais.|
|`IIdentityAuthority::CreateDefinition`|Obtém um ponteiro para uma nova `IDefinitionIdentity` instância que representa o objeto de código no escopo atual.|
|`IIdentityAuthority::CreateReference`|Obtém um ponteiro para uma nova `IReferenceIdentity` instância que representa o objeto de código no escopo atual.|
|`IIdentityAuthority::DefinitionToText`|Obtém uma versão de cadeia de caracteres formatada `IDefinitionIdentity`do especificada.|
|`IIdentityAuthority::DefinitionToTextBuffer`|Preenche o buffer de caracteres largos especificado com uma versão de cadeia `IDefinitionIdentity`de caracteres do especificado.|
|`IIdentityAuthority::DoesDefinitionMatchReference`|Obtém um valor que indica se as instâncias `IDefinitionIdentity` especificadas `IReferenceIdentity` e se referem ao mesmo objeto de código.|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Obtém um valor que indica se as cadeias de caracteres especificadas se referem ao mesmo objeto de código.|
|`IIdentityAuthority::GenerateDefinitionKey`|Obtém um ponteiro para uma chave de cadeia de caracteres recém-criada para `IDefinitionIdentity`o especificado.|
|`IIdentityAuthority::GenerateReferenceKey`|Obtém um ponteiro para uma chave de cadeia de caracteres recém-criada para `IReferenceIdentity`o especificado.|
|`IIdentityAuthority::HashDefinition`|Obtém um valor de hash para o `IDefinitionIdentity`especificado.|
|`IIdentityAuthority::HashReference`|Obtém um valor de hash para o `IReferenceIdentity`especificado.|
|`IIdentityAuthority::ReferenceToText`|Obtém uma versão de cadeia de caracteres formatada `IReferenceIdentity`do especificada.|
|`IIdentityAuthority::ReferenceToTextBuffer`|Preenche o buffer de caracteres largos especificado com uma versão de cadeia `IReferenceIdentity`de caracteres do especificado.|
|`IIdentityAuthority::TextToDefinition`|Obtém um ponteiro de interface para `IDefinitionIdentity` uma instância gerada a partir da cadeia de caracteres formatada especificada.|
|`IIdentityAuthority::TextToReference`|Obtém um ponteiro de interface para `IReferenceIdentity` uma instância gerada a partir da cadeia de caracteres formatada especificada.|

## <a name="requirements"></a>Requisitos

**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).

**Cabeçalho:** Isolamento. h

**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Interfaces de fusão](fusion-interfaces.md)
