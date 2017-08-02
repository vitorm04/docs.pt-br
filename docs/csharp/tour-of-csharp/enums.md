---
title: Enums em C# - um tour pela linguagem C#
description: Saiba mais sobre enums, constantes nomeadas discretas no C#
keywords: .NET, csharp
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 77d315dd87d9cab32605de415674d146eb9115fa
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
    
# <a name="enums"></a>Enums

Um ***tipo enum*** é um tipo de valor diferente com um conjunto de constantes nomeadas. Você define enums quando precisa definir um tipo que pode ter um conjunto de valores discretos. Eles usam um dos tipos de valor integral como o armazenamento subjacente. Eles fornecem um significado semântico aos valores discretos.

O exemplo a seguir declara e usa um tipo `enum` chamado `Color` com três valores de constantes, `Red`, `Green` e `Blue`.

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

Cada tipo `enum` tem um tipo integral correspondente chamado de ***tipo subjacente*** do tipo `enum`. Um tipo `enum` que não declara explicitamente um tipo subjacente tem um tipo subjacente de `int`. Um formato de armazenamento do tipo `enum` e o intervalo de valores possíveis são determinados pelo seu tipo subjacente. O conjunto de valores que um tipo `enum` pode lidar não é limitado pelos seus membros `enum`. Em particular, qualquer valor do tipo subjacente de um `enum` pode ser convertido em um tipo `enum` e é um valor válido diferente do que o do tipo `enum`.

O exemplo a seguir declara um tipo `enum` chamado `Alignment` com um tipo subjacente de `sbyte`.

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

Conforme mostrado no exemplo anterior, uma declaração de membro `enum` pode incluir uma expressão constante que especifica o valor do membro. O valor da constante para cada membro `enum` deve estar no intervalo do tipo subjacente do `enum`. Quando uma declaração de membro `enum` não especifica explicitamente um valor, o membro recebe o valor zero (se ele é o primeiro membro no tipo `enum`) ou o valor do membro `enum` textualmente precedente mais um.

Os valores `Enum` podem ser convertidos em valores integrais e vice-versa usando conversões de tipo. Por exemplo:

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

O valor padrão de qualquer tipo `enum` é o valor integral zero convertido para o tipo `enum`. Em casos nos quais as variáveis são inicializadas automaticamente como um valor padrão, esse é o valor fornecido para variáveis de tipos `enum`. Para que o valor padrão de um tipo `enum` fique facilmente disponível, o `0` literal é convertido implicitamente para qualquer tipo `enum`. Dessa forma, o seguinte é permitido.

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

>[!div class="step-by-step"]
[Anterior](interfaces.md)
[Próximo](delegates.md)

