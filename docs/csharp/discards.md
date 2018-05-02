---
title: Descartes – Guia do C#
description: Descreve o suporte do C# a descartes, que são variáveis descartáveis não atribuídas, além das maneiras em que descartes podem ser usados.
keywords: .NET,.NET Core
author: rpetrusha
ms.author: ronpet
ms.date: 07/21/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 94badd78485ee4d3928b170d81a80743bf84102f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="discards---c-guide"></a>Descartes – Guia do C#

Começando com o C# 7.0, o C# é compatível com descartes, que são variáveis temporárias e fictícias, não utilizadas intencionalmente no código do aplicativo. Descartes são equivalentes a variáveis não atribuídas; eles não têm um valor. Já que há apenas uma variável de descarte e essa variável pode nem mesmo ser de armazenamento alocado, descartes podem reduzir as alocações de memória. Por deixarem clara a intenção do seu código, eles melhoram a sua legibilidade e a facilidade de manutenção.

Você indica que uma variável é um descarte atribuindo a ela o sublinhado (`_`) como seu nome. Por exemplo, a chamada de método a seguir retorna uma tupla de 3 na qual o primeiro e o segundo valores são descartes, e *area* é uma variável declarada anteriormente para ser definida para o terceiro componente correspondente retornado por *GetCityInformation*:

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

No C# 7.0, há suporte para descartes em atribuições nos seguintes contextos:

- [Desconstrução](deconstruct.md) de objeto e de tupla.
- Correspondência de padrões com [is](language-reference/keywords/is.md) e [switch](language-reference/keywords/switch.md).
- Chamadas para métodos com parâmetros `out`.
- Um `_` autônomo quando nenhum `_` está no escopo.

Quando `_` é um descarte válido, tentar recuperar seu valor ou usá-lo em uma operação de atribuição gera o erro do compilador CS0301, "O nome '\_' não existe no contexto atual". Isso ocorre porque não há um valor atribuído a `_` e pode não haver nem mesmo um local de armazenamento atribuído a ela. Se ela fosse uma variável real, você não poderia descartar mais de um valor, tal como ocorreu no exemplo anterior.

## <a name="tuple-and-object-deconstruction"></a>Desconstrução de objeto e de tupla

Descartes são particularmente úteis para trabalhar com tuplas quando seu código de aplicativo usa alguns elementos de tupla, mas ignora outros. Por exemplo, o método `QueryCityDataForYears` a seguir retorna uma tupla de 6 com o nome de uma cidade, sua área, um ano, a população da cidade nesse ano, um segundo ano e população da cidade nesse segundo ano. O exemplo mostra a alteração na população entre esses dois anos. Entre os dados disponíveis da tupla, não estamos preocupados com a área da cidade e sabemos o nome da cidade e as duas datas em tempo de design. Como resultado, estamos interessados apenas nos dois valores de população armazenados na tupla e podemos lidar com seus valores restantes como descartes.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Para obter mais informações sobre desconstruir tuplas com descartes, consulte [Desconstruindo tuplas e outros tipos](deconstruct.md#deconstructing-tuple-elements-with-discards).

O método `Deconstruct` de uma classe, estrutura ou interface também permite que você recupere e decomponha um conjunto específico de dados de um objeto. Você poderá usar descartes quando estiver interessado em trabalhar com apenas um subconjunto dos valores desconstruídos. O exemplo a seguir desconstrói um objeto `Person` em quatro cadeias de caracteres (os nomes e sobrenomes, a cidade e o estado), mas descarta o sobrenome e o estado.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

Para obter mais informações sobre desconstruir tipos definidos pelo usuário com descartes, consulte [Desconstruindo tuplas e outros tipos](deconstruct.md#deconstructing-a-user-defined-type-with-discards).

## <a name="pattern-matching-with-switch-and-is"></a>Correspondência de padrões com `switch` e `is`

O *padrão de descarte* pode ser usado na correspondência de padrões com as palavras-chave [is](language-reference/keywords/is.md) e [switch](language-reference/keywords/switch.md). Toda expressão sempre corresponde ao padrão de descarte.

O exemplo a seguir define um método `ProvidesFormatInfo` que usa instruções [is](language-reference/keywords/is.md) para determinar se um objeto fornece uma implementação de <xref:System.IFormatProvider> e testa se o objeto é `null`. Ele também usa o padrão de descarte para manipular objetos não nulos de qualquer outro tipo.

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a>Chamadas para métodos com parâmetros out

Ao chamar o método `Deconstruct` para desconstruir um tipo definido pelo usuário (uma instância de uma classe, estrutura ou interface), você pode descartar os valores de argumentos `out` individuais. Mas você também pode descartar o valor de argumentos `out` ao chamar qualquer método com um parâmetro out. 

A exemplo a seguir chama o método [DateTime.TryParse(String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) para determinar se a representação de cadeia de caracteres de uma data é válida na cultura atual. Já que o exemplo está preocupado apenas em validar a cadeia de caracteres de data e não em analisá-lo para extrair a data, o argumento `out` para o método é um descarte.

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a>Um descarte autônomo

Você pode usar um descarte autônomo para indicar qualquer variável que você opte por ignorar. O exemplo a seguir usa um descarte autônomo para ignorar o objeto <xref:System.Threading.Tasks.Task> retornado por uma operação assíncrona. Isso tem o efeito de suprimir a exceção que a operação gera quando está prestes a ser concluída.

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

Observe que `_` também é um identificador válido. Quando usado fora de um contexto com suporte, `_` não é tratado como um descarte, mas como uma variável válida. Se um identificador chamado `_` já está no escopo, o uso de `_` como um descarte autônomo pode resultar em:

- A modificação acidental do valor da variável `_` no escopo atribuindo a ela o valor do descarte pretendido. Por exemplo:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]
 
- Um erro do compilador por violação de segurança de tipo. Por exemplo:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]
 
- Erro do compilador CS0136, "Um local ou um parâmetro denominado '_' não pode ser declarado neste escopo porque esse nome é usado em um escopo delimitador de local para definir um local ou parâmetro." Por exemplo:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a>Consulte também
[Desconstruindo tuplas e outros tipos](deconstruct.md)   
[`is` palavra-chave](language-reference/keywords/is.md)   
[`switch` palavra-chave](language-reference/keywords/switch.md)   
