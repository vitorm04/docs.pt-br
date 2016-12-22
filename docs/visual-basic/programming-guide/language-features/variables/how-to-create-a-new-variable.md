---
title: "Como criar uma nova vari&#225;vel (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "instrução Dim"
  - "variáveis [Visual Basic], criando"
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: 29
caps.handback.revision: 29
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar uma nova vari&#225;vel (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Criar uma variável com uma [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).  
  
### Para criar uma nova variável  
  
1.  Declare a variável em uma instrução `Dim`.  
  
    ```  
  
    Dim newCustomer  
    ```  
  
2.  Incluir as especificações para as características da variável, tais como [Particular](../../../../visual-basic/language-reference/modifiers/private.md), [Estático](../../../../visual-basic/language-reference/modifiers/static.md), [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md), ou [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).  Para obter mais informações, consulte [Características do elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
     Você não precisa de uma palavra\-chave `Dim` se você usar outras palavras\-chaves na declaração.  
  
3.  Siga as especificações com o nome da variável, que deve seguir as  regras e convenções [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  Para obter mais informações, consulte [Nomes de elemento declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  Acompanhe o nome com a cláusula [As](../../../../visual-basic/language-reference/statements/as-clause.md) para especificar o tipo de dados da variável.  
  
    ```  
    Public Static newCustomer As Customer   
    ```  
  
     Se você não especificar o tipo de dados, ele utilizará o padrão: `Object`.  
  
5.  Acompanhe a cláusula `As` com um sinal de igualdade \(`=`\) e acompanhe o sinal de igualdade com o valor inicial da variável.  
  
     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] atribui o valor especificado para a variável sempre que ele executa a instrução `Dim`.  Se você não especificar um valor inicial, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] atribui o valor inicial padrão para o tipo de dados da variável quando ele entra pela primeira vez o código que contém a instrução `Dim`.  
  
     Se a variável for uma tipo de referência, você pode criar uma instância de sua classe, incluindo a palavra\-chave [Operador New](../../../../visual-basic/language-reference/operators/new-operator.md) na cláusula `As`.  Se você não usar `New`, o valor inicial da variável é [nada](../../../../visual-basic/language-reference/nothing.md).  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## Consulte também  
 [Variáveis](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Nomes de elemento declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Características do elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Tipos de valor e referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Instruções](../../../../visual-basic/language-reference/statements/index.md)   
 [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Instrução Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)