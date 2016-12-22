---
title: "Como determinar a que tipo uma vari&#225;vel de objeto se refere (Visual Basic) | Microsoft Docs"
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
  - "variáveis de objeto, determinando o tipo"
  - "Operador TypeOf [Visual Basic], determinando o tipo de variável de objeto"
  - "variáveis [Visual Basic], Objeto "
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como determinar a que tipo uma vari&#225;vel de objeto se refere (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um variável de objeto contém um ponteiro para dados armazenados em outro lugar.  O tipo de dados que pode alterar durante tempo de execução.  A qualquer momento, você pode usar o método <xref:System.Type.GetTypeCode%2A> para determinar o run\-time type atual, ou [Operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md) para saber se o run\-time type atual é compatível com um tipo especificado.  
  
### Para determinar que a exata tipo um variável de objeto atualmente refere\-se a  
  
1.  Sobre o variável de objeto, chame o método <xref:System.Object.GetType%2A> Para recuperar um objeto <xref:System.Type?displayProperty=fullName>.  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  Na classe <xref:System.Type?displayProperty=fullName>, chame o método <xref:System.Type.GetTypeCode%2A> para recuperar o valor de enumeração <xref:System.TypeCode> para o tipo de objeto compartilhado.  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     Você pode testar o valor de enumeração <xref:System.TypeCode> contra qualquer enumeração membros são de interesse, como `Double`.  
  
### Para determinar se um variável de objeto do tipo é compatível com um tipo especificado  
  
-   Use o operador `TypeOf` Em combinação com o [Operador Is](../../../../visual-basic/language-reference/operators/is-operator.md) Para testar o objeto com um `TypeOf`... `Is` expressão.  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     O `TypeOf`... `Is` expressão retorna `True` se o objeto do run\-time type é compatível com o tipo especificado.  
  
     O critério para compatibilidade depende se o tipo especificado é uma classe, estrutura ou interface.  Em geral, os tipos são compatíveis se o objeto é do mesmo tipo como, herda de ou implementa o tipo especificado.  Para obter mais informações, consulte [Operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## Compilando o código  
 Observe que o tipo especificado não pode ser uma variável ou expressão.  Ele deve ser o nome de um tipo definido, como uma classe, estrutura ou interface.  Isso inclui intrínsecos tipos como `Integer` e `String`.  
  
## Consulte também  
 <xref:System.Object.GetType%2A>   
 <xref:System.Type?displayProperty=fullName>   
 <xref:System.Type.GetTypeCode%2A>   
 <xref:System.TypeCode>   
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Valores de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)