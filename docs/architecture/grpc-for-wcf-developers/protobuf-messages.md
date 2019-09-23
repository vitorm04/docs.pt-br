---
title: Mensagens Protobuf-gRPC para desenvolvedores do WCF
description: Saiba como as mensagens Protobuf são definidas em IDL e geradas C#no.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: f6bb67fe3bc37fcb49c0e69b7960a00d584307b8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184200"
---
# <a name="protobuf-messages"></a>Mensagens Protobuf

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Esta seção aborda como declarar mensagens Protobuf em `.proto` arquivos, explica os conceitos fundamentais de números e tipos de campo e examina o C# código que `protoc` é gerado pelo compilador. O restante do capítulo examinará mais detalhadamente como os diferentes tipos de dados são representados em Protobuf.

## <a name="declaring-a-message"></a>Declarando uma mensagem

No WCF, uma `Stock` classe para um aplicativo de comércio no mercado de ações pode ser definida como o exemplo a seguir:

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

Para implementar a classe equivalente em Protobuf, ela deve ser declarada `.proto` no arquivo. O `protoc` compilador então irá gerar a classe .net como parte do processo de compilação.

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string displayName = 3;
    int32 marketId = 4;

}  
```

A primeira linha declara a versão de sintaxe que está sendo usada. A versão 3 da linguagem foi lançada em 2016 e é a versão recomendada para os serviços gRPCs.

A `option csharp_namespace` linha especifica o namespace a ser usado para os tipos C# gerados. Essa opção será ignorada quando o `.proto` arquivo for compilado para outros idiomas. É comum que os arquivos Protobuf contenham opções específicas de idioma para vários idiomas.

A `Stock` definição da mensagem Especifica quatro campos, cada um com um tipo, um nome e um número de campo.

## <a name="field-numbers"></a>Números de campo

Os números de campo são uma parte importante do Protobuf. Eles são usados para identificar campos nos dados binários codificados, o que significa que eles não podem mudar de versão para versão do seu serviço. A vantagem é que a compatibilidade com versões anteriores e posteriores é possível. Os clientes e serviços simplesmente ignorarão os números de campo que não conhecem, contanto que a possibilidade de valores ausentes seja manipulada.

No formato binário, o número do campo é combinado com um identificador de tipo. Os números de campo de 1 a 15 podem ser codificados com seu tipo como um único byte; os números de 16 a 2047 levam 2 bytes. Você pode ficar mais alto se precisar de mais de 2047 campos em uma mensagem por qualquer motivo. Os identificadores de byte único para os números de campo de 1 a 15 oferecem melhor desempenho, portanto, você deve usá-los para os campos mais básicos e usados com frequência.

## <a name="types"></a>Tipos

As declarações de tipo estão usando os tipos de dados escalares nativos do Protobuf, que são abordados em mais detalhes na [próxima seção](protobuf-data-types.md). O restante deste capítulo abordará os tipos internos do Protobuf e mostrará como eles se relacionam com os tipos .NET comuns.

> [!NOTE]
> O Protobuf não dá suporte nativo `decimal` a um tipo, portanto, Double é usado em vez disso. Para aplicativos que exigem precisão decimal completa, consulte a [seção sobre decimais](protobuf-data-types.md#decimals) na próxima parte deste capítulo.

## <a name="the-generated-code"></a>O código gerado

Quando você cria seu aplicativo, o Protobuf cria classes para cada uma de suas mensagens, mapeando seus C# tipos nativos para tipos. O tipo `Stock` gerado teria a seguinte assinatura:

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

O código real gerado é muito mais complicado do que isso, pois cada classe contém todo o código necessário para serializar e desserializar para o formato de fio binário.

### <a name="property-names"></a>Nomes de propriedade

Observe que o compilador Protobuf aplicado `PascalCase` aos nomes de propriedade, embora eles `camelCase` estivessem no `.proto` arquivo. É melhor usar `camelCase` na definição de mensagem para que a geração de código para outras plataformas produza o caso esperado para suas convenções.

>[!div class="step-by-step"]
>[Anterior](protocol-buffers.md)
>[Próximo](protobuf-data-types.md)
