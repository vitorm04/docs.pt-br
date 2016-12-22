---
title: "Como acessar membros de um objeto (Visual Basic) | Microsoft Docs"
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
  - "membros, acessando"
  - "variáveis de objeto, acessando membros"
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como acessar membros de um objeto (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Quando você tiver um variável de objeto que se refere a um objeto, você geralmente deseja trabalhar com os membros desse objeto, como seus métodos, propriedades, campos e eventos.  Por exemplo, depois de criar um novo objeto <xref:System.Windows.Forms.Form>, convém definir sua propriedade <xref:System.Windows.Forms.Control.Text%2A> ou chamar o método <xref:System.Windows.Forms.Control.Focus%2A>.  
  
## Acessando Membros  
 Você acessar membros de um objeto através da variável que faz referência a ele.  
  
#### Para Acessar Membros de um Objeto  
  
-   Use o operador de acesso a membro \(`.`\) entre o nome da variável do objeto e o nome do membro.  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     Se o membro for [Compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md), você não precisa de uma variável para acessá\-lo.  
  
## Acessando Membros de um Objeto do Tipo Conhecido  
 Se você souber o tipo de um objeto em tempo de compilação, você pode usar  *vinculação antecipada*  para uma variável que faz referência a ele.  
  
#### Para acessar membros de um objeto para o qual você sabe o tipo em tempo de compilação  
  
1.  Declare a variável de objeto para ser do tipo do objeto que você pretende atribuir à variável.  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form   
    ```  
  
     Com `Option Strict On`, você pode atribuir apenas objetos <xref:System.Windows.Forms.Form> \(ou objetos de um tipo derivado de <xref:System.Windows.Forms.Form>\) para `extraForm`.  Se você tiver definido uma classe ou estrutura com uma conversão `CType` de ampliação para <xref:System.Windows.Forms.Form>, você também pode atribuir essa classe ou estrutura a `extraForm`.  
  
2.  Use o operador de acesso a membro \(`.`\) entre o nome da variável do objeto e o nome do membro.  
  
    ```  
    extraForm.Show()  
    ```  
  
     Você pode acessar todos os métodos e propriedades específicas para a classe <xref:System.Windows.Forms.Form>, independentemente da configuração `Option Strict`.  
  
## Acessando Membros de um Objeto de Tipo Não Conhecido  
 Se você não souber o tipo de um objeto em tempo de compilação, você deve usar  *vinculação atrasada*  para qualquer variável que faz referência a ele.  
  
#### Para acessar membros de um objeto para o qual você não sabe o tipo em tempo de compilação  
  
1.  Declare o variável de objeto para ser de [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md).  \(Declarar uma variável como `Object` é o mesmo que declará\-la como <xref:System.Object?displayProperty=fullName>\).  
  
    ```  
    Dim someControl As Object   
    ```  
  
     Com `Option Strict On`, você pode acessar somente os membros que estão definidos na classe <xref:System.Object>.  
  
2.  Use o operador de acesso a membro \(`.`\) entre o nome da variável do objeto e o nome do membro.  
  
    ```  
    someControl.GetType()  
    ```  
  
     Para poder acessar os membros de qualquer objeto que você atribuir à variável de objeto, você deve definir `Option Strict Off`.  Quando você fizer isso, o compilador não pode garantir que um determinado membro é exposto pelo objeto que você atribui à variável.  Se o objeto não expõe um membro que você tentar acessar, uma exceção <xref:System.MemberAccessException> ocorre.  
  
## Consulte também  
 <xref:System.Object>   
 <xref:System.Windows.Forms.Form>   
 <xref:System.MemberAccessException>   
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Declaração de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)