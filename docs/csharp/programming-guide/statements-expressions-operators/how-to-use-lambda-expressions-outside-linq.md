---
title: 'Como: usar expressões lambda fora do LINQ – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: c66dea393ad2351402f54b2391d424701208eba2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619810"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a>Como: usar expressões lambda fora do LINQ (Guia de Programação em C#)
Expressões lambda não estão limitadas a consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Você pode usá-las em qualquer lugar em que um valor de delegado é esperado, ou seja, sempre que um método anônimo puder ser usado. O exemplo a seguir mostra como usar uma expressão lambda em um manipulador de eventos do Windows Forms. Observe que os tipos das entradas (<xref:System.Object> e <xref:System.Windows.Forms.MouseEventArgs>) são inferidos pelo compilador e não precisam ser explicitamente fornecidos nos parâmetros de entrada lambda.  
  
## <a name="example"></a>Exemplo  
  
```csharp  
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

- [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Métodos anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
- [LINQ (Consulta integrada à linguagem)](../../../csharp/programming-guide/concepts/linq/index.md)
