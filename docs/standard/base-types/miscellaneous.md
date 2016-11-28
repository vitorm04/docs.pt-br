---
title: "Constructos diversos em expressões regulares"
description: "Constructos diversos em expressões regulares"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 478901dc-db6c-4d90-9d3b-f5cfdca2cbf5
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 4205d2a318849a7b24ac0f1fd65f7e8a23ec7f55

---

# <a name="miscellaneous-constructs-in-regular-expressions"></a>Constructos diversos em expressões regulares


As expressões regulares em .NET incluem três constructos diversos de linguagem. Um deles permite habilitar ou desabilitar opções específicas de correspondência no meio de um padrão de expressão regular. Os dois restantes permitem incluir comentários em uma expressão regular.

## <a name="inline-options"></a>Opções embutidas

É possível definir ou desabilitar opções específicas de correspondência de padrão para parte de uma expressão regular mediante uso da sintaxe

```
(?imnsx-imnsx)
```

Você lista as opções que deseja habilitar após o ponto de interrogação e as opções que deseja desabilitar após o sinal de subtração. A tabela a seguir descreve cada opção. Para obter mais informações sobre cada opção, consulte [Opções de expressões regulares](options.md).

Opção | Descrição
------ | ----------- 
**i** | Correspondência sem diferenciação entre maiúsculas e minúsculas.
**m** | Modo multilinha.
**n** | Apenas capturas explícitas. (Parênteses não funcionam como grupos de captura.)
**s** | Modo de linha única.
**x** | Ignorar espaço em branco sem escape e permitir comentários no modo x. 
 
Qualquer alteração nas opções de expressões regulares definida pelo constructo **(?imnsx-imnsx)** permanece em vigor até o fim do grupo delimitador.

> [!NOTE]
> O constructo de agrupamento **(?imnsx-imnsx**:_subexpression_**)** oferece uma funcionalidade idêntica para uma subexpressão. Para obter mais informações, consulte [Constructos de agrupamento em expressões regulares](grouping.md).
 
O exemplo a seguir usa as opções **i**, **n** e **x** para desabilitar a diferenciação entre maiúsculas e minúsculas e habilitar e capturas explícitas, bem como ignorar o espaço em branco no padrão de expressão regular no meio de uma expressão regular. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern; 
      string input = "double dare double Double a Drooling dog The Dreaded Deep";

      pattern = @"\b(D\w+)\s(d\w+)\b";
      // Match pattern using default options.
      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine(match.Value);
         if (match.Groups.Count > 1)
            for (int ctr = 1; ctr < match.Groups.Count; ctr++) 
               Console.WriteLine("   Group {0}: {1}", ctr, match.Groups[ctr].Value);
      }
      Console.WriteLine();

      // Change regular expression pattern to include options.
      pattern = @"\b(D\w+)(?ixn) \s (d\w+) \b";
      // Match new pattern with options. 
      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine(match.Value);
         if (match.Groups.Count > 1)
            for (int ctr = 1; ctr < match.Groups.Count; ctr++) 
               Console.WriteLine("   Group {0}: '{1}'", ctr, match.Groups[ctr].Value);
      }
   }
}
// The example displays the following output:
//       Drooling dog
//          Group 1: Drooling
//          Group 2: dog
//       
//       Drooling dog
//          Group 1: 'Drooling'
//       Dreaded Deep
//          Group 1: 'Dreaded'
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String 
      Dim input As String = "double dare double Double a Drooling dog The Dreaded Deep"

      pattern = "\b(D\w+)\s(d\w+)\b"
      ' Match pattern using default options.
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
         If match.Groups.Count > 1 Then
            For ctr As Integer = 1 To match.Groups.Count - 1 
               Console.WriteLine("   Group {0}: {1}", ctr, match.Groups(ctr).Value)
            Next
         End If
      Next
      Console.WriteLine()

      ' Change regular expression pattern to include options.
      pattern = "\b(D\w+)(?ixn) \s (d\w+) \b"
      ' Match new pattern with options. 
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
         If match.Groups.Count > 1 Then
            For ctr As Integer = 1 To match.Groups.Count - 1 
               Console.WriteLine("   Group {0}: '{1}'", ctr, match.Groups(ctr).Value)
            Next
         End If
      Next
   End Sub
