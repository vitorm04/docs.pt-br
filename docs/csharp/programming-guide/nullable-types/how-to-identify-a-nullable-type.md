---
title: "Como identificar um tipo anul&#225;vel (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "tipos anuláveis [C#], identificando"
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como identificar um tipo anul&#225;vel (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você pode usar o C\#  [typeof](../../../csharp/language-reference/keywords/typeof.md) operador para criar um <xref:System.Type> o objeto que representa um tipo anulável:  
  
```  
System.Type type = typeof(int?);  
```  
  
 Você também pode usar as classes e métodos para o <xref:System.Reflection> namespace para gerar <xref:System.Type> objetos que representam os tipos anuláveis.  No entanto, se você tenta obter informações sobre o tipo das variáveis anuláveis em tempo de execução usando o <xref:System.Object.GetType%2A> método ou a `is` operador, o resultado é um <xref:System.Type> tipo de objeto que representa o tipo subjacente, e não o Nullable propriamente dito.  
  
 Chamando `GetType` em um Nullable tipo faz com que uma operação de conversão boxing deve ser executada quando o tipo é implicitamente convertido para <xref:System.Object>.  Portanto, <xref:System.Object.GetType%2A> sempre retorna um <xref:System.Type> o objeto que representa o tipo subjacente, e não do tipo anulável.  
  
```  
int? i = 5;  
Type t = i.GetType();  
Console.WriteLine(t.FullName); //"System.Int32"  
```  
  
 C\#  [é](../../../csharp/language-reference/keywords/is.md) operador também opera no tipo subjacente de um Nullable.  Portanto, você não pode usar `is` para determinar se uma variável é um tipo anulável.  O exemplo a seguir mostra que o `is` operador trata um Nullable \<int\> variável como int.  
  
```  
static void Main(string[] args)  
{  
  int? i = 5;  
  if (i is int) // true  
    //…  
}  
```  
  
## Exemplo  
 Use o código a seguir para determinar se um <xref:System.Type> objeto representa um tipo anulável.  Lembre\-se de que esse código sempre retorna falso se o `Type` objeto foi retornado de uma chamada para <xref:System.Object.GetType%2A>, conforme explicado anteriormente neste tópico.  
  
```  
if (type.IsGenericType && type.GetGenericTypeDefinition() == typeof(Nullable<>)) {…}  
```  
  
## Consulte também  
 [Tipos anuláveis](../../../csharp/programming-guide/nullable-types/index.md)   
 [Executando a conversão boxing de tipos anuláveis](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)