---
title: "typeof (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "typeof"
  - "typeof_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave typeof [C#]"
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# typeof (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Usado para obter o `System.Type` o objeto para um tipo.  A `typeof` expressão possui o seguinte formato:  
  
```  
System.Type type = typeof(int);  
```  
  
## Comentários  
 Para obter o tipo de tempo de execução de uma expressão, você pode usar o.Método do NET Framework <xref:System.Object.GetType%2A>, como no exemplo a seguir:  
  
```  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 O `typeof` operador não pode ser sobrecarregado.  
  
 O `typeof` pode também ser usado em tipos genéricos abertos.  Tipos com mais de um parâmetro de tipo devem ter o número apropriado de vírgulas na especificação.  O exemplo a seguir mostra como determinar se o tipo de retorno de um método é um genérico <xref:System.Collections.Generic.IEnumerable%601>.  Suponha que o método é uma instância de um tipo de MethodInfo:  
  
```  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## Exemplo  
 [!code-cs[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## Exemplo  
 Este exemplo utiliza a <xref:System.Object.GetType%2A> método para determinar o tipo que é usado para conter o resultado de um cálculo numérico.  Isso depende do número resultante, os requisitos de armazenamento.  
  
 [!code-cs[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 <xref:System.Type?displayProperty=fullName>   
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [Palavras\-chave do operador](../../../csharp/language-reference/keywords/operator-keywords.md)