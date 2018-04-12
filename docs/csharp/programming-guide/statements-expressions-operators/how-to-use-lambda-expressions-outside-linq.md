---
title: Como usar expressões lambda fora do LINQ (Guia de Programação em C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c99f6bc7c9db1f0e2341c31ec5bf60217723d4e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a>Como usar expressões lambda fora do LINQ (Guia de Programação em C#)
Expressões lambda não estão limitadas a consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Você pode usá-las em qualquer lugar em que um valor de delegado é esperado, ou seja, sempre que um método anônimo puder ser usado. O exemplo a seguir mostra como usar uma expressão lambda em um manipulador de eventos do Windows Forms. Observe que os tipos das entradas (<xref:System.Object> e <xref:System.Windows.Forms.MouseEventArgs>) são inferidos pelo compilador e não precisam ser explicitamente fornecidos nos parâmetros de entrada lambda.  
  
## <a name="example"></a>Exemplo  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Métodos anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [LINQ (Consulta Integrada à Linguagem)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
