---
title: Cadeias de caracteres interpoladas (C#)
ms.date: 2017-02-03
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: 9
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 29790cadd30e9aca56d7ba4c8d7a945b4f891f35
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="interpolated-strings-c-reference"></a>Cadeias de caracteres interpoladas (Referência de C#)

Usado para construir cadeias de caracteres.  Uma cadeia de caracteres interpolada é semelhante a uma cadeia de caracteres de modelo que contém *expressões interpoladas*.  Uma cadeia de caracteres interpolada retorna uma cadeia de caracteres que substitui as expressões interpoladas que ela contém por suas representações de cadeia de caracteres.  

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

- *format-string* é uma cadeia de caracteres de formato apropriada para o tipo do objeto que está sendo formatado. Por exemplo, para um valor @System.DateTime, pode ser uma cadeia de caracteres de formato de data e hora padrão, como "D" ou "d".

 Você pode usar uma cadeia de caracteres interpolada em qualquer lugar em que pode usar um literal de cadeia de caracteres.  A cadeia de caracteres interpolada é avaliada sempre que o código com a cadeia de caracteres interpolada for executado. Isso permite que você separe a definição e a avaliação de uma cadeia de caracteres interpolada.  
  
 Para incluir uma chave ("{" ou "}") em uma cadeia de caracteres interpolada, use duas chaves, "{{" ou "}}".  Consulte a seção sobre Conversões implícitas para obter mais detalhes.  

Se a cadeia de caracteres interpolada contiver outros caracteres com significado especial em uma cadeia de caracteres interpolada, como aspas ("), dois-pontos (:) ou vírgulas (,), eles devem ser substituídos se ocorrerem no texto literal ou devem ser incluídos em uma expressão delimitada por parênteses se forem elementos de linguagem incluídos em uma expressão interpolada. O exemplo a seguir ignora as aspas para incluí-las na cadeia de caracteres de resultado e usa parênteses para delimitar a expressão `(age == 1 ? "" : "s")`, de modo que os dois-pontos não sejam interpretados como o início de uma cadeia de caracteres de formato.

[!code-cs[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]  

## <a name="implicit-conversions"></a>Conversões implícitas  

Há três conversões de tipo implícitas de uma cadeia de caracteres interpolada:  

1. Conversão de uma cadeia de caracteres interpolada em um @System.String. O exemplo a seguir retorna uma cadeia de caracteres cujas expressões de cadeia de caracteres interpolada foram substituídas por suas representações de cadeia de caracteres. Por exemplo:

   [!code-cs[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]  

   Esse é o resultado final de uma interpretação de cadeia de caracteres. Todas as ocorrências de chaves duplas ("{{" e "}}") serão convertidas em uma chave única. 

2. Conversão de uma cadeia de caracteres interpolada em uma variável <xref:System.IFormattable> que permite criar várias cadeias de caracteres de resultado com conteúdo específico da cultura de uma única instância <xref:System.IFormattable>. Isso é útil para incluir itens como os formatos de número e data corretos para culturas individuais.  Todas as ocorrências de chaves duplas ("{{" e "}}") permanecem como chaves duplas até que você formate a cadeia de caracteres explícita ou implicitamente chamando o método @System.Object.ToString.  Todas as expressões de interpolação contidas são convertidas em {0}, {1} e assim por diante.  

   O exemplo a seguir usa reflexão para exibir os membros, bem como os valores de campo e propriedade de uma variável <xref:System.IFormattable> criada de uma cadeia de caracteres interpolada. Ela também passa a variável <xref:System.IFormattable> para o método @System.Console(System.String).

   [!code-cs[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]  

   Observe que a cadeia de caracteres interpolada pode ser inspecionada somente usando a reflexão. Se ela for passada para um método de formatação de cadeia de caracteres, como @System.Console.WriteLine(System.String), seus itens de formato serão resolvidos e a cadeia de caracteres de resultado será retornada. 

3. Conversão de uma cadeia de caracteres interpolada em uma variável <xref:System.FormattableString> que representa uma cadeia de caracteres de formato composto. Inspecionar a cadeia de caracteres de formato composto e como ela é renderizada como uma cadeia de caracteres de resultado pode, por exemplo, ajudar a proteger contra um ataque de injeção se você estiver criando uma consulta.  <xref:System.FormattableString> também inclui sobrecargas <xref:System.FormattableString.ToString> que permitem que você gere cadeias de caracteres de resultado para a @System.Globalization.InvariantCulture e a @System.Globalization.CurrentCulture.  Todas as ocorrências de chaves duplas ("{{" e "}}") permanecem como chaves duplas, até você formatar.  Todas as expressões de interpolação contidas são convertidas em {0}, {1} e assim por diante.  

   [!code-cs[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]  

## <a name="language-specification"></a>Especificação da linguagem  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IFormattable?displayProperty=fullName>   
 <xref:System.FormattableString?displayProperty=fullName>   
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)

