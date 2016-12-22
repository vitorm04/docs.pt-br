---
title: "short (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "short"
  - "short_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave curta [C#]"
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# short (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `short` palavra\-chave denota um tipo de dados integral que armazena valores de acordo com o tamanho e o intervalo, mostrado na tabela a seguir.  
  
|Tipo|Intervalo|Tamanho|Tipo .NET Framework|  
|----------|---------------|-------------|-------------------------|  
|`short`|\-32.768 a 32.767|Inteiro assinado de 16 bits|<xref:System.Int16?displayProperty=fullName>|  
  
## Literais  
 Você pode declarar e inicializar um `short` variável semelhante ao exemplo:  
  
```  
  
short x = 32767;  
```  
  
 Na declaração precedente, a literal inteira `32767` é convertido implicitamente de  [int](../../../csharp/language-reference/keywords/int.md) para `short`.  Se a literal inteira não cabe em um `short` o local de armazenamento, um erro de compilação ocorrerá.  
  
 Uma conversão deve ser usada quando chamada sobrecarregado métodos.  Considere, por exemplo, o seguinte sobrecarregado métodos que usam `short` e  [int](../../../csharp/language-reference/keywords/int.md) parâmetros:  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 Usando o `short` cast garante que o tipo correto é chamado, por exemplo:  
  
```  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## Conversões  
 Há uma conversão implícita predefinida de `short` para  [int](../../../csharp/language-reference/keywords/int.md),  [longo](../../../csharp/language-reference/keywords/long.md),  [float](../../../csharp/language-reference/keywords/float.md),  [double](../../../csharp/language-reference/keywords/double.md), ou  [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Você não pode converter implicitamente nonliteral tipos numéricos de maior tamanho de armazenamento para `short` \(consulte [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md) para os tamanhos de armazenamento dos tipos integrais\).  Considere, por exemplo, os dois seguintes `short` variáveis de `x` e `y`:  
  
```  
  
short x = 5, y = 12;  
```  
  
 A instrução de atribuição a seguir gerará um erro de compilação, porque a expressão aritmética do operador de atribuição no lado direito é avaliada, por padrão, como [int](../../../csharp/language-reference/keywords/int.md).  
  
 `short`   `z = x + y;   // Error: no conversion from int to short`  
  
 Para corrigir esse problema, use um cast:  
  
 `short`   `z = (`  `short`  `)(x + y);   // OK: explicit conversion`  
  
 No entanto é possível usar as instruções a seguir, onde a variável de destino tem o mesmo tamanho de armazenamento ou um tamanho maior de armazenamento:  
  
```  
int m = x + y;  
long n = x + y;  
```  
  
 Não há nenhuma conversão implícita de tipos de ponto flutuante para `short`.  Por exemplo, a instrução a seguir gera um erro do compilador, a menos que seja usada uma conversão explícita:  
  
```  
  
        short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 Para obter informações sobre expressões aritméticas com tipos mistos de ponto flutuante e tipos integrais, consulte  [float](../../../csharp/language-reference/keywords/float.md) e  [double](../../../csharp/language-reference/keywords/double.md).  
  
 Para obter mais informações sobre regras de conversão numérica implícito, consulte o [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 <xref:System.Int16>   
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)