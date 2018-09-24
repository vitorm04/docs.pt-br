---
title: interface (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 4adc7ba106e0044ba6aff94ea3180d9c8e3ded7b
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46711292"
---
# <a name="interface-c-reference"></a>interface (Referência de C#)

Uma interface contém apenas as assinaturas de [métodos](../../programming-guide/classes-and-structs/methods.md), [propriedades](../../programming-guide/classes-and-structs/properties.md), [eventos](../../programming-guide/events/index.md) ou [indexadores](../../programming-guide/indexers/index.md). Uma classe ou struct que implementa a interface deve implementar os membros da interface que estão especificados na definição de interface. No exemplo a seguir, a classe `ImplementationClass` deve implementar um método chamado `SampleMethod` que não tem parâmetros e retorna `void`.

Para obter mais informações e exemplos, consulte [Interfaces](../../programming-guide/interfaces/index.md).

## <a name="example"></a>Exemplo

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

Uma interface pode ser um membro de um namespace ou de uma classe e pode conter assinaturas dos seguintes membros:

- [Métodos](../../programming-guide/classes-and-structs/methods.md)

- [Propriedades](../../programming-guide/classes-and-structs/using-properties.md)

- [Indexadores](../../programming-guide/indexers/using-indexers.md)

- [Eventos](event.md)

Uma interface pode herdar de uma ou mais interfaces base.

Quando uma lista de tipos base contém uma classe base e interfaces, a classe base deve vir em primeiro na lista.

Uma classe que implementa uma interface pode implementar membros dessa interface explicitamente. Um membro implementado explicitamente não pode ser acessado por meio de uma instância da classe, mas apenas por meio de uma instância da interface.

Para obter mais detalhes e exemplos de código sobre a implementação explícita da interface, consulte [Implementação explícita da interface](../../programming-guide/interfaces/explicit-interface-implementation.md).

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra a implementação da interface. Neste exemplo, a interface contém a declaração de propriedade e a classe contém a implementação. Qualquer instância de uma classe que implementa `IPoint` tem propriedades de inteiro `x` e `y`.

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../programming-guide/index.md)  
- [Palavras-chave do C#](index.md)  
- [Tipos de referência](reference-types.md)  
- [Interfaces](../../programming-guide/interfaces/index.md)  
- [Usando propriedades](../../programming-guide/classes-and-structs/using-properties.md)  
- [Usando indexadores](../../programming-guide/indexers/using-indexers.md)  
- [class](class.md)  
- [struct](struct.md)  
- [Interfaces](../../programming-guide/interfaces/index.md)
