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
ms.openlocfilehash: 3e2d2335e37ced9139ea44092f10b19566894681
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127091"
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
|`IIdentityAuthority::CreateDefinition`|Obtém um ponteiro para uma nova instância de `IDefinitionIdentity` que representa o objeto de código no escopo atual.|
|`IIdentityAuthority::CreateReference`|Obtém um ponteiro para uma nova instância de `IReferenceIdentity` que representa o objeto de código no escopo atual.|
|`IIdentityAuthority::DefinitionToText`|Obtém uma versão de cadeia de caracteres formatada do `IDefinitionIdentity`especificado.|
|`IIdentityAuthority::DefinitionToTextBuffer`|Preenche o buffer de caracteres largos especificado com uma versão de cadeia de caracteres do `IDefinitionIdentity`especificado.|
|`IIdentityAuthority::DoesDefinitionMatchReference`|Obtém um valor que indica se as instâncias especificadas `IDefinitionIdentity` e `IReferenceIdentity` se referem ao mesmo objeto de código.|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Obtém um valor que indica se as cadeias de caracteres especificadas se referem ao mesmo objeto de código.|
|`IIdentityAuthority::GenerateDefinitionKey`|Obtém um ponteiro para uma chave de cadeia de caracteres recém-criada para o `IDefinitionIdentity`especificado.|
|`IIdentityAuthority::GenerateReferenceKey`|Obtém um ponteiro para uma chave de cadeia de caracteres recém-criada para o `IReferenceIdentity`especificado.|
|`IIdentityAuthority::HashDefinition`|Obtém um valor de hash para o `IDefinitionIdentity`especificado.|
|`IIdentityAuthority::HashReference`|Obtém um valor de hash para o `IReferenceIdentity`especificado.|
|`IIdentityAuthority::ReferenceToText`|Obtém uma versão de cadeia de caracteres formatada do `IReferenceIdentity`especificado.|
|`IIdentityAuthority::ReferenceToTextBuffer`|Preenche o buffer de caracteres largos especificado com uma versão de cadeia de caracteres do `IReferenceIdentity`especificado.|
|`IIdentityAuthority::TextToDefinition`|Obtém um ponteiro de interface para uma instância de `IDefinitionIdentity` gerada a partir da cadeia de caracteres formatada especificada.|
|`IIdentityAuthority::TextToReference`|Obtém um ponteiro de interface para uma instância de `IReferenceIdentity` gerada a partir da cadeia de caracteres formatada especificada.|

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

**Cabeçalho:** Isolamento. h

**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Interfaces de fusão](fusion-interfaces.md)
