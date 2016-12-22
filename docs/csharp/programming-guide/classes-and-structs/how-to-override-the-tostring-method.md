---
title: "Como substituir o m&#233;todo ToString (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "herança [C#], substituindo OnPaint e ToString"
  - "Método ToString, substituindo em C#"
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como substituir o m&#233;todo ToString (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cada classe ou struct no C\# implicitamente herda o <xref:System.Object> classe.   Portanto, cada objeto no C\# obtém o <xref:System.Object.ToString%2A> método, que retorna uma representação de seqüência de caracteres desse objeto.   Por exemplo, todas as variáveis do tipo `int` tem um `ToString` método, que permite retornar seu conteúdo como uma seqüência de caracteres:  
  
 [!code-cs[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]  
  
 Quando você criar uma personalizada, classe ou struct, você deve substituir o <xref:System.Object.ToString%2A> método para fornecer informações sobre o tipo de código do cliente.  
  
 Para obter informações sobre como usar o formato de seqüências e outros tipos de formatação personalizada com o `ToString` método, consulte [Formatando tipos](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md).  
  
> [!IMPORTANT]
>  Quando você decide quais informações devem ser fornecidas por meio desse método, considere a possibilidade de se sua classe ou struct será nunca usada pelo código não confiável.  Tenha cuidado para garantir que você não fornecer qualquer informação que pode ser explorada por código mal\-intencionado.  
  
### Para substituir o método de ToString em sua classe ou struct  
  
1.  Declarar um `ToString`o método com os seguintes modificadores e o tipo de retorno:  
  
    ```c#  
    public override string ToString(){}  
    ```  
  
2.  Implemente o método para que ele retorne uma seqüência de caracteres.  
  
     O exemplo a seguir retorna o nome da classe em juntamente com os dados específicos a uma instância particular da classe.  
  
     [!code-cs[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]  
  
     Você pode teste o `ToString` método conforme mostrado no exemplo de código a seguir:  
  
     [!code-cs[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]  
  
## Consulte também  
 <xref:System.IFormattable>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Cadeias de caracteres](../../../csharp/programming-guide/strings/index.md)   
 [cadeia de caracteres](../../../csharp/language-reference/keywords/string.md)   
 [new](../../../csharp/language-reference/keywords/new.md)   
 [override](../../../csharp/language-reference/keywords/override.md)   
 [virtual](../../../csharp/language-reference/keywords/virtual.md)   
 [Formatando tipos](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md)