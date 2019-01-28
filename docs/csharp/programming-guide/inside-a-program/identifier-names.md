---
title: Nomes de identificadores
description: Conheça as regras para nomes de identificador válidos na linguagem de programação C#.
ms.date: 08/21/2018
ms.openlocfilehash: 2147b3846d4ba6d5471b81448489c6d716e3cd61
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606946"
---
# <a name="identifier-names"></a>Nomes de identificadores

Um **identificador** é o nome que você atribui a um tipo (classe, interface, struct, delegado ou enumerado), membro, variável ou namespace. Os identificadores válidos devem seguir estas regras:

- Os identificadores devem começar com uma letra ou `_`.
- Os identificadores podem conter caracteres de letra Unicode, caracteres de dígito decimal, caracteres de conexão Unicode, caracteres de combinação Unicode ou caracteres de formatação Unicode. Para obter mais informações sobre as categorias Unicode, consulte o [Banco de dados da categoria Unicode](https://www.unicode.org/reports/tr44/).
É possível declarar identificadores que correspondem às palavras-chave em C# usando o prefixo `@` no identificador. O `@` não faz parte do nome do identificador. Por exemplo, `@if` declara um identificador chamado `if`. Esses [identificadores textuais](../../language-reference/tokens/verbatim.md) são destinados principalmente para interoperabilidade com os identificadores declarados em outras linguagens.

Para obter uma definição completa de identificadores válidos, consulte o [tópico de identificadores na especificação da linguagem C#](../../../../_csharplang/spec/lexical-structure.md#identifiers).

## <a name="naming-conventions"></a>Convenções de nomenclatura

Além das regras, há inúmeras [convenções de nomenclatura](../../../standard/design-guidelines/naming-guidelines.md) de identificador usadas em toda as APIs do .NET. Por convenção, os programas C# usam `PascalCase` para nomes de tipo, namespaces e todos os membros públicos. Além disso, as seguintes convenções são comuns:

- Os nomes de interface começam com `I` maiúsculo.
- Os tipos de atributo terminam com a palavra `Attribute`.
- Os tipos enumerados usam um substantivo singular para não sinalizadores e um substantivo plural para sinalizadores.
- Os identificadores não devem conter dois caracteres `_` consecutivos. Esses nomes estão reservados para identificadores gerados por compilador.

## <a name="c-language-specification"></a>Especificação da Linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Por dentro de um programa em C#](../inside-a-program/index.md)
- [Referência de C#](../../language-reference/index.md)
- [Classes](../classes-and-structs/classes.md)
- [Estruturas](../classes-and-structs/structs.md)
- [Namespaces](../namespaces/index.md)
- [Interfaces](../interfaces/index.md)
- [Delegados](../delegates/index.md)
