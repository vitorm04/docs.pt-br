---
title: Como usar structs – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: 8b2810af81a57cf21b9a2e2438f7f6aa2cb7a669
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72772067"
---
# <a name="using-structs-c-programming-guide"></a>Usando structs (C# guia de programação)

O tipo `struct` é adequado para representar objetos leves como `Point`, `Rectangle` e `Color`. Embora seja conveniente representar um ponto como uma [classe](../../language-reference/keywords/class.md) com [Propriedades Auto-implementadas](./auto-implemented-properties.md), um [struct](../../language-reference/keywords/struct.md) pode ser mais eficiente em alguns cenários. Por exemplo, se você declarar uma matriz de 1000 objetos `Point`, alocará memória adicional para referenciar cada objeto, nesse caso, um struct será mais barato. Como o .NET Framework contém um objeto chamado <xref:System.Drawing.Point>, a estrutura neste exemplo é denominada `Coords` em vez disso.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

É um erro definir um construtor sem parâmetros para uma struct. Também é um erro ao inicializar um campo de instância em um corpo de struct. Você pode inicializar membros de struct externamente acessíveis somente por meio de um construtor com parâmetros, do construtor sem parâmetro implícito, de um [inicializador de objeto](object-and-collection-initializers.md) ou acessando os membros individualmente depois que o struct é declarado. Todos os membros particulares ou, de outro modo, inacessíveis exigem o uso de construtores exclusivamente.

Quando você cria um objeto de struct usando o operador [new](../../language-reference/operators/new-operator.md), ele é criado e o construtor apropriado é chamado de acordo com a [assinatura do construtor](constructors.md#constructor-syntax). Diferentemente das classes, os structs podem ser instanciados sem usar o operador `new`. Nesse caso, não há nenhuma chamada do construtor, o que torna a alocação mais eficiente. No entanto, os campos permanecerão não atribuídos e o objeto não poderá ser usado até que todos os campos sejam inicializados. Isso inclui a incapacidade de obter ou definir valores por meio de propriedades.

Se você criar uma instância de um objeto struct usando o construtor sem parâmetros, todos os membros serão atribuídos de acordo com seus [valores padrão](../../language-reference/keywords/default-values-table.md).

Ao gravar um construtor com parâmetros para uma struct, você deve inicializar explicitamente todos os membros; caso contrário, um ou mais membros permanecerão não atribuídos e a estrutura não poderá ser usada, produzindo o erro [CS0171](../../misc/cs0171.md)do compilador.

Não há nenhuma herança para structs como há para classes. Um struct não pode herdar de outra estrutura ou classe e ele não pode ser a base de uma classe. No entanto, os structs herdam da classe base <xref:System.Object>. Um struct pode implementar interfaces e ele faz isso exatamente como as classes.

Você não pode declarar uma classe usando a palavra-chave `struct`. No C#, as classes e os structs são semanticamente diferentes. Um struct é um tipo de valor, enquanto uma classe é um tipo de referência. Para obter mais informações, consulte [tipos de valor](../../language-reference/keywords/value-types.md) e tipos de [referência](../../language-reference/keywords/reference-types.md).

A menos que você precise de semântica de tipo de referência, uma pequena classe pode ser tratada com mais eficiência pelo sistema se você declará-la como um struct em vez disso.

## <a name="example-1"></a>Exemplo 1

Este exemplo demonstra `struct` inicialização usando os construtores sem parâmetros e com parâmetros.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

[!code-csharp[csProgGuideObjects#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#2)]

## <a name="example-2"></a>Exemplo 2

Este exemplo demonstra um recurso que é exclusivo para struct. Ele cria um objeto Coords sem usar o operador `new`. Se você substituir a palavra `struct` pela palavra `class`, o programa não compilará.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

[!code-csharp[csProgGuideObjects#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#3)]

## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Classes e Structs](index.md)
- [Structs](structs.md)
