---
title: Variáveis de estrutura
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 16b6cdc5a849b50f6caa8b7963dac5c12d63cf3e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346301"
---
# <a name="structure-variables-visual-basic"></a>Variáveis de estrutura (Visual Basic)

Depois de criar uma estrutura, você pode declarar variáveis em nível de procedimento e de módulo como esse tipo. Por exemplo, você pode criar uma estrutura que registra informações sobre um sistema de computador. O exemplo a seguir demonstra isso.

```vb
Public Structure systemInfo
    Public cPU As String
    Public memory As Long
    Public purchaseDate As Date
End Structure
```

Agora você pode declarar variáveis desse tipo. A declaração a seguir ilustra isso.

```vb
Dim mySystem, yourSystem As systemInfo
```

> [!NOTE]
> Em classes e módulos, as estruturas declaradas usando a [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) assumem o acesso público como padrão. Se você pretende que uma estrutura seja privada, certifique-se de declará-la usando a palavra-chave [Private](../../../../visual-basic/language-reference/modifiers/private.md) .

## <a name="access-to-structure-values"></a>Acesso a valores de estrutura

Para atribuir e recuperar valores dos elementos de uma variável de estrutura, use a mesma sintaxe usada para definir e obter propriedades em um objeto. Você coloca o operador de acesso de membro (`.`) entre o nome da variável de estrutura e o nome do elemento. O exemplo a seguir acessa os elementos das variáveis declaradas anteriormente como tipo `systemInfo`.

```vb
mySystem.cPU = "486"
Dim tooOld As Boolean
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True
```

## <a name="assigning-structure-variables"></a>Atribuindo variáveis de estrutura

Você também pode atribuir uma variável a outra se ambas forem do mesmo tipo de estrutura. Isso copia todos os elementos de uma estrutura para os elementos correspondentes no outro. A declaração a seguir ilustra isso.

```vb
yourSystem = mySystem
```

Se um elemento de estrutura for um tipo de referência, como um `String`, `Object`ou matriz, o ponteiro para os dados será copiado. No exemplo anterior, se `systemInfo` tiver incluído uma variável de objeto, o exemplo anterior teria copiado o ponteiro de `mySystem` para `yourSystem`, e uma alteração nos dados do objeto por meio de uma estrutura estaria em vigor quando acessada por meio da outra estrutura.

## <a name="see-also"></a>Consulte também

- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Tipos de Dados Elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Tipos de Dados Compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Como declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Estruturas e Outros Elementos de Programação](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Estruturas e Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
