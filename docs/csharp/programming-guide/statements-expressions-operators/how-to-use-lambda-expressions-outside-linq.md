---
title: "Como usar express&#245;es lambda fora do LINQ (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "expressões lambda [C#], fora do LINQ"
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como usar express&#245;es lambda fora do LINQ (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

As expressões lambda não estão limitadas a [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] consultas.  Você pode usá\-los em qualquer lugar que um valor de delegado é esperado, ou seja, sempre que um método anônimo pode ser usado.  O exemplo a seguir mostra como usar uma expressão lambda em um manipulador de eventos do Windows Forms.  Observe que os tipos de entradas \(<xref:System.Object> e <xref:System.Windows.Forms.MouseEventArgs>\) são inferidos pelo compilador e não têm a ser dada explicitamente nos parâmetros de entrada lambda.  
  
## Exemplo  
  
```  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
       this.Click += (s, e) => { MessageBox.Show(((MouseEventArgs)e).Location.ToString());};  
    }  
}  
```  
  
## Consulte também  
 [Expressões lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [Métodos anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)   
 [LINQ \(Consulta Integrada à Linguagem\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)