---
title: Enumerações Protobuf-gRPC para desenvolvedores do WCF
description: Saiba como declarar e usar enumerações no Protobuf.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: d93319b713588129a19246976a82bb03a90ce680
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184235"
---
# <a name="protobuf-enumerations"></a>Enumerações Protobuf

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

O Protobuf dá suporte a tipos de enumeração, como visto na seção anterior, em que uma enumeração foi usada para `oneof` determinar o tipo de um campo. Você pode definir seus próprios tipos de enumeração e Protobuf irá compilá- C# los para tipos de enumeração. Como Protobuf pode ser usado com idiomas diferentes, as convenções de nomenclatura para enumerações são diferentes das C# convenções. No entanto, o gerador de código é inteligente e converte os nomes C# para o caso tradicional. Se o equivalente ao caso do Pascal do nome do campo começar com o nome da enumeração, ele será removido.

Por exemplo, nesta Enumeração Protobuf, os campos são prefixados `ACCOUNT_STATUS`com, que é equivalente ao nome de enumeração do caso `AccountStatus`Pascal:.

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

Portanto, o gerador cria um C# equivalente de enum para o código a seguir:

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

As definições de enumeração Protobuf **devem** ter uma constante zero como seu primeiro campo. Como no C#, você pode declarar vários campos com o mesmo valor, mas você deve habilitar explicitamente essa opção usando a `allow_alias` opção na enumeração:

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

Você pode declarar enumerações no nível superior em um `.proto` arquivo ou aninhado em uma definição de mensagem. Enumerações aninhadas — como mensagens aninhadas — serão declaradas dentro da `.Types` classe estática na classe de mensagem gerada.

Não há como aplicar o atributo [[flags]](xref:System.FlagsAttribute) a uma enumeração gerada por Protobuf, e o Protobuf não compreende combinações de enums de bits. Veja o exemplo a seguir:

```protobuf
enum Region {
  REGION_NONE = 0;
  REGION_NORTH_AMERICA = 1;
  REGION_SOUTH_AMERICA = 2;
  REGION_EMEA = 4;
  REGION_APAC = 8;
}

message Product {
  Region availableIn = 1;
}
```

Se você definir `product.AvailableIn` `Region.NorthAmerica | Region.SouthAmerica`como, ele será serializado como o valor `3`inteiro. Quando um cliente ou servidor tenta desserializar o valor, ele não encontra uma correspondência na definição de enumeração para `3` e o resultado `Region.None`será.

A melhor maneira de trabalhar com vários valores enum em Protobuf é usar um `repeated` campo do tipo enum.

>[!div class="step-by-step"]
>[Anterior](protobuf-any-oneof.md)
>[Próximo](protobuf-maps.md)
