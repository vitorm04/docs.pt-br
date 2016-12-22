---
title: "Vari&#225;veis de estrutura (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variáveis de estrutura"
  - "estruturas, variáveis de estrutura"
  - "estruturas, variáveis"
  - "variáveis [Visual Basic], variáveis de estrutura"
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vari&#225;veis de estrutura (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Depois de criar uma estrutura, você pode declarar variáveis no nível de procedimento e no nível de módulo como esse tipo.  Por exemplo, você pode criar uma estrutura que registra informações sobre um sistema de computador.  O exemplo a seguir demonstra isso.  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 Agora você pode declarar as variáveis desse tipo.  A seguinte declaração ilustra isto.  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  Em módulos e classes, estruturas declaradas usando a [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) são por padrão de acesso público.  Se você pretende que uma estrutura seja particular, certifique\-se de que você a declares usando a palavra\-chave [Particular](../../../../visual-basic/language-reference/modifiers/private.md).  
  
## Acesso a valores de estrutura  
 Para atribuir e recuperar valores de elementos de uma variável de estrutura, você usa a mesma sintaxe que você usa para configurar e obter as propriedades de um objeto.  Você coloca o operador de acesso do membro \(`.`\) entre o nome da variável de estrutura e o nome do elemento.  O exemplo a seguir acessa elementos das variáveis previamente declaradas como do tipo `systemInfo`.  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## Atribuindo variáveis de estrutura  
 Você também pode atribuir uma variável a outra se ambas forem do mesmo tipo de estrutura.  Isso copiará todos os elementos de uma estrutura para os elementos correspondentes na outra.  A seguinte declaração ilustra isto.  
  
```  
yourSystem = mySystem  
```  
  
 Se um elemento de estrutura for um tipo de referência, como uma `String`,`Object`, ou matriz, o ponteiro para os dados é copiado.  No exemplo anterior, se `systemInfo` tivesse incluído uma variável de objeto, então o exemplo anterior teria copiado o ponteiro de `mySystem` para `yourSystem`, e uma alteração nos dados do objeto através de uma estrutura teriam efeito quando acessados através da outra estrutura.  
  
## Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Tipos de valor e referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Como declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Estruturas e outros elementos de programação](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)   
 [Estruturas e classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)   
 [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)