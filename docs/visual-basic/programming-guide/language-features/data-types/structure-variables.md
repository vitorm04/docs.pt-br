---
title: Variáveis de estrutura (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 9a6e542e297a17f44d929235530ae6058cf13a36
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816324"
---
# <a name="structure-variables-visual-basic"></a>Variáveis de estrutura (Visual Basic)
Depois de criar uma estrutura, você pode declarar variáveis de nível de procedimento e o nível de módulo como esse tipo. Por exemplo, você pode criar uma estrutura que registra informações sobre um sistema de computador. O exemplo a seguir demonstra isso.  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 Agora você pode declarar variáveis desse tipo. A declaração a seguir ilustra isso.  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  Em módulos e classes, estruturas declaradas usando o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) padrão de acesso público. Se você pretende que uma estrutura seja particular, verifique se você declará-la usando o [privada](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave.  
  
## <a name="access-to-structure-values"></a>Acesso aos valores de estrutura  
 Para atribuir e recuperar valores de elementos de uma variável de estrutura, você usar a mesma sintaxe que você use para definir e obter as propriedades de um objeto. Você coloca o operador de acesso de membro (`.`) entre o nome da variável de estrutura e o nome do elemento. O exemplo a seguir acessa elementos das variáveis declarados anteriormente como tipo `systemInfo`.  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a>Atribuindo variáveis de estrutura  
 Você também pode atribuir uma variável para outra se ambas forem do mesmo tipo de estrutura. Isso copiará todos os elementos de uma estrutura para os elementos correspondentes no outro. A declaração a seguir ilustra isso.  
  
```  
yourSystem = mySystem  
```  
  
 Se um elemento de estrutura é um tipo de referência, como uma `String`, `Object`, ou matriz, o ponteiro para os dados é copiado. No exemplo anterior, se `systemInfo` tivesse incluído uma variável de objeto, em seguida, o exemplo anterior seria ter copiado o ponteiro de `mySystem` para `yourSystem`, e uma alteração nos dados do objeto através de uma estrutura teriam efeito quando acessados através da estrutura.  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Tipos de Dados Elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Tipos de Dados Compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Como: declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Estruturas e Outros Elementos de Programação](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Estruturas e Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
