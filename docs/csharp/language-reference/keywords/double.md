---
title: "double (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "double"
  - "double_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "tipo de dados double [C#]"
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# double (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `double` palavra\-chave significa um tipo simples que armazena valores de ponto flutuante de 64 bits.  A tabela a seguir mostra a precisão e o intervalo aproximado para o `double` tipo.  
  
|Tipo|Intervalo aproximado|Precisão|Tipo .NET Framework|  
|----------|--------------------------|--------------|-------------------------|  
|`double`|±5.0 × 10<sup>−324</sup> para ±1.7 × 10<sup>308</sup>|15\-16 dígitos|<xref:System.Double?displayProperty=fullName>|  
  
## Literais  
 Por padrão, um literal numérico real no lado direito do operador de atribuição é tratado como `double`.  No entanto, se você deseja um número inteiro deve ser tratado como `double`, use o d de sufixo ou a D, por exemplo:  
  
```  
  
double x = 3D;  
```  
  
## Conversões  
 Você pode misturar tipos numéricos de integrais e tipos de ponto flutuante em uma expressão.  Nesse caso, os tipos integrais são convertidos para tipos de ponto flutuante.  A avaliação da expressão é realizada de acordo com as seguintes regras:  
  
-   Se um dos tipos de ponto flutuante for `double`, a expressão for avaliada como `double`, ou  [bool](../../../csharp/language-reference/keywords/bool.md) em expressões booleanas ou relacionais.  
  
-   Se não houver nenhum `double` tipo na expressão, ele será avaliado como  [float](../../../csharp/language-reference/keywords/float.md), ou  [bool](../../../csharp/language-reference/keywords/bool.md) em expressões booleanas ou relacionais.  
  
 Uma expressão de ponto flutuante pode conter os seguintes conjuntos de valores:  
  
-   Zero positivo e negativo.  
  
-   Infinito positivo e negativo.  
  
-   Valor de não\-numéricos \(NaN\).  
  
-   O conjunto finito de valores diferentes de zero.  
  
 Para obter mais informações sobre esses valores, consulte o padrão IEEE para aritmética de ponto flutuante binário, disponível na [IEEE](http://go.microsoft.com/fwlink/?LinkId=26269) site da Web.  
  
## Exemplo  
 No exemplo a seguir, um  [int](../../../csharp/language-reference/keywords/int.md), um  [curto](../../../csharp/language-reference/keywords/short.md), um  [float](../../../csharp/language-reference/keywords/float.md)e um `double` são adicionados, oferecendo uma `double` resultado.  
  
 [!CODE [csrefKeywordsTypes#9](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#9)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de valores padrão](../../../csharp/language-reference/keywords/default-values-table.md)   
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de tipos de ponto flutuante](../../../csharp/language-reference/keywords/floating-point-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)