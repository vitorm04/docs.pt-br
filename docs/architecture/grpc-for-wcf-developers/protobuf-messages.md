---
title: Mensagens protobuf - gRPC para desenvolvedores WCF
description: Saiba como as mensagens Protobuf são definidas no IDL e geradas em C#.
ms.date: 09/09/2019
ms.openlocfilehash: 5b3d4383de39a3785ef804fec21939a740f54669
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147978"
---
# <a name="protobuf-messages"></a>Mensagens de Protobuf

Esta seção abrange como declarar mensagens de Buffer `.proto` de Protocolo (Protobuf) em arquivos. Ele explica os conceitos fundamentais de números de campo e `protoc` tipos, e olha para o código C# que o compilador gera.

O resto do capítulo analisará com mais detalhes como diferentes tipos de dados são representados no Protobuf.

## <a name="declaring-a-message"></a>Declarando uma mensagem

No Windows Communication Foundation (WCF), uma `Stock` classe para um aplicativo de negociação no mercado de ações pode ser definida como o seguinte exemplo:

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

Para implementar a classe equivalente em Protobuf, `.proto` você deve declará-la no arquivo. O `protoc` compilador gerará a classe .NET como parte do processo de compilação.

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

A primeira linha declara a versão de sintaxe sendo usada. A versão 3 do idioma foi lançada em 2016. É a versão que recomendamos para os serviços gRPC.

A `option csharp_namespace` linha especifica o namespace a ser usado para os tipos C# gerados. Essa opção será ignorada `.proto` quando o arquivo for compilado para outros idiomas. Os arquivos protobuf geralmente contêm opções específicas do idioma para vários idiomas.

A `Stock` definição da mensagem especifica quatro campos. Cada um tem um tipo, um nome e um número de campo.

## <a name="field-numbers"></a>Números de campo

Os números de campo são uma parte importante do Protobuf. Eles são usados para identificar campos nos dados codificados binários, o que significa que eles não podem mudar de versão para versão do seu serviço. A vantagem é que a compatibilidade retrógrada e a compatibilidade avançada são possíveis. Clientes e serviços simplesmente ignorarão os números de campo que eles desconhecem, desde que a possibilidade de valores perdidos seja tratada.

No formato binário, o número de campo é combinado com um identificador de tipo. Os números de campo de 1 a 15 podem ser codificados com seu tipo como um único byte. Números de 16 a 2.047 levam 2 bytes. Você pode ir mais alto se precisar de mais de 2.047 campos em uma mensagem por qualquer motivo. Os identificadores single byte para números de campo de 1 a 15 oferecem melhor desempenho, então você deve usá-los para os campos mais básicos e usados com freqüência.

## <a name="types"></a>Tipos

As declarações do tipo estão usando os tipos de dados escalares nativos da Protobuf, que são discutidos com mais detalhes [na próxima seção](protobuf-data-types.md). O resto deste capítulo cobrirá os tipos incorporados do Protobuf e mostrará como eles se relacionam com tipos comuns .NET.

> [!NOTE]
> Protobuf não suporta nativamente `decimal` um tipo, por isso `double` é usado em vez disso. Para aplicações que requerem precisão decimal total, consulte a [seção em decimais](protobuf-data-types.md#decimals) na próxima parte deste capítulo.

## <a name="the-generated-code"></a>O código gerado

Quando você constrói seu aplicativo, o Protobuf cria classes para cada uma de suas mensagens, mapeando seus tipos nativos para tipos C#. O `Stock` tipo gerado teria a seguinte assinatura:

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

O código real gerado é muito mais complicado do que isso. A razão é que cada classe contém todo o código necessário para serializar e desserializar-se ao formato de fio binário.

### <a name="property-names"></a>Nomes de propriedades

Observe que o compilador Protobuf se inscreveu `PascalCase` nos `snake_case` nomes `.proto` da propriedade, embora estivessem no arquivo. O [guia de estilo Protobuf](https://developers.google.com/protocol-buffers/docs/style) recomenda usar `snake_case` em suas definições de mensagem para que a geração de código para outras plataformas produza o caso esperado para suas convenções.

>[!div class="step-by-step"]
>[Próximo](protocol-buffers.md)
>[anterior](protobuf-data-types.md)
