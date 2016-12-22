---
title: "O tipo de vari&#225;vel &#39;&lt; variablename &gt;&#39; n&#227;o ser&#225; inferido porque est&#225; associado a um campo em um escopo delimitador | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42110"
  - "bc42110"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42110"
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O tipo de vari&#225;vel &#39;&lt; variablename &gt;&#39; n&#227;o ser&#225; inferido porque est&#225; associado a um campo em um escopo delimitador
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O tipo para o variablename variável\> ' \<não será inferido porque está associado a um campo em um escopo delimitador.Altere o nome '\<do variablename\>', ou use o nome totalmente qualificado \(por exemplo, “Me.variablename” ou “MyBase.variablename "\).  
  
 Uma variável de controle de loop no seu código tem o mesmo nome que um campo da classe ou outro escopo delimitador.  Porque a variável de controle é usado sem uma cláusula de `As` , é associado ao campo no escopo delimitador, e o compilador não cria uma nova variável para ele ou infere o tipo.  
  
 No exemplo a seguir, `Index`, a variável de controle na declaração de `For` , é associado ao campo de `Index` na classe de `Customer` .  O compilador não cria uma nova variável para a variável de controle `Index` ou infere o tipo.  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
    ' The following line will raise this warning.  
        For Index = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
  
```  
  
 Por default, esta é uma mensagem de aviso.  Para obter informações sobre como ocultar avisos ou de como tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **Identificação do erro:** BC42110  
  
### Para resolver este aviso  
  
-   Faça o local da variável de controle de loop alterando seu nome a um identificador que não é também o nome de um campo da classe.  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   Para que a variável de controle de loop associa ao campo da classe prefixando `Me.` o nome de variável.  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   Em vez de depender de inferência de tipos local, use uma cláusula de `As` para especificar um tipo para a variável de controle de loop.  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## Exemplo  
 O código a seguir mostra o exemplo anterior com a primeira correção no lugar.  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
        For I = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
## Consulte também  
 [Instrução Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Como fazer referência à instância atual de um objeto](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)   
 [Inferência de tipo local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)