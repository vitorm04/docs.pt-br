---
title: Tipos aninhados – Guia de Programação em C#
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 12e44ccc1254424c152a238c8390f133550fa54c
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626484"
---
# <a name="nested-types-c-programming-guide"></a>Tipos aninhados (Guia de Programação em C#)

Um tipo definido em uma [classe](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md)ou [interface](../../language-reference/keywords/interface.md) é chamado de tipo aninhado. Por exemplo

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

Independentemente de o tipo externo ser uma classe, interface ou struct, os tipos aninhados são padrão para [privado](../../language-reference/keywords/private.md); Eles são acessíveis somente de seu tipo recipiente. No exemplo anterior, a classe `Nested` é inacessível para tipos externos.

Você também pode especificar um [modificador de acesso](../../language-reference/keywords/access-modifiers.md) para definir a acessibilidade de um tipo aninhado, da seguinte maneira:

- Os tipos aninhados de uma **classe** podem ser [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) ou [private protected](../../language-reference/keywords/private-protected.md).

   No entanto, a definição de uma classe aninhada `protected`, `protected internal` ou `private protected` dentro de uma [classe selada](../../language-reference/keywords/sealed.md) gera um aviso do compilador [CS0628](../../misc/cs0628.md), "novo membro protegido declarado na classe selada".
  
- Tipos aninhados de um **struct** podem ser [públicos](../../language-reference/keywords/public.md), [internos](../../language-reference/keywords/internal.md) ou [particulares](../../language-reference/keywords/private.md).

O exemplo a seguir torna a classe `Nested` pública:

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

O tipo aninhado ou interno pode acessar o tipo recipiente ou externo. Para acessar o tipo recipiente, passe-o como um argumento ao construtor do tipo aninhado. Por exemplo:

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

Um tipo aninhado tem acesso a todos os membros acessíveis ao seu tipo recipiente. Ele pode acessar membros privados e protegidos do tipo recipiente, incluindo quaisquer membros protegidos herdados.

Na declaração anterior, o nome completo da classe `Nested` é `Container.Nested`. Este é o nome usado para criar uma nova instância da classe aninhada, da seguinte maneira:

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a>Confira também

- [Guia de Programação em C#](../index.md)
- [Classes e Structs](./index.md)
- [Modificadores de acesso](./access-modifiers.md)
- [Construtores](./constructors.md)
