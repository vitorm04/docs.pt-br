---
title: "decimal (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "decimal_CSharpKeyword"
  - "decimal"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave decimal [C#]"
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
caps.latest.revision: 32
caps.handback.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# decimal (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A palavra\-chave `decimal` indica um tipo de dados de 128 bits.  Comparado aos tipos de pontos flutuantes, o tipo `decimal` tem mais precisão e um intervalo menor que o torna apropriado para cálculos financeiros e monetários.  O intervalo e a precisão aproximados para o tipo `decimal` são mostrados na tabela a seguir.  
  
|Tipo|Intervalo aproximado|Precisão|Tipo do .NET Framework|  
|----------|--------------------------|--------------|----------------------------|  
|`decimal`|\(\-7,9 x 10<sup>28</sup> a 7,9 x 10<sup>28</sup>\) \/ \(10<sup>0 a 28</sup>\)|28 a 29 dígitos significativos|<xref:System.Decimal?displayProperty=fullName>|  
  
## Literais  
 Se você desejar tratar um literal numérico como `decimal`, use o sufixo m ou M, por exemplo:  
  
```  
  
decimal myMoney = 300.5m;  
```  
  
 Sem o sufixo m, o número será tratado como [double](../../../csharp/language-reference/keywords/double.md) e gerará um erro do compilador.  
  
## Conversões  
 Os tipos integrais são convertidos implicitamente em `decimal` e o resultado é avaliado como `decimal`.  Portanto, você pode inicializar uma variável decimal com um literal inteiro sem o sufixo como a seguir:  
  
```  
  
decimal myMoney = 300;  
```  
  
 Não há nenhuma conversão implícita entre os tipos de pontos flutuantes e o tipo `decimal`. Portanto, uma conversão deve ser usada para converter entre esses dois tipos.  Por exemplo:  
  
```  
  
        decimal myMoney = 99.9m;  
double x = (double)myMoney;  
myMoney = (decimal)x;  
```  
  
 Você também pode misturar `decimal` e tipos integrais numéricos na mesma expressão.  No entanto, misturar `decimal` e tipos de pontos flutuantes sem uma conversão causa um erro de compilação.  
  
 Para obter mais informações sobre conversões numéricas implícitas, consulte [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
 Para obter mais informações sobre conversões numéricas explícitas, consulte [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
## Formatando saída decimal  
 Você pode formatar os resultados ao usar o método `String.Format` ou <xref:System.Console.Write%2A?displayProperty=fullName> que chama `String.Format()`.  O formato de moeda é especificado ao usar a cadeia de caracteres de formato de moeda padrão "C" ou "c", como mostrado no segundo exemplo posteriormente neste artigo.  Para obter mais informações sobre o método `String.Format`, consulte <xref:System.String.Format%2A?displayProperty=fullName>.  
  
## Exemplo  
 O exemplo a seguir causa um erro do compilador ao tentar adicionar variáveis [double](../../../csharp/language-reference/keywords/double.md) e `decimal`.  
  
```c#  
double dub = 9;  
// The following line causes an error that reads "Operator '+' cannot be applied to   
// operands of type 'double' and 'decimal'"  
Console.WriteLine(dec + dub);   
  
// You can fix the error by using explicit casting of either operand.  
Console.WriteLine(dec + (decimal)dub);  
Console.WriteLine((double)dec + dub);  
  
```  
  
 O resultado é o seguinte erro:  
  
 `Operator '+' cannot be applied to operands of type 'double' and 'decimal'`  
  
 Neste exemplo, `decimal` e [int](../../../csharp/language-reference/keywords/int.md) são misturados na mesma expressão.  O resultado é avaliado como o tipo `decimal`.  
  
 [!CODE [csrefKeywordsTypes#6](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#6)]  
  
## Exemplo  
 Neste exemplo, a saída é formatada usando a cadeia de caracteres de formato de moeda.  Observe que `x` é arredondado porque as casas decimais excedem US$ 0,99.  A variável `y`, que representa os dígitos exatos máximos, é exibida exatamente no formato correto.  
  
 [!CODE [csrefKeywordsTypes#7](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#7)]  
  
## Especificação da Linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 <xref:System.Decimal>   
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)   
 [Cadeias de caracteres de formato numérico padrão](../Topic/Standard%20Numeric%20Format%20Strings.md)