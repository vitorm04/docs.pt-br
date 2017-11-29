---
title: Interfaces em C# - um tour pela linguagem C#
description: As interfaces definem os contratos implementados pelos tipos no C#
keywords: ".NET, csharp, interfaces, herança múltipla, polimorfismo"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 673ac56f3f5732fcda02d313b6f4273708ae365f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="interfaces"></a>Interfaces

Uma ***interface*** define um contrato que pode ser implementado por classes e estruturas. Uma interface pode conter métodos, propriedades, eventos e indexadores. Uma interface não fornece implementações dos membros que define — ela simplesmente especifica os membros que devem ser fornecidos por classes ou estruturas que implementam a interface.

As interfaces podem empregar a ***herança múltipla***. No exemplo a seguir, a interface `IComboBox` herda de `ITextBox` e `IListBox`.

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

Classes e structs podem implementar várias interfaces. No exemplo a seguir, a classe `EditBox` implementa `IControl` e `IDataBound`.

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

Quando uma classe ou struct implementa uma interface específica, as instâncias dessa classe ou struct podem ser convertidas implicitamente para esse tipo de interface. Por exemplo

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

Em casos nos quais uma instância não é conhecida por ser estática para implementar uma interface específica, é possível usar conversões de tipo dinâmico. Por exemplo, as instruções a seguir usam conversões de tipo dinâmico para obter as implementações de interface de `IControl` e `IDataBound` do objeto. Como o tipo de tempo de execução real do objeto é `EditBox`, as conversões são bem-sucedidas.

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

Na classe `EditBox` anterior, o método `Paint` da interface `IControl` e o método `Bind` da interface `IDataBound` são implementados usando membros públicos. C# também oferece suporte explícito a ***implementações de membros de interface***, permitindo que a classe ou struct evite tornar os membros públicos. Uma implementação de membro de interface explícita é escrita usando o nome do membro de interface totalmente qualificado. Por exemplo, a classe `EditBox` pode implementar os métodos `IControl.Paint` e `IDataBound.Bind` usando implementações de membros de interface explícita da seguinte maneira.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

Os membros de interface explícita só podem ser acessados por meio do tipo de interface. Por exemplo, a implementação de `IControl.Paint` fornecida pela classe EditBox anterior só pode ser chamada convertendo primeiro a referência `EditBox` ao tipo de interface `IControl`.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
[Anterior](arrays.md)
[Próximo](enums.md)
