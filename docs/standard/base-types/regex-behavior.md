---
title: "Detalhes do comportamento de expressões regulares"
description: "Detalhes do comportamento de expressões regulares"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 6f11047f-45a4-4caf-a259-18abe08cc0d2
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: fa0513a5b450742995bd86fca495ba9904e7361b

---

# <a name="details-of-regular-expression-behavior"></a>Detalhes do comportamento de expressões regulares


O mecanismo de expressões regulares do .NET é um correspondente de expressão regular de retrocesso que incorpora um mecanismo de NFA (Automação Finita Não Determinística) tradicional, como o usado pelo Perl, Python, Emacs e Tcl. Isso o distingue de mecanismos de DFA (Autômato finito determinístico) de expressões regulares puras mais rápidos, porém mais limitados, como os encontrados em awk, egrep ou lex. Também o distingue de NFAs POSIX padronizados, porém mais lentos. A seção a seguir descreve os três tipos de mecanismos de expressões regulares e explica por que as expressões regulares no .NET são implementadas usando um mecanismo de NFA tradicional.

## <a name="benefits-of-the-nfa-engine"></a>Benefícios do mecanismo de NFA

Quando mecanismos de DFA executam a correspondência de padrões, a ordem de processamento é orientada pela cadeia de caracteres de entrada. O mecanismo começa no início da cadeia de caracteres de entrada e continua sequencialmente para determinar se o próximo caractere corresponde ao padrão de expressão regular. Podem assegurar uma correspondência com a cadeia de caracteres mais longa possível. Como nunca testam o mesmo caractere duas vezes, os mecanismos de DFA não dão suporte ao retrocesso. No entanto, como um mecanismo de DFA contém somente o estado finito, não pode corresponder a um padrão com referências inversas; além disso, uma vez que não constrói uma expansão explícita, não pode capturar subexpressões.

Ao contrário de mecanismos de DFA, quando mecanismos de NFA tradicionais executam a correspondência de padrões, a ordem de processamento é orientada pelo padrão de expressão regular. Como processa um elemento de linguagem específico, o mecanismo usa a correspondência Greedy; ou seja, corresponde à maior parte possível da cadeia de caracteres de entrada. Contudo, também consegue salvar seu estado correspondendo a uma subexpressão. Se uma correspondência falhar, o mecanismo poderá retornar para um estado salvo a fim de tentar correspondências adicionais. Esse processo de abandonar uma correspondência de subexpressão bem-sucedida para que elementos de linguagem posteriores na expressão regular também possam corresponder é conhecido como retrocesso. Os mecanismos de NFA usam o retrocesso para testar todas as possíveis expansões de uma expressão regular em uma ordem específica e aceitam a primeira correspondência. Como um mecanismo de NFA tradicional constrói uma expansão específica da expressão regular para uma correspondência de sucesso, pode capturar correspondências de subexpressões e referências inversas correspondentes. Entretanto, como um NFA tradicional retrocede, pode visitar o mesmo estado diversas vezes se chegar no estado por diferentes caminhos. Como resultado, pode executar de modo exponencial lentamente na pior das hipóteses. Já que um mecanismo de NFA tradicional aceita a primeira correspondência que encontra, também pode deixar outras correspondências (possivelmente mais longas) não descobertas.

Os mecanismos de NFA POSIX são como mecanismos de NFA tradicionais, exceto pelo fato de continuarem retrocedendo até poderem assegurar que encontraram a correspondência mais longa possível. Como resultado, um mecanismo de NFA POSIX é mais lento do que um mecanismo de NFA tradicional; quando você usa um mecanismo de NFA POSIX, não pode favorecer uma correspondência menor em detrimento de uma maior alterando a ordem da pesquisa de retrocesso. 

Os mecanismos de NFA tradicionais são favorecidos por programadores porque oferecem maior controle sobre a correspondência da cadeia de caracteres do que mecanismos de DFA ou NFA POSIX. Embora, na pior das hipóteses, possam ser executados mais lentamente, você pode orientá-los para encontrar correspondências em tempo linear ou polinomial usando padrões que reduzem ambiguidades e limitam o retrocesso. Em outras palavras, apesar de os mecanismos de NFA trocarem o desempenho por força e flexibilidade, na maioria dos casos, eles oferecem um desempenho bom ou aceitável se uma expressão regular for bem escrita e evitar casos em que o retrocesso degrada o desempenho exponencialmente.

