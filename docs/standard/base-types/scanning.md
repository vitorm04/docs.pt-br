---
title: "Exemplo de expressão regular: verificação de HREFs"
description: "Exemplo de expressão regular: verificação de HREFs"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: d6484880-bdac-47cd-b5e5-9419c9ed14cd
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 494ceeb2cc3bbf77098d2b6145690e7229ed3b9f

---

# <a name="regular-expression-example-scanning-for-hrefs"></a>Exemplo de expressão regular: verificação de HREFs

O exemplo a seguir procura uma cadeia de caracteres de entrada e exibe todos os valores href="…" e suas localizações na cadeia de caracteres. 

## <a name="the-regex-object"></a>O objeto Regex

Como o método `DumpHRefs` pode ser chamado diversas vezes com o código do usuário, utiliza o método `static` [Regex.Match(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions)). Isso permite que o mecanismo de expressões regulares armazene em cache a expressão regular e evite a sobrecarga de instanciar um novo objeto [Regex](xref:System.Text.RegularExpressions.Regex) cada vez que o método é chamado. Um objeto [Match](xref:System.Text.RegularExpressions.Match) é usado para iterar por todas as correspondências na cadeia de caracteres. 

```csharp
private static void DumpHRefs(string inputString) 
{
   Match m;
   string HRefPattern = "href\\s*=\\s*(?:[\"'](?<1>[^\"']*)[\"']|(?<1>\\S+))";

   try {
      m = Regex.Match(inputString, HRefPattern, 
                      RegexOptions.IgnoreCase | RegexOptions.Compiled, 
                      TimeSpan.FromSeconds(1));
      while (m.Success)
      {
         Console.WriteLine("Found href " + m.Groups[1] + " at " 
            + m.Groups[1].Index);
         m = m.NextMatch();
      }   
   }
   catch (RegexMatchTimeoutException) {
      Console.WriteLine("The matching operation timed out.");
   }
}
```

```vb
Private Sub DumpHRefs(inputString As String) 
   Dim m As Match
   Dim HRefPattern As String = "href\s*=\s*(?:[""'](?<1>[^""']*)[""']|(?<1>\S+))"

   Try
      m = Regex.Match(inputString, HRefPattern, _ 
                      RegexOptions.IgnoreCase Or RegexOptions.Compiled,
                      TimeSpan.FromSeconds(1))
      Do While m.Success
         Console.WriteLine("Found href {0} at {1}.", _
                           m.Groups(1), m.Groups(1).Index)
         m = m.NextMatch()
      Loop   
   Catch e As RegexMatchTimeoutException
      Console.WriteLine("The matching operation timed out.")
   End Try
End Sub
```

O exemplo a seguir mostra uma chamada para o método `DumpHRefs`.

```csharp
public static void Main()
{
   string inputString = "My favorite web sites include:</P>" +
                        "<A HREF=\"http://msdn2.microsoft.com\">" +
                        "MSDN Home Page</A></P>" +
                        "<A HREF=\"http://www.microsoft.com\">" +
                        "Microsoft Corporation Home Page</A></P>" +
                        "<A HREF=\"http://blogs.msdn.com/bclteam\">" +
                        ".NET Base Class Library blog</A></P>";
   DumpHRefs(inputString);                     

}
// The example displays the following output:
//       Found href http://msdn2.microsoft.com at 43
//       Found href http://www.microsoft.com at 102
//       Found href http://blogs.msdn.com/bclteam at 176
```

```vb
Public Sub Main()
   Dim inputString As String = "My favorite web sites include:</P>" & _
                               "<A HREF=""http://msdn2.microsoft.com"">" & _
                               "MSDN Home Page</A></P>" & _
                               "<A HREF=""http://www.microsoft.com"">" & _
                               "Microsoft Corporation Home Page</A></P>" & _
                               "<A HREF=""http://blogs.msdn.com/bclteam"">" & _
                               ".NET Base Class Library blog</A></P>"
   DumpHRefs(inputString)                     
End Sub
' The example displays the following output:
'       Found href http://msdn2.microsoft.com at 43
'       Found href http://www.microsoft.com at 102
'       Found href http://blogs.msdn.com/bclteam/) at 176
```

O padrão da expressão regular `href\s*=\s*(?:["']&#40;?<1>[^"']*)["']|(?<1>\S+))` é interpretado conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | ----------- 
`href` | Corresponder à cadeia de caracteres literal “href”. A correspondência não diferencia maiúsculas de minúsculas.
`\s*` | Corresponder a zero ou mais caracteres de espaço em branco.
`=` |'Corresponder ao sinal de igual.
`\s*` | Corresponder a zero ou mais caracteres de espaço em branco.
`(?:["']&#40;?<1>[^"']*)"&#124;(?<1>\S+))` | Corresponder a um dos seguintes sem atribuir o resultado a um grupo capturado: aspas simples ou apóstrofe, seguido por zero ou mais ocorrências de qualquer caractere diferente de aspas simples ou apóstrofe, seguido por aspas simples ou apóstrofe. O grupo chamado `1` está incluído nesse padrão. -ou- Um ou mais caracteres diferentes de espaço em branco. O grupo chamado `1` está incluído nesse padrão.
`(?<1>[^"']*)` | Atribuir zero ou mais ocorrências de qualquer caractere diferente de aspas simples ou apóstrofe ao grupo de captura chamado `1`.
`"(?<1>\S+)` | Atribuir um ou mais caracteres diferentes de espaço em branco ao grupo de captura chamado `1`.
 
## <a name="match-result-class"></a>Classe de resultado de correspondência

Os resultados de uma pesquisa são armazenados na classe [Match](xref:System.Text.RegularExpressions.Match), que fornece acesso a todas as subcadeias de caracteres extraídas pela pesquisa. Também lembra a cadeia de caracteres que está sendo pesquisada e a expressão regular que está sendo usada para poder chamar o método [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) para executar outra pesquisa iniciando onde a última terminou.

## <a name="explicitly-named-captures"></a>Capturas nomeadas explicitamente

Em expressões regulares tradicionais, os parênteses de captura são numerados sequencialmente de forma automática. Isso causa dois problemas. Primeiro, se uma expressão regular for modificada pela inserção ou remoção de um conjunto de parênteses, todo o código que se refere às captura numeradas deverá ser reescrito para refletir a nova numeração. Em segundo lugar, como diferentes conjuntos de parênteses geralmente são usados para fornecer duas expressões alternativas para uma correspondência aceitável, pode ser difícil determinar qual das duas expressões realmente retornou um resultado.

Para resolver esses problemas, a classe [Regex](xref:System.Text.RegularExpressions.Regex) dá suporte à sintaxe `(?<name>…)` para capturar uma correspondência em um slot especificado (o slot pode ser nomeado usando uma cadeia de caracteres ou um inteiro; inteiros podem ser recuperados mais rapidamente). Assim, todas as correspondências alternativas para a mesma cadeia de caracteres podem ser direcionadas para o mesmo local. Em caso de conflito, a última correspondência solta em um slot é a correspondência com êxito. (No entanto, está disponível uma lista completa de diversas correspondências para um único slot. Consulte a coleção [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) para obter detalhes.)

## <a name="see-also"></a>Consulte também

[Expressões regulares do .NET](regular-expressions.md)

[Exemplos de expressões regulares](regex-examples.md)




<!--HONumber=Nov16_HO3-->


