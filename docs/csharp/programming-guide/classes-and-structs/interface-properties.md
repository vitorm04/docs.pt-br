---
title: Propriedades de interface – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: fad674c6d56011afcccbe9ce2a88e7af411fe0a2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579149"
---
# <a name="interface-properties-c-programming-guide"></a>Propriedades de interface (Guia de Programação em C#)

As propriedades podem ser declaradas em uma [interface](../../language-reference/keywords/interface.md). Este é um exemplo de um acessador de propriedade de interface:

[!code-csharp[csProgGuideProperties#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#14)]

O acessador de uma propriedade de interface não tem um corpo. Portanto, a finalidade dos acessadores é indicar se a propriedade é leitura/gravação, somente leitura ou somente gravação.

## <a name="example"></a>Exemplo

Neste exemplo, a interface `IEmployee` tem uma propriedade de leitura/gravação, `Name` e uma propriedade somente leitura, `Counter`. A classe `Employee` implementa a interface `IEmployee` e usa essas duas propriedades. O programa lê o nome de um novo funcionário e o número atual de funcionários e exibe o nome do funcionário e o número do funcionário computado.

Seria possível usar o nome totalmente qualificado da propriedade, que referencia a interface na qual o membro é declarado. Por exemplo:

[!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]

Isso é denominado [Implementação explícita da interface](../interfaces/explicit-interface-implementation.md). Por exemplo, se a classe `Employee` estiver implementando duas interfaces `ICitizen` e `IEmployee` e as duas interfaces tiverem a propriedade `Name`, será necessária a implementação explícita de membro da interface. Ou seja, a seguinte declaração de propriedade:

[!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]

implementa a propriedade `Name` na interface `IEmployee`, enquanto a seguinte declaração:

[!code-csharp[csProgGuideProperties#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#17)]

implementa a propriedade `Name` na interface `ICitizen`.

[!code-csharp[csProgGuideProperties#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#15)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a>Saída de exemplo

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Propriedades](./properties.md)
- [Usando propriedades](./using-properties.md)
- [Comparação entre propriedades e indexadores](../indexers/comparison-between-properties-and-indexers.md)
- [Indexadores](../indexers/index.md)
- [Interfaces](../interfaces/index.md)