> [!NOTE]
> Para obter informações sobre a penalidade de desempenho causada por retrocesso excessivo e maneiras de criar uma expressão regular para solucioná-lo, consulte [Retrocesso em expressões regulares](backtracking.md).
 
## <a name="net-framework-engine-capabilities"></a>Recursos do mecanismo do .NET Framework

Para tirar proveito dos benefícios de um mecanismo de NFA tradicional, o mecanismo de expressões regulares do .NET inclui um conjunto completo de constructos para permitir que os programadores conduzam o mecanismo de retrocesso. Tais constructos podem ser usados para encontrar correspondências mais rapidamente ou favorecer expansões específicas em detrimento de outras.

Outros recursos do mecanismo de expressões regulares do .NET incluem o seguinte: 

### <a name="lazy-quantifiers"></a>Quantificadores lentos

Quantificadores lentos: **??**, __*?__, **+?**, **{**_n_**,**_m_**}?**. Esses constructos instruem o mecanismo de retrocesso a pesquisar o número mínimo de repetições primeiro. Por outro lado, quantificadores Greedy comuns tentam corresponder ao número máximo de repetições primeiro. O exemplo a seguir mostra a diferença entre os dois. Uma expressão regular corresponde a uma frase que termina em um número e um grupo de captura deve extrair esse número. A expressão regular `.+(\d+)\.` inclui o quantificador Greedy `.+`, que faz com que o mecanismo de expressões regulares capture o último dígito do número. Por outro lado, a expressão regular `.+?(\d+)\.` inclui o quantificador lento `.+?`, que faz com que o mecanismo de expressões regulares capture o número inteiro.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string greedyPattern = @".+(\d+)\.";
      string lazyPattern = @".+?(\d+)\.";
      string input = "This sentence ends with the number 107325.";
      Match match;

      // Match using greedy quantifier .+.
      match = Regex.Match(input, greedyPattern);
      if (match.Success)
         Console.WriteLine("Number at end of sentence (greedy): {0}", 
                           match.Groups[1].Value);
      else
         Console.WriteLine("{0} finds no match.", greedyPattern);
       // Match using lazy quantifier .+?.
      match = Regex.Match(input, lazyPattern);
      if (match.Success)
         Console.WriteLine("Number at end of sentence (lazy): {0}", 
                           match.Groups[1].Value);
      else
         Console.WriteLine("{0} finds no match.", lazyPattern);
   }
}
// The example displays the following output:
//       Number at end of sentence (greedy): 5
//       Number at end of sentence (lazy): 107325
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim greedyPattern As String = ".+(\d+)\."
      Dim lazyPattern As String = ".+?(\d+)\."
      Dim input As String = "This sentence ends with the number 107325."
      Dim match As Match

      ' Match using greedy quantifier .+.
      match = Regex.Match(input, greedyPattern)
      If match.Success Then
         Console.WriteLine("Number at end of sentence (greedy): {0}", 
                           match.Groups(1).Value)
      Else
         Console.WriteLine("{0} finds no match.", greedyPattern)
      End If

      ' Match using lazy quantifier .+?.
      match = Regex.Match(input, lazyPattern)
      If match.Success Then
         Console.WriteLine("Number at end of sentence (lazy): {0}", 
                           match.Groups(1).Value)
      Else
         Console.WriteLine("{0} finds no match.", lazyPattern)
      End If
   End Sub
