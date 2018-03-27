---
title: Cadeias de caracteres interpoladas (C#)
ms.date: 10/18/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 03315a2d9a44405ff520a1c333f56311e2657df6
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2018
---
# <a name="interpolated-strings-c-reference"></a>Cadeias de caracteres interpoladas (Referência de C#)

Usado para construir cadeias de caracteres.  Uma cadeia de caracteres interpolada é semelhante a uma cadeia de caracteres de modelo que contém *expressões interpoladas*.  Uma cadeia de caracteres interpolada retorna uma cadeia de caracteres que substitui as expressões interpoladas que ela contém por suas representações de cadeia de caracteres. Este recurso está disponível no C# 6 e versões posteriores.

Os argumentos de uma cadeia de caracteres interpolada são mais fáceis de entender do que uma [cadeia de caracteres de formato composto](../../../standard/base-types/composite-formatting.md#composite-format-string).  Por exemplo, a cadeia de caracteres interpolada  
  
```csharp  
Console.WriteLine($"Name = {name}, hours = {hours:hh}");
```  
contém duas expressões interpoladas, "{name}" e "{hours:hh}". A cadeia de caracteres de formato composto equivalente é:

```csharp
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

A estrutura de uma cadeia de caracteres interpolada é:  
  
```  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

em que: 

- *field-width* é um inteiro com sinal que indica o número de caracteres no campo. Se ele for positivo, o campo será alinhado à direita. Se for negativo, será alinhado à esquerda. 

- *format-string* é uma cadeia de caracteres de formato apropriada para o tipo do objeto que está sendo formatado. Por exemplo, para um valor <xref:System.DateTime>, pode ser uma cadeia de caracteres de formato de data e hora padrão, como "D" ou "d".

> [!IMPORTANT]
> Você não pode ter nenhum espaço em branco entre o `$` e `"` que iniciam a cadeia de caracteres. Fazer isso causa um erro em tempo de compilação.

 Você pode usar uma cadeia de caracteres interpolada em qualquer lugar em que pode usar um literal de cadeia de caracteres.  A cadeia de caracteres interpolada é avaliada sempre que o código com a cadeia de caracteres interpolada for executado. Isso permite que você separe a definição e a avaliação de uma cadeia de caracteres interpolada.  
  
 Para incluir uma chave ("{" ou "}") em uma cadeia de caracteres interpolada, use duas chaves, "{{" ou "}}".  Consulte a seção sobre [Conversões Implícitas](#implicit-conversions) para obter mais detalhes.  

Se a cadeia de caracteres interpolada contiver outros caracteres com significado especial em uma cadeia de caracteres interpolada, como aspas ("), dois-pontos (:) ou vírgulas (,), eles devem ser substituídos se ocorrerem no texto literal ou devem ser incluídos em uma expressão delimitada por parênteses se forem elementos de linguagem incluídos em uma expressão interpolada. O exemplo a seguir ignora as aspas para incluí-las na cadeia de caracteres de resultado e usa parênteses para delimitar a expressão `(age == 1 ? "" : "s")`, de modo que os dois-pontos não sejam interpretados como o início de uma cadeia de caracteres de formato.

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]  

As cadeias de caracteres textuais interpoladas usam o caractere `$` seguido pelo caractere `@`. Para obter mais informações sobre cadeias de caracteres textuais, consulte o tópico [cadeia de caracteres](string.md). O código a seguir é uma versão modificada do trecho de código anterior usando uma cadeia de caracteres textual interpolada:

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings5.cs#1)]  

As alterações de formatação são necessárias porque as cadeias de caracteres textuais não obedecem às sequências de escape `\`.

> [!IMPORTANT]
> O token `$` deve aparecer antes do token `@` em uma cadeia de caracteres textual interpolada.


## <a name="implicit-conversions"></a>Conversões implícitas  

Há três conversões de tipo implícitas de uma cadeia de caracteres interpolada:  

1. Conversão de uma cadeia de caracteres interpolada em um <xref:System.String>. O exemplo a seguir retorna uma cadeia de caracteres cujas expressões de cadeia de caracteres interpolada foram substituídas por suas representações de cadeia de caracteres. Por exemplo:

   [!code-csharp[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]  

   Esse é o resultado final de uma interpretação de cadeia de caracteres. Todas as ocorrências de chaves duplas ("{{" e "}}") serão convertidas em uma chave única. 

2. Conversão de uma cadeia de caracteres interpolada em uma variável <xref:System.IFormattable>, que permite criar várias cadeias de caracteres de resultado com conteúdo específico da cultura de uma única instância <xref:System.IFormattable>. Isso é útil para incluir itens como os formatos de número e data corretos para culturas individuais.  Todas as ocorrências de chaves duplas ("{{" e "}}") permanecem como chaves duplas até que você formate a cadeia de caracteres explícita ou implicitamente chamando o método <xref:System.Object.ToString>.  Todas as expressões de interpolação contidas são convertidas em {0}, {1} e assim por diante.  

   O exemplo a seguir usa reflexão para exibir os membros, bem como os valores de campo e propriedade de uma variável <xref:System.IFormattable> criada de uma cadeia de caracteres interpolada. Ele também passa a variável <xref:System.IFormattable> para o método <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>.

   [!code-csharp[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]  

   Observe que a cadeia de caracteres interpolada pode ser inspecionada somente usando a reflexão. Se ela for passada para um método de formatação de cadeia de caracteres, como <xref:System.Console.WriteLine(System.String)>, seus itens de formato serão resolvidos e a cadeia de caracteres de resultado será retornada. 

3. Conversão de uma cadeia de caracteres interpolada em uma variável <xref:System.FormattableString> que representa uma cadeia de caracteres de formato composto. Inspecionar a cadeia de caracteres de formato composto e como ela é renderizada como uma cadeia de caracteres de resultado pode, por exemplo, ajudar a proteger contra um ataque de injeção se você estiver criando uma consulta. <xref:System.FormattableString> também inclui sobrecargas <xref:System.FormattableString.ToString> que permitem que você gere cadeias de caracteres de resultado para a <xref:System.Globalization.CultureInfo.InvariantCulture> e a <xref:System.Globalization.CultureInfo.CurrentCulture>.  Todas as ocorrências de chaves duplas ("{{" e "}}") permanecem como chaves duplas, até você formatar.  Todas as expressões de interpolação contidas são convertidas em {0}, {1} e assim por diante.  

   [!code-csharp[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]  

## <a name="language-specification"></a>Especificação da linguagem  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 [Interpolação de cadeia de caracteres no C#](../../../csharp/tutorials/string-interpolation.md)  
 [Cadeias de caracteres interpoladas em C#](../../../csharp/quick-starts/interpolated-strings.yml)  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
