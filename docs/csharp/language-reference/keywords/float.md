---
title: "float (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "float"
  - "float_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave float [C#]"
  - "números de ponto flutuante [C#], palavra-chave float"
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# float (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `float` palavra\-chave significa um tipo simples que armazena valores de ponto flutuante de 32 bits.  A tabela a seguir mostra a precisão e o intervalo aproximado para o `float` tipo.  
  
|Tipo|Intervalo aproximado|Precisão|Tipo .NET Framework|  
|----------|--------------------------|--------------|-------------------------|  
|`float`|\-3.4 × 10<sup>38</sup>to \+3.4 × 10<sup>38</sup>|7 dígitos|<xref:System.Single?displayProperty=fullName>|  
  
## Literais  
 Por padrão, um literal numérico real no lado direito do operador de atribuição é tratado como  [double](../../../csharp/language-reference/keywords/double.md).  Portanto, para inicializar uma variável float, use o sufixo `f` ou `F`, como no exemplo a seguir:  
  
```  
  
float x = 3.5F;  
```  
  
 Se você não usar o sufixo na declaração anterior, você obterá um erro de compilação porque você está tentando armazenar um  [double](../../../csharp/language-reference/keywords/double.md) de valor em um `float` variável.  
  
## Conversões  
 Você pode misturar tipos numéricos de integrais e tipos de ponto flutuante em uma expressão.  Nesse caso, os tipos integrais são convertidos para tipos de ponto flutuante.  A avaliação da expressão é realizada de acordo com as seguintes regras:  
  
-   Se um dos tipos de ponto flutuante for  [double](../../../csharp/language-reference/keywords/double.md), a expressão for avaliada como  [double](../../../csharp/language-reference/keywords/double.md) ou  [bool](../../../csharp/language-reference/keywords/bool.md) em expressões booleanas ou relacionais.  
  
-   Se não houver nenhum  [double](../../../csharp/language-reference/keywords/double.md) o tipo da expressão, a expressão for avaliada como `float` ou  [bool](../../../csharp/language-reference/keywords/bool.md) em expressões booleanas ou relacionais.  
  
 Uma expressão de ponto flutuante pode conter os seguintes conjuntos de valores:  
  
-   Zero positivo e negativo  
  
-   Infinito positivo e negativo  
  
-   Valor de não\-numéricos \(NaN\)  
  
-   O conjunto finito de valores diferentes de zero  
  
 Para obter mais informações sobre esses valores, consulte o padrão IEEE para aritmética de ponto flutuante binário, disponível na [IEEE](http://go.microsoft.com/fwlink/?LinkId=26269) site da Web.  
  
## Exemplo  
 No exemplo a seguir, um  [int](../../../csharp/language-reference/keywords/int.md), um  [curto](../../../csharp/language-reference/keywords/short.md)e um `float` estão incluídos em uma expressão matemática dando uma `float` resultado.  \(Lembre\-se de que `float` é um alias para o <xref:System.Single?displayProperty=fullName> tipo.\) Observe que não há nenhum  [double](../../../csharp/language-reference/keywords/double.md) na expressão.  
  
 [!CODE [csrefKeywordsTypes#13](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#13)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 <xref:System.Single>   
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Conversões cast e conversões de tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)