End Module
' The example displays the following output:
'       Number at end of sentence (greedy): 5
'       Number at end of sentence (lazy): 107325
```

As versões Greedy e lenta dessa expressão regular são definidas como mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`.+` (quantificador Greedy) | Corresponder a pelo menos uma ocorrência de qualquer caractere. Isso faz com que o mecanismo de expressões regulares corresponda à cadeia de caracteres inteira e, em seguida, retroceda da forma necessária para corresponder ao restante do padrão.
`.+?` (quantificador lento) | Corresponder a pelo menos uma ocorrência de qualquer caractere, mas ao menor número possível.
`(\d+)` | Corresponder a pelo menos um caractere numérico e atribuí-lo ao primeiro grupo de captura.
`\.` | Corresponde a um ponto final.
 
Para obter mais informações sobre quantificadores lentos, consulte [Quantificadores em expressões regulares](quantifiers.md).

### <a name="positive-lookahead"></a>Lookahead positivo

Lookahead positivo: **(?**=_subexpression_**)**. Esse recurso permite que o mecanismo de retrocesso retorne ao mesmo ponto no texto após corresponder a uma subexpressão. É útil para pesquisar em todo o texto verificando vários padrões que iniciam na mesma posição. Também permite que o mecanismo verifique se existe uma subcadeia de caracteres no final da correspondência sem incluir a subcadeia de caracteres no texto correspondente. O exemplo a seguir usa lookahead positivo para extrair as palavras de uma frase que não são seguidas por símbolos de pontuação.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b[A-Z]+\b(?=\P{P})";
      string input = "If so, what comes next?";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       If
//       what
//       comes
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b[A-Z]+\b(?=\P{P})"
      Dim input As String = "If so, what comes next?"
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
         Console.WriteLine(match.Value)
      Next   
   End Sub
End Module
' The example displays the following output:
'       If
'       what
'       comes
```

A expressão regular `\b[A-Z]+\b(?=\P{P})` é definida conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Começar a correspondência em um limite de palavra.
`[A-Z]+` | Corresponder a qualquer caractere alfabético uma ou mais vezes. Uma vez que o método [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) é chamado com a opção [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase), a comparação não diferencia maiúsculas de minúsculas. 
`\b` | Termina a correspondência em um limite de palavra.
`(?=\P{P})` | Antecipe para determinar se o próximo caractere é um símbolo de pontuação. Se não for, a correspondência será bem-sucedida.

Para obter mais informações sobre as asserções de lookahead positivo, consulte [Constructos de agrupamento em expressões regulares](grouping.md).

### <a name="negative-lookahead"></a>Lookahead negativo

Lookahead negativo: **(?!**_subexpression_**)**. Esse recurso adiciona a capacidade de corresponder a uma expressão somente se uma subexpressão não corresponder. Ele é indicado especialmente para refinar uma pesquisa, porque, muitas vezes, é mais simples fornecer uma expressão para um caso que deve ser eliminado do que uma expressão para casos que precisam ser incluídos. Por exemplo, é difícil escrever uma expressão para palavras que não começam com “non”. O exemplo a seguir usa lookahead negativo para excluir.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(?!non)\w+\b";
      string input = "Nonsense is not always non-functional.";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       is
