---
title: "Como declarar uma constante (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.constant"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tipo de dados Booliano, declarando constantes"
  - "tipo de dados Byte, declarando constantes"
  - "instrução Const [Visual Basic], declarando constantes"
  - "constantes, declarando"
  - "tipo de dados Currency, declarando constantes e variantes"
  - "tipos de dados [Visual Basic], constantes"
  - "tipo de dados de data, declarando constantes"
  - "declarando constantes, palavra-chave const"
  - "tipo de dados Double, declarando constantes"
  - "tipo de dados Integer, declarando constantes"
  - "tipo de dados Long, declarando constantes"
  - "constantes e variáveis de nível de módulo"
  - "módulos, declarando constantes"
  - "tipo de dados Object, declarando constantes"
  - "procedimentos, declaração"
  - "tipo de dados Single, declarando constantes"
  - "tipo de dados String, declarando constantes"
  - "código do Visual Basic, declarando variáveis e constantes"
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como declarar uma constante (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode usar o `Const` instrução para declarar uma constante e defina seu valor.  Ao declarar uma constante, você pode atribuir um nome significativo para um valor.  Depois que uma constante é declarada, não pode ser modificado ou atribuído a um novo valor.  
  
 Você declarar uma constante dentro de um procedimento ou na seção declarações de um módulo, classe ou estrutura.  Classe ou constantes no nível de estrutura são `Private` por padrão, mas também podem ser declarados como `Public`, `Friend`, `Protected`, ou `Protected Friend` para o nível apropriado de acesso ao código.  
  
 A constante deve ter um nome simbólico válido \(as regras são as mesmas para a criação de nomes de variáveis\) e uma expressão composta do numérico ou cadeia de caracteres constantes e operadores \(mas não há chamadas de função\).  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### Para declarar uma constante  
  
-   Escrever uma declaração que inclui um especificador de acesso, o `Const` palavra\-chave e uma expressão, como nos exemplos a seguir:  
  
     [!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type \(`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`\).  
  
     Quando `Option Infer` é `On` ou `Option Strict` é `Off`, você pode declarar uma constante sem especificar um tipo de dados com um `As` cláusula.  O compilador determina o tipo da constante do tipo da expressão.  Para obter mais informações, consulte [Tipos de dados constante e literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md).  
  
### Para declarar uma constante que tem um tipo de dados explicitamente estabelecido  
  
-   Escrever uma declaração que inclui o `As` digitar palavra\-chave e uma data de explícita, como nos exemplos a seguir:  
  
     [!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     Você pode declarar diversas constantes em uma única linha, embora seu código mais legível, se você declarar uma única constante por linha.  Se você declarar constantes várias em uma única linha, eles devem ter o mesmo nível de acesso \(`Public`, `Private`, `Friend`, `Protected`, ou `Protected Friend`\).  
  
### Para declarar constantes de várias em uma única linha.  
  
-   Separe as declarações com uma vírgula e um espaço, como no exemplo a seguir:  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## Consulte também  
 [Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md)   
 [Tipos de dados constante e literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Constantes e enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)   
 [Visão geral de enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [Visão geral de constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Como declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)