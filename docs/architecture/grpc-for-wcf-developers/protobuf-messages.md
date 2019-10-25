---
title: Mensagens Protobuf-gRPC para desenvolvedores do WCF
description: Saiba como as mensagens Protobuf são definidas em IDL e geradas C#no.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 9943478698acfbb54b3e1dd0e6a856d11b9266c3
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846336"
---
# <a name="protobuf-messages"></a>Mensagens de Protobuf

Esta seção aborda como declarar mensagens Protobuf em arquivos `.proto`, explica os conceitos fundamentais de números e tipos de campo e examina o C# código gerado pelo compilador de `protoc`. O restante do capítulo examinará mais detalhadamente como os diferentes tipos de dados são representados em Protobuf.

## <a name="declaring-a-message"></a>Declarando uma mensagem

No WCF, uma classe de `Stock` para um aplicativo de comércio no mercado de ações pode ser definida como o exemplo a seguir:

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

Para implementar a classe equivalente em Protobuf, ela deve ser declarada no arquivo `.proto`. O compilador de `protoc` irá gerar a classe .NET como parte do processo de compilação.

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

A primeira linha declara a versão de sintaxe que está sendo usada. A versão 3 da linguagem foi lançada em 2016 e é a versão recomendada para os serviços gRPCs.

A linha de `option csharp_namespace` especifica o namespace a ser usado para os C# tipos gerados. Essa opção será ignorada quando o arquivo de `.proto` for compilado para outros idiomas. É comum que os arquivos Protobuf contenham opções específicas de idioma para vários idiomas.

A definição da mensagem de `Stock` especifica quatro campos, cada um com um tipo, um nome e um número de campo.

## <a name="field-numbers"></a>Números de campo

Os números de campo são uma parte importante do Protobuf. Eles são usados para identificar campos nos dados binários codificados, o que significa que eles não podem mudar de versão para versão do seu serviço. A vantagem é que a compatibilidade com versões anteriores e posteriores é possível. Os clientes e serviços simplesmente ignorarão os números de campo que não conhecem, contanto que a possibilidade de valores ausentes seja manipulada.

No formato binário, o número do campo é combinado com um identificador de tipo. Os números de campo de 1 a 15 podem ser codificados com seu tipo como um único byte; os números de 16 a 2047 levam 2 bytes. Você pode ficar mais alto se precisar de mais de 2047 campos em uma mensagem por qualquer motivo. Os identificadores de byte único para os números de campo de 1 a 15 oferecem melhor desempenho, portanto, você deve usá-los para os campos mais básicos e usados com frequência.

## <a name="types"></a>Tipos

As declarações de tipo estão usando os tipos de dados escalares nativos do Protobuf, que são abordados em mais detalhes na [próxima seção](protobuf-data-types.md). O restante deste capítulo abordará os tipos internos do Protobuf e mostrará como eles se relacionam com os tipos .NET comuns.

> [!NOTE]
> O Protobuf não dá suporte nativo a um tipo de `decimal`, portanto, Double é usado em vez disso. Para aplicativos que exigem precisão decimal completa, consulte a [seção sobre decimais](protobuf-data-types.md#decimals) na próxima parte deste capítulo.

## <a name="the-generated-code"></a>O código gerado

Quando você cria seu aplicativo, o Protobuf cria classes para cada uma de suas mensagens, mapeando seus C# tipos nativos para tipos. O tipo de `Stock` gerado teria a seguinte assinatura:

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

Observe que o compilador Protobuf aplicou `PascalCase` aos nomes de propriedade, embora eles fossem `snake_case` no arquivo `.proto`. O [Guia de estilo Protobuf](https://developers.google.com/protocol-buffers/docs/style) recomenda o uso de `snake_case` em suas definições de mensagem para que a geração de código para outras plataformas produza o caso esperado para suas convenções.

>[!div class="step-by-step"]
>[Anterior](protocol-buffers.md)
>[Próximo](protobuf-data-types.md)
