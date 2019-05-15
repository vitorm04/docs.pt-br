---
title: 'Operador :: – referência do C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 324f6711cdec478e5647b05d84c281f79e95f036
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452354"
---
# <a name="-operator-c-reference"></a>Operador :: (referência do C#)

O qualificador alias de namespace (`::`) é usado para pesquisar identificadores. Ele sempre está posicionado entre dois identificadores, como neste exemplo:

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

O operador `::` também pode ser usado com uma *diretiva alias de uso*:

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a>Comentários

O qualificador alias de namespace pode ser `global`. Isso invoca uma pesquisa no namespace global, em vez de um namespace com alias.

## <a name="for-more-information"></a>Para obter mais informações

Para obter um exemplo de como usar o operador `::`, consulte a seção a seguir:

- [Como: usar o alias de namespace global](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Palavras-chave de namespace](../keywords/namespace-keywords.md)
- [Operador .](member-access-operators.md#member-access-operator-)
- [Alias extern](../keywords/extern-alias.md)