End Module
' The example displays the following output:
'       Drooling dog
'          Group 1: Drooling
'          Group 2: dog
'       
'       Drooling dog
'          Group 1: 'Drooling'
'       Dreaded Deep
'          Group 1: 'Dreaded'
```

O exemplo define duas expressões regulares. A primeira, `\b(D\w+)\s(d\w+)\b`, corresponde a duas palavras consecutivas que começam com um “D” maiúsculo e um “d” minúsculo. A segunda expressão regular, `\b(D\w+)(?ixn) \s (d\w+) \b`, usa opções embutidas para modificar esse padrão, conforme descrito na tabela a seguir. Uma comparação dos resultados confirma o efeito do constructo `(?ixn)`.

Padrão | Descrição
------- | ----------- 
`\b` | Iniciar em um limite de palavra.
`(D\w+)` | Corresponder a um “D” maiúsculo seguido por um ou mais caracteres de palavra. Este é o primeiro grupo de captura.
`(?ixn)` | Desse ponto em diante, faça comparações sem distinção de maiúsculas e minúsculas, faça apenas capturas explícitas e ignore o espaço em branco no padrão de expressão regular.
`\s` | Corresponde a um caractere de espaço em branco.
`(d\w+)` | Corresponder a um “d” maiúsculo ou minúsculo seguido por um ou mais caracteres de palavra. Este grupo não foi capturado porque a opção n (captura explícita) estava habilitada.
`\b` | Corresponder a um limite de palavra.
 
## <a name="inline-comment"></a>Comentário embutido

O constructo **(?#** _comment_**)** permite incluir um comentário embutido em uma expressão regular. O mecanismo de expressões regulares não usa nenhuma parte do comentário na correspondência de padrão, apesar de o comentário estar incluído na cadeia de caracteres que é retornada pelo método [Regex.ToString](xref:System.Text.RegularExpressions.Regex.Unescape(System.String)). O comentário é encerrado no primeiro caractere de fechar parênteses.

O exemplo a seguir repete o primeiro padrão de expressão regular do exemplo na seção anterior. Ele adiciona dois comentários embutidos na expressão regular para indicar se a comparação diferencia maiúsculas de minúsculas. O padrão de expressão regular, `\b((?# case-sensitive comparison)D\w+)\s((?#case-insensitive comparison)d\w+)\b`, é definido da seguinte forma.

Padrão | Descrição
------- | ----------- 
`\b` | Iniciar em um limite de palavra.
`(?# case-sensitive comparison)` | Um comentário. Não afeta o comportamento de correspondência.
`(D\w+)` | Corresponder a um “D” maiúsculo seguido por um ou mais caracteres de palavra. Este é o primeiro grupo de captura.
`\s` | Corresponde a um caractere de espaço em branco.
`(?ixn)` |`Desse ponto em diante, faça comparações sem distinção de maiúsculas e minúsculas, faça apenas capturas explícitas e ignore o espaço em branco no padrão de expressão regular.
`(?#case-insensitive comparison)` | Um comentário. Não afeta o comportamento de correspondência. 
`(d\w+)` | Corresponder a um “d” maiúsculo ou minúsculo seguido por um ou mais caracteres de palavra. Este é o segundo grupo de captura.
`\b` | Corresponder a um limite de palavra.
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b((?# case sensitive comparison)D\w+)\s(?ixn)((?#case insensitive comparison)d\w+)\b";
      Regex rgx = new Regex(pattern);
      string input = "double dare double Double a Drooling dog The Dreaded Deep";

      Console.WriteLine("Pattern: " + pattern.ToString());
      // Match pattern using default options.
      foreach (Match match in rgx.Matches(input))
      {
         Console.WriteLine(match.Value);
         if (match.Groups.Count > 1)
         {
            for (int ctr = 1; ctr <match.Groups.Count; ctr++) 
               Console.WriteLine("   Group {0}: {1}", ctr, match.Groups[ctr].Value);
         }
      }
   }
}
// The example displays the following output:
//    Pattern: \b((?# case sensitive comparison)D\w+)\s(?ixn)((?#case insensitive comp
//    arison)d\w+)\b
//    Drooling dog
//       Group 1: Drooling
//    Dreaded Deep
//       Group 1: Dreaded
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b((?# case sensitive comparison)D\w+)\s(?ixn)((?#case insensitive comparison)d\w+)\b"
      Dim rgx As New Regex(pattern)
      Dim input As String = "double dare double Double a Drooling dog The Dreaded Deep"

      Console.WriteLine("Pattern: " + pattern.ToString())
      ' Match pattern using default options.
      For Each match As Match In rgx.Matches(input)
         Console.WriteLine(match.Value)
         If match.Groups.Count > 1 Then
            For ctr As Integer = 1 To match.Groups.Count - 1 
               Console.WriteLine("   Group {0}: {1}", ctr, match.Groups(ctr).Value)
            Next
         End If
      Next
   End Sub
End Module
' The example displays the following output:
'    Pattern: \b((?# case sensitive comparison)D\w+)\s(?ixn)((?#case insensitive comp
'    arison)d\w+)\b
'    Drooling dog
'       Group 1: Drooling
'    Dreaded Deep
'       Group 1: Dreaded
```

## <a name="end-of-line-comment"></a>Comentário de final de linha

Um sinal numérico (**#**) marca um comentário do modo x, que começa com o caractere # sem escape no final do padrão de expressão regular e continua até o final da linha. Para usar esse constructo, deve-se habilitar a opção **x** (por meio de opções embutidas) ou fornecer o valor [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) para o parâmetro *option* ao instanciar o objeto [Regex](xref:System.Text.RegularExpressions.Regex) ou chamar um método [Regex](xref:System.Text.RegularExpressions.Regex) estático. 

O exemplo a seguir ilustra o constructo do comentário de final de linha. Ele determina se uma cadeia de caracteres é uma cadeia de caracteres de formato de composição que inclui pelo menos um item de formato. A tabela a seguir descreve os constructos no padrão de expressão regular: 

`\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item`. 

Padrão | Descrição
------- | ----------- 
`\{` | Corresponder a uma chave de abertura.
`\d+` | Corresponde a um ou mais dígitos decimais.
`(,-*\d+)*` | Corresponder a zero ou a uma ocorrência de vírgula, seguida por um sinal de subtração opcional, seguido por um ou mais dígitos decimais.
`(\:\w{1,4}?)*` | Corresponder a zero ou a uma ocorrência de dois-pontos, seguido de um a quatro caracteres em branco, mas o mínimo possível.
`(?#case insensitive comparison)` | Um comentário embutido. Não tem nenhum efeito no comportamento de correspondência de padrão.
`\}` | Corresponder a uma chave de fechamento.
`(?x)` | Habilitar a opção de ignorar espaço em branco no padrão para o comentário de final de linha ser reconhecido.
`# Looks for a composite format item.` | Um comentário de final de linha.
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.";
      string input = "{0,-3:F}";
      Console.WriteLine("'{0}':", input);
      if (Regex.IsMatch(input, pattern))
         Console.WriteLine("   contains a composite format item.");
      else
         Console.WriteLine("   does not contain a composite format item.");
   }
}
// The example displays the following output:
//       '{0,-3:F}':
//          contains a composite format item.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item."
      Dim input As String = "{0,-3:F}"
      Console.WriteLine("'{0}':", input)
      If Regex.IsMatch(input, pattern) Then
         Console.WriteLine("   contains a composite format item.")
      Else
         Console.WriteLine("   does not contain a composite format item.")
      End If
   End Sub
End Module
' The example displays the following output:
'       '{0,-3:F}':
'          contains a composite format item.
```

Observe que, em vez de fornecer o constructo `(?x)` na expressão regular, o comentário também poderia ter sido reconhecido chamando o método [Regex.IsMatch(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) e passando-o para o valor de enumeração [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace).

## <a name="see-also"></a>Consulte também

[Linguagem de expressão regular – referência rápida](quick-ref.md)




<!--HONumber=Nov16_HO4-->