//       not
//       always
//       functional
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(?!non)\w+\b"
      Dim input As String = "Nonsense is not always non-functional."
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       is
'       not
'       always
'       functional
```

O padrão de expressão regular `\b(?!non)\w+\b` é definido conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Começar a correspondência em um limite de palavra.
`(?!non)` | Antecipar para garantir que a cadeia de caracteres atual não comece com “non”. Se isso acontecer, a correspondência falha.
`(\w+)` | Fazer a correspondência a um ou mais caracteres de palavra.
`\b` | Termina a correspondência em um limite de palavra.
 
Para obter mais informações sobre as asserções de lookahead negativo, consulte [Constructos de agrupamento em expressões regulares](grouping.md).

### <a name="conditional-evaluation"></a>Avaliação condicional

Avaliação condicional: **(?(**_expression_**)**_yes_&#124;_no_**)** e**(?(**_name_**)**_yes_&#124;_no_**)**, em que *expression* é uma subexpressão para corresponder, *name* é o nome de um grupo de captura, *yes* é a cadeia de caracteres para corresponder se *expression* for correspondente ou se *name* for um grupo capturado válido não vazio e *no* é a subexpressão para corresponder se *expression* não é correspondente ou se *name* não for um grupo capturado válido não vazio. Esse recurso permite que o mecanismo pesquise usando mais de um padrão alternativo, dependendo do resultado de uma correspondência de subexpressão anterior ou do resultado de uma asserção de largura zero. Isso possibilita uma forma mais potente de referência inversa que permite, por exemplo, corresponder a uma subexpressão com base no fato de uma subexpressão anterior ser correspondente. A expressão regular no exemplo a seguir corresponde a parágrafos que são destinados a uso público e interno. Os parágrafos destinados apenas a uso interno começam com uma marca `<PRIVATE>`. O padrão de expressão regular `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` usa avaliação condicional para atribuir o conteúdo de parágrafos destinados a uso público e interno a grupos de captura separados. Esses parágrafos podem ser tratados de maneiras diferentes.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "<PRIVATE> This is not for public consumption." + Environment.NewLine + 
                     "But this is for public consumption." + Environment.NewLine + 
                     "<PRIVATE> Again, this is confidential.\n";  
      string pattern = @"^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$";
      string publicDocument = null, privateDocument = null;

      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.Multiline))
      {
         if (match.Groups[1].Success) {
            privateDocument += match.Groups[1].Value + "\n";
         }
         else {
            publicDocument += match.Groups[3].Value + "\n";   
            privateDocument += match.Groups[3].Value + "\n";
         }  
      }

      Console.WriteLine("Private Document:");
      Console.WriteLine(privateDocument);
      Console.WriteLine("Public Document:");
      Console.WriteLine(publicDocument);
   }
}
// The example displays the following output:
//    Private Document:
//    This is not for public consumption.
//    But this is for public consumption.
//    Again, this is confidential.
//    
//    Public Document:
//    But this is for public consumption.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "<PRIVATE> This is not for public consumption." + vbCrLf + _
                            "But this is for public consumption." + vbCrLf + _
                            "<PRIVATE> Again, this is confidential." + vbCrLf
      Dim pattern As String = "^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$"
      Dim publicDocument As String = Nothing
      Dim privateDocument As String = Nothing

      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.Multiline)
         If match.Groups(1).Success Then
            privateDocument += match.Groups(1).Value + vbCrLf
         Else
            publicDocument += match.Groups(3).Value + vbCrLf   
            privateDocument += match.Groups(3).Value + vbCrLf
         End If  
      Next

      Console.WriteLine("Private Document:")
      Console.WriteLine(privateDocument)
      Console.WriteLine("Public Document:")
      Console.WriteLine(publicDocument)
   End Sub
End Module
' The example displays the following output:
'    Private Document:
'    This is not for public consumption.
'    But this is for public consumption.
'    Again, this is confidential.
'    
'    Public Document:
'    But this is for public consumption.
```

O padrão de expressão regular é definido como mostra a tabela a seguir.

Padrão | Descrição
------- | -----------
`^` | Começar a correspondência no início de uma linha.
`(?<Pvt>\<PRIVATE\>\s)?` | Corresponder a zero ou uma ocorrência da cadeia de caracteres `<PRIVATE>` seguida para um caractere de espaço em branco. Atribuir a correspondência a um grupo de captura chamado Pvt.
`(?(Pvt)((\w+\p{P}?\s)+)` | Se o grupo de captura `Pvt` existir, corresponder a uma ou mais ocorrências de um ou mais caracteres de palavra seguidos por zero ou um separador de pontuação, seguido por um caractere de espaço em branco. Atribuir a subcadeia de caracteres ao primeiro grupo de captura.
`&#124;((\w+\p{P}?\s)+))` | Se o grupo de captura `Pvt` não existir, corresponder a uma ou mais ocorrências de um ou mais caracteres de palavra seguidos por zero ou um separador de pontuação, seguido por um caractere de espaço em branco. Atribuir a subcadeia de caracteres ao terceiro grupo de captura.
`\r?$` | Corresponder ao final de uma linha ou ao final da cadeia de caracteres.
 
Para obter mais informações sobre a avaliação condicional, consulte [Constructos de alternância em expressões regulares](alternation.md).

### <a name="balancing-group-definitions"></a>Definições de grupo de balanceamento

Equilibrando definições do grupo: **(?<**_name1-name2_**>** _subexpression_**)**. Esse recurso permite que o mecanismo de expressões regulares controle constructos aninhados, como parênteses ou colchetes de abertura e fechamento. Para ver um exemplo, consulte [Constructos de agrupamento em expressões regulares](grouping.md).

### <a name="nonbacktracking-subexpressions"></a>Subexpressões sem retrocesso

