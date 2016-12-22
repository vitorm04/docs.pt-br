---
title: "Cadeias de caracteres interpoladas (refer&#234;ncia do C# e do Visual Basic) | Microsoft Docs"
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
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Cadeias de caracteres interpoladas (refer&#234;ncia do C# e do Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Usado para construir cadeias de caracteres.  Uma expressão de cadeia de caracteres interpolados se parece com uma cadeia de caracteres de modelo que contém expressões.  Uma expressão de cadeia de caracteres interpolados cria uma cadeia de caracteres, substituindo as expressões independentes com o represenations ToString dos resultados de expressões.  Uma cadeia de caracteres interpolada é mais fácil compreender em relação a argumentos que [Formatação composta](../Topic/Composite%20Formatting.md).  Aqui está um exemplo de uma cadeia de caracteres interpolado:  
  
```c#  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")  
```  
  
 A estrutura de uma cadeia de caracteres interpolada é da seguinte maneira:  
  
```  
$ " <text> { <interpolation-expression> <optional-comma-field-width> <optional-colon-format> } <text> ... } "  
```  
  
 Você pode usar uma cadeia de caracteres interpolada em qualquer lugar que você pode usar um literal de cadeia de caracteres.  Ao executar o programa poderia executar o código com um literal de cadeia interpolado, o código calcula uma nova cadeia de caracteres literal pela avaliação das expressões de interpolação.  Esse cálculo ocorre sempre que o código com a cadeia de caracteres interpolado é executado.  
  
 Para incluir uma chave de abertura \("{" ou "}"\) em uma cadeia de caracteres interpolada usar duas chaves, "{{" ou "}}".  Consulte a seção de conversões implícitas para obter mais detalhes.  
  
## Conversões implícitas  
 Há conversões implícitas de tipo de uma cadeia de caracteres interpolada:  
  
```c#  
var s = $"hello, {name}" System.IFormattable s = $"Hello, {name}" System.FormattableString s = $"Hello, {name}"  
  
```  
  
 O primeiro exemplo produz uma `string` valor onde todos os valores de interpolação de cadeia de caracteres terem sido computados.  É o resultado final e tem tipo cadeia de caracteres.  Todas as ocorrências de colchetes duplos \("{{" e "}}"\) são convertidos em uma única chave.  
  
 O segundo exemplo produz um <xref:System.IFormattable> variável que permite converter a cadeia de caracteres com contexto invariável.  Isso é útil para obter numérico e formatos de dados corrija em idiomas diferentes.  Todas as ocorrências de colchetes duplos \("{{" e "}}"\) permanecem como chaves duplas, até que o formato de cadeia de caracteres com ToString.  Todas as expressões de interpolação contidos são convertidas em {0}, \\{1\\}, e assim por diante.  
  
```c#  
s.ToString(null, System.Globalization.CultureInfo.InvariantCulture);  
```  
  
 O terceiro exemplo produz um <xref:System.FormattableString>, que lhe permite inspecionar os objetos que resultam das computações de interpolação.  Objetos de inspeção e como eles processem como cadeias de caracteres, por exemplo, ajudam a proteger contra um ataque de injeção, se você estivesse criando uma consulta.  Com <xref:System.FormattableString>, você tem operações de conveniência para produzir os resultados de cadeia de caracteres InvariantCulture e CurrentCulture.  Todas as ocorrências de colchetes duplos \("{{" e "}}"\) permanecem como chaves duplas, até você formatar.  Todas as expressões de interpolação contidos são convertidas em {0}, \\{1\\}, e assim por diante.  
  
## Exemplos  
  
```c#  
$"Name = {name}, hours = {hours:hh}" var s = $"hello, {name}" System.IFormattable s = $"Hello, {name}" System.FormattableString s = $"Hello, {name}" $"{person.Name, 20} is {person.Age:D3} year {(p.Age == 1 ? "" : "s")} old."  
  
```  
  
 Você não precisa citar os caracteres de aspas simples dentro de expressões a interpolação independente como cadeia de caracteres interpolada expressões começam com $ e o compilador examina as expressões de interpolação independente como texto equilibrado até encontrar uma vírgula, vírgula ou chave de fechamento.  Pelas mesmas razões, o último exemplo usa parênteses para permitir que a expressão condicional \(`p.Age == 1 ? "" : "s"`\) pode estar dentro da expressão de interpolação sem os dois pontos iniciando uma especificação de formato.  Fora da expressão de interpolação independente \(mas ainda dentro da expressão de cadeia de caracteres interpolados\) é substituir caracteres de aspas simples como faria normalmente.  
  
## Sintaxe  
  
```  
expression: interpolated-string-expression interpolated-string-expression: interpolated-string-start interpolations interpolated-string-end interpolations: single-interpolation single-interpolation interpolated-string-mid interpolations single-interpolation: interpolation-start interpolation-start : regular-string-literal interpolation-start: expression expression , expression  
  
```  
  
## Especificações da linguagem  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
 Para obter mais informações, consulte o [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md).  
  
## Consulte também  
 <xref:System.IFormattable?displayProperty=fullName>   
 <xref:System.FormattableString?displayProperty=fullName>   
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md)   
 [Guia de programação do Visual Basic](../../../visual-basic/programming-guide/index.md)