---
title: Atributos em C# - um tour pela linguagem C#
description: Saiba mais sobre a programação declarativa usando atributos no C#
ms.date: 08/10/2016
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: 671023f268ae78d63db8868ef6046b8f13880659
ms.sourcegitcommit: 78bcb629abdbdbde0e295b4e81f350a477864aba
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/08/2018
ms.locfileid: "34312229"
---
# <a name="attributes"></a>Atributos

Tipos, membros e outras entidades em um programa C# dão suporte a modificadores que controlam determinados aspectos de seu comportamento. Por exemplo, a acessibilidade de um método é controlada usando os modificadores `public`, `protected`, `internal` e `private`. O C# generaliza essa funcionalidade, de modo que os tipos definidos pelo usuário de informações declarativas podem ser anexados a entidades de programa e recuperados no tempo de execução. Os programas especificam essas informações declarativas adicionais, definindo e usando os ***atributos***.

O exemplo a seguir declara um atributo `HelpAttribute` que pode ser colocado em entidades de programa para fornecem links para a documentação associada.

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

Todas as classes de atributo derivam da classe base <xref:System.Attribute> fornecida pela biblioteca padrão. Os atributos podem ser aplicados, fornecendo seu nome, junto com quaisquer argumentos, dentro dos colchetes pouco antes da declaração associada. Se o nome de um atributo termina em `Attribute`, essa parte do nome pode ser omitida quando o atributo é referenciado. Por exemplo, o atributo `HelpAttribute` pode ser usado da seguinte maneira.

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

Este exemplo anexa um `HelpAttribute` à classe `Widget`. Ele adiciona outro `HelpAttribute` ao método `Display` na classe. Os construtores públicos de uma classe de atributo controlam as informações que devem ser fornecidas quando o atributo é anexado a uma entidade de programa. As informações adicionais podem ser fornecidas ao referenciar propriedades públicas de leitura-gravação da classe de atributo (como a referência anterior à propriedade `Topic`).

Os metadados definidos por atributos podem ser lidos e manipulados em tempo de execução usando reflexão. Quando um atributo específico for solicitado usando esta técnica, o construtor para a classe de atributo será invocado com as informações fornecidas na origem do programa e a instância do atributo resultante será retornada. Se forem fornecidas informações adicionais por meio de propriedades, essas propriedades serão definidas para os valores fornecidos antes que a instância do atributo seja retornada.

O exemplo de código a seguir demonstra como obter as instâncias `HelpAttribute` associadas à classe `Widget` e seu método `Display`.

[!code-csharp[AttributeRead](../../../samples/snippets/csharp/tour/attributes/Program.cs#ReadAttributes)]

>[!div class="step-by-step"]
[Anterior](delegates.md)