Subexpressões sem retrocesso (também conhecidas como subexpressões Greedy): **(?>**_subexpression_**)**. Esse recurso permite que o mecanismo de retrocesso assegure que uma subexpressão corresponda apenas à primeira correspondência encontrada para ela, como se a expressão estivesse sendo executada independentemente da expressão que a contém. Se você não usar esse constructo, as pesquisas de retrocesso de expressões maiores poderão alterar o comportamento de uma subexpressão. Por exemplo, a expressão regular `(a+)\w` corresponde um ou mais caracteres “a”, juntamente com um caractere de palavra que segue a cadeia de caracteres “a”, e atribui a cadeia de caracteres “a” para o primeiro grupo de captura. Contudo, se o caractere final da cadeia de caracteres de entrada também for um “a”, corresponderá ao elemento de linguagem `\w` e não estará incluído no grupo capturado.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "aaaaa", "aaaaab" };
      string backtrackingPattern = @"(a+)\w";
      Match match;

      foreach (string input in inputs) {
         Console.WriteLine("Input: {0}", input);
         match = Regex.Match(input, backtrackingPattern);
         Console.WriteLine("   Pattern: {0}", backtrackingPattern);
         if (match.Success) { 
            Console.WriteLine("      Match: {0}", match.Value);
            Console.WriteLine("      Group 1: {0}", match.Groups[1].Value);
         }
         else {
            Console.WriteLine("      Match failed.");
         }   
      }
      Console.WriteLine();            
   }
}
// The example displays the following output:
//       Input: aaaaa
//          Pattern: (a+)\w
//             Match: aaaaa
//             Group 1: aaaa
//       Input: aaaaab
//          Pattern: (a+)\w
//             Match: aaaaab
//             Group 1: aaaaa
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "aaaaa", "aaaaab" }
      Dim backtrackingPattern As String = "(a+)\w"
      Dim match As Match

      For Each input As String In inputs
         Console.WriteLine("Input: {0}", input)
         match = Regex.Match(input, backtrackingPattern)
         Console.WriteLine("   Pattern: {0}", backtrackingPattern)
         If match.Success Then 
            Console.WriteLine("      Match: {0}", match.Value)
            Console.WriteLine("      Group 1: {0}", match.Groups(1).Value)
         Else 
            Console.WriteLine("      Match failed.")
         End If   
      Next
      Console.WriteLine()            
   End Sub
End Module
' The example displays the following output:
'       Input: aaaaa
'          Pattern: (a+)\w
'             Match: aaaaa
'             Group 1: aaaa
'       Input: aaaaab
'          Pattern: (a+)\w
'             Match: aaaaab
'             Group 1: aaaaa
```

A expressão regular `((?>a+))\w` impede esse comportamento. Como todos os caracteres “a” consecutivos são correspondidos sem retrocesso, o primeiro grupo de captura inclui todos os caracteres “a” consecutivos. Se os caracteres “a” não forem seguidos por pelo menos um caractere diferente de “a”, a correspondência falhará.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "aaaaa", "aaaaab" };
      string nonbacktrackingPattern = @"((?>a+))\w";
      Match match;

      foreach (string input in inputs) {
         Console.WriteLine("Input: {0}", input);
         match = Regex.Match(input, nonbacktrackingPattern);
         Console.WriteLine("   Pattern: {0}", nonbacktrackingPattern);
         if (match.Success) { 
            Console.WriteLine("      Match: {0}", match.Value);
            Console.WriteLine("      Group 1: {0}", match.Groups[1].Value);
         }
         else {
            Console.WriteLine("      Match failed.");
         }   
      }
      Console.WriteLine();            
   }
}
// The example displays the following output:
//       Input: aaaaa
//          Pattern: ((?>a+))\w
//             Match failed.
//       Input: aaaaab
//          Pattern: ((?>a+))\w
//             Match: aaaaab
//             Group 1: aaaaa
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "aaaaa", "aaaaab" }
      Dim nonbacktrackingPattern As String = "((?>a+))\w"
      Dim match As Match

      For Each input As String In inputs
         Console.WriteLine("Input: {0}", input)
         match = Regex.Match(input, nonbacktrackingPattern)
         Console.WriteLine("   Pattern: {0}", nonbacktrackingPattern)
         If match.Success Then 
            Console.WriteLine("      Match: {0}", match.Value)
            Console.WriteLine("      Group 1: {0}", match.Groups(1).Value)
         Else 
            Console.WriteLine("      Match failed.")
         End If   
      Next
      Console.WriteLine()            
   End Sub
End Module
' The example displays the following output:
'       Input: aaaaa
'          Pattern: ((?>a+))\w
'             Match failed.
'       Input: aaaaab
'          Pattern: ((?>a+))\w
'             Match: aaaaab
'             Group 1: aaaaa
```

