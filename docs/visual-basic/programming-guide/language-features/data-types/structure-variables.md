---
title: "Estrutura variáveis (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- structures, variables
- structures, structure variables
- variables [Visual Basic], structure variables
- structure variables
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 18ddde7f5b7576c6534e9d9a283c24f27ef5c6a2
ms.lasthandoff: 03/13/2017

---
# <a name="structure-variables-visual-basic"></a>Variáveis de estrutura (Visual Basic)
Depois de ter criado uma estrutura, você pode declarar variáveis de nível de procedimento e o nível de módulo como esse tipo. Por exemplo, você pode criar uma estrutura que registra informações sobre um sistema de computador. O exemplo a seguir demonstra isso.  
  
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
>  Em módulos e classes, estruturas declaradas usando a [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) padrão de acesso público. Se você pretende que uma estrutura seja particular, certifique-se de você declará-la usando o [particular](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave.  
  
## <a name="access-to-structure-values"></a>Acesso a valores de estrutura  
 Para atribuir e recuperar valores de elementos de uma variável de estrutura, você usar a mesma sintaxe que você usa para definir e obter as propriedades de um objeto. Coloque o operador de acesso de membro (`.`) entre o nome da variável de estrutura e o nome do elemento. O exemplo a seguir acessa elementos das variáveis previamente declaradas como do tipo `systemInfo`.  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a>Atribuindo variáveis de estrutura  
 Você também pode atribuir uma variável a outra se ambas forem do mesmo tipo de estrutura. Isso copiará todos os elementos de uma estrutura para os elementos correspondentes no outro. A declaração a seguir ilustra isso.  
  
```  
yourSystem = mySystem  
```  
  
 Se um elemento de estrutura for um tipo de referência, como um `String`, `Object`, ou matriz, o ponteiro para os dados é copiado. No exemplo anterior, se `systemInfo` tivesse incluído uma variável de objeto, em seguida, o exemplo anterior teria copiado o ponteiro de `mySystem` para `yourSystem`, e uma alteração nos dados do objeto através de uma estrutura teriam efeito quando acessados através da outra estrutura.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Como: declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Estruturas e outros elementos de programação](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)   
 [Estruturas e Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)   
 [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
