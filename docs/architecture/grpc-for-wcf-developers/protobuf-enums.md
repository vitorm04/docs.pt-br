---
title: Enumerações protobuf - gRPC para desenvolvedores WCF
description: Saiba como declarar e usar enumerações em Protobuf.
ms.date: 09/09/2019
ms.openlocfilehash: 2177f568a671fa0e651625c6e025ac70c243feb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148069"
---
# <a name="protobuf-enumerations"></a>Enumerações de Protobuf

Protobuf suporta tipos de enumeração. Você viu esse suporte na seção anterior, onde um enum foi usado para determinar o tipo de `Oneof` campo. Você pode definir seus próprios tipos de enumeração, e o Protobuf irá compilá-los para os tipos c# enum.

Como você pode usar protobuf com várias línguas, as convenções de nomeação para enumerações são diferentes das convenções C#. No entanto, o gerador de código converte os nomes para o caso C# tradicional. Se o equivalente pascal-case do nome de campo começa com o nome de enumeração, então ele é removido.

Por exemplo, na seguinte enumeração protobuf, os `ACCOUNT_STATUS`campos são prefixados com . Este prefixo é equivalente ao nome `AccountStatus`de enum pascal-case, .

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

O gerador cria um enum C# equivalente ao seguinte código:

```csharp
public enum AccountStatus
{
    Unknown = 0,
    Pending = 1,
    Active = 2,
    Suspended = 3,
    Closed = 4
}
```

As definições de enumeração de Protobuf *devem* ter uma constante zero como seu primeiro campo. Como em C#, você pode declarar vários campos com o mesmo valor. Mas você deve habilitar explicitamente `allow_alias` essa opção usando a opção no enum:

```protobuf
enum AccountStatus {
  option allow_alias = true;
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
  ACCOUNT_STATUS_CANCELLED = 4;
}
```

Você pode declarar enumerações no `.proto` nível superior em um arquivo ou aninhados dentro de uma definição de mensagem. Enumerações aninhadas — como mensagens aninhadas `.Types` — serão declaradas dentro da classe estática na classe de mensagens geradas.

Não há como aplicar o atributo [[Bandeiras]](xref:System.FlagsAttribute) a um enum gerado por Protobuf, e protobuf não entende combinações de enum bitwise. Veja o seguinte exemplo:

```protobuf
enum Region {
  REGION_NONE = 0;
  REGION_NORTH_AMERICA = 1;
  REGION_SOUTH_AMERICA = 2;
  REGION_EMEA = 4;
  REGION_APAC = 8;
}

message Product {
  Region available_in = 1;
}
```

Se você `product.AvailableIn` `Region.NorthAmerica | Region.SouthAmerica`definir para , é serializado como `3`o valor inteiro . Quando um cliente ou servidor tenta desserializar o valor, ele não `3`encontrará uma correspondência na definição de enum para . O resultado `Region.None`será .

A melhor maneira de trabalhar com múltiplos valores de `repeated` enum em Protobuf é usar um campo do tipo enum.

>[!div class="step-by-step"]
>[Próximo](protobuf-any-oneof.md)
>[anterior](protobuf-maps.md)