Para obter mais informações sobre as subexpressões sem retrocesso, consulte [Constructos de agrupamento em expressões regulares](grouping.md).

### <a name="right-to-left-matching"></a>Correspondência da direita para a esquerda

Correspondência da direita para a esquerda, que é especificada fornecendo a opção [RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft) para um construtor de classe [Regex](xref:System.Text.RegularExpressions.Regex) ou um método de correspondência de instância estática. Esse recurso é útil durante a pesquisa da direita para a esquerda em vez da esquerda para direita ou nos casos em que é mais eficiente iniciar uma correspondência na parte direita do padrão em vez de à esquerda. Como mostra o exemplo a seguir, o uso da correspondência da direita para esquerda pode alterar o comportamento de quantificadores Greedy. O exemplo realiza duas pesquisas por uma frase que termina em número. A pesquisa da esquerda para a direita que usa o quantificador Greedy `+` corresponde a um dos seis dígitos na frase, enquanto a pesquisa da direita para a esquerda corresponde a todos os seis dígitos. Para obter uma descrição do padrão de expressão regular, consulte o exemplo que mostra quantificadores lentos no início desta seção.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string greedyPattern = @".+(\d+)\.";
      string input = "This sentence ends with the number 107325.";
      Match match;

      // Match from left-to-right using lazy quantifier .+?.
      match = Regex.Match(input, greedyPattern);
      if (match.Success)
         Console.WriteLine("Number at end of sentence (left-to-right): {0}", 
                           match.Groups[1].Value);
      else
         Console.WriteLine("{0} finds no match.", greedyPattern);

      // Match from right-to-left using greedy quantifier .+.
      match = Regex.Match(input, greedyPattern, RegexOptions.RightToLeft);
      if (match.Success)
         Console.WriteLine("Number at end of sentence (right-to-left): {0}", 
                           match.Groups[1].Value);
      else
         Console.WriteLine("{0} finds no match.", greedyPattern);
   }
}
// The example displays the following output:
//       Number at end of sentence (left-to-right): 5
//       Number at end of sentence (right-to-left): 107325
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim greedyPattern As String = ".+(\d+)\."
      Dim input As String = "This sentence ends with the number 107325."
      Dim match As Match

      ' Match from left-to-right using lazy quantifier .+?.
      match = Regex.Match(input, greedyPattern)
      If match.Success Then
         Console.WriteLine("Number at end of sentence (left-to-right): {0}", 
                           match.Groups(1).Value)
      Else
         Console.WriteLine("{0} finds no match.", greedyPattern)
      End If

      ' Match from right-to-left using greedy quantifier .+.
      match = Regex.Match(input, greedyPattern, RegexOptions.RightToLeft)
      If match.Success Then
         Console.WriteLine("Number at end of sentence (right-to-left): {0}", 
                           match.Groups(1).Value)
      Else
         Console.WriteLine("{0} finds no match.", greedyPattern)
      End If
   End Sub
End Module
' The example displays the following output:
'       Number at end of sentence (left-to-right): 5
'       Number at end of sentence (right-to-left): 107325
```

Para obter mais informações sobre a correspondência da direita para a esquerda, consulte [Opções de expressões regulares](options.md).

### <a name="positive-and-negative-lookbehind"></a>Lookbehind positivo e negativo

Lookbehind positivo e negativo: **(?<**=_subexpression_**)** para lookbehind positivo e **(?<!**_subexpression_**)** para lookbehind negativo. Esse recurso é semelhante ao lookahead, que é discutido neste tópico. Como o mecanismo de expressões regulares possibilita uma correspondência completa da direita para a esquerda, expressões regulares permitem lookbehinds irrestritos. O lookbehind positivo e negativo também pode ser usado para evitar o aninhamento de quantificadores quando a subexpressão aninhada é um superconjunto de uma expressão externa. Expressões regulares com tais quantificadores aninhados geralmente oferecem um desempenho ruim. Por exemplo, o exemplo a seguir verifica se uma cadeia de caracteres começa e termina com um caractere alfanumérico e se qualquer outro caractere na cadeia de caracteres faz parte de um subconjunto maior. Faz parte da expressão regular usada para validar endereços de email. Para obter mais informações, consulte [Como verificar se cadeias de caracteres estão em um formato de email válido](verify-format.md).

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "jack.sprat", "dog#", "dog#1", "me.myself", 
                          "me.myself!" };
      string pattern = @"^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$";
      foreach (string input in inputs) {
         if (Regex.IsMatch(input, pattern, RegexOptions.IgnoreCase))
            Console.WriteLine("{0}: Valid", input);
         else
            Console.WriteLine("{0}: Invalid", input);
      }
   }
}
// The example displays the following output:
//       jack.sprat: Valid
//       dog#: Invalid
//       dog#1: Valid
//       me.myself: Valid
//       me.myself!: Invalid
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "jack.sprat", "dog#", "dog#1", "me.myself", 
                                 "me.myself!" }
      Dim pattern As String = "^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$"
      For Each input As String In inputs
         If Regex.IsMatch(input, pattern, RegexOptions.IgnoreCase) Then
            Console.WriteLine("{0}: Valid", input)
         Else
            Console.WriteLine("{0}: Invalid", input)
         End If   
      Next
   End Sub
End Module
' The example displays the following output:
'       jack.sprat: Valid
'       dog#: Invalid
'       dog#1: Valid
'       me.myself: Valid
'       me.myself!: Invalid
```

A expressão regular `^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$` é definida conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | ----------- 
`^` | Começar a correspondência no início da cadeia de caracteres.
`[A-Z0-9]` | Corresponder a qualquer caractere numérico ou alfanumérico. (A comparação não diferencia maiúsculas de minúsculas.)
`([-!#$%&'.*+/=?^`{}&#124;~\w])*` | Corresponder a zero ou mais ocorrências de qualquer caractere de palavra ou qualquer um destes caracteres: -, !, #, $, %, &, ', ., *, +, /, =, ?, ^, `, {, }, &#124; ou ~.
`(?<=[A-Z0-9])` | Olhar para o caractere anterior, que precisa ser numérico ou alfanumérico. (A comparação não diferencia maiúsculas de minúsculas.)
`$` | Encerrar a correspondência ao final da cadeia de caracteres.
 
Para obter mais informações sobre lookbehind positivo e negativo, consulte [Constructos de agrupamento em expressões regulares](grouping.md).


## <a name="related-topics"></a>Tópicos relacionados

Título | Descrição
----- | ----------- 
[Retrocesso](backtracking.md) | Fornece informações sobre como o retrocesso de expressões regulares se ramifica para encontrar correspondências alternativas.
[Compilação e reutilização](compilation.md) | Fornece informações sobre a compilação e a reutilização de expressões regulares para aumentar o desempenho.
[Acesso thread-safe](thread-safety.md) | Fornece informações sobre a segurança de thread de expressões regulares e explica quando você deve sincronizar o acesso a objetos de expressão regular.
[Expressões regulares do .NET](regular-expressions.md) | Fornece uma visão geral sobre o aspecto de linguagem de programação das expressões regulares.
[O Modelo de Objeto de expressão regular](object-model.md) | Oferece informações e exemplos de código que mostram como usar as classes de expressão regular.
[Exemplos de expressões regulares](regex-examples.md) | Contém exemplos de código que mostram o uso de expressões regulares em aplicativos comuns.
[Linguagem de expressão regular – referência rápida](quick-ref.md) | Oferece informações a respeito do conjunto de caracteres, operadores e constructos que você pode usar para definir expressões regulares.
 
## <a name="reference"></a>Referência

[System.Text.RegularExpressions](xref:System.Text.RegularExpressions)




<!--HONumber=Dec16_HO1-->


