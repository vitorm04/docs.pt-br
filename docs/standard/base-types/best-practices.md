---
title: "Práticas recomendadas para expressões regulares"
description: "Práticas recomendadas para expressões regulares"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 096fd614-91bf-4296-be24-12f62b062294
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: d92549bf46f1c7a728bc6e2ac7cb183251115084

---

# <a name="best-practices-for-regular-expressions"></a>Práticas recomendadas para expressões regulares

O mecanismo de expressões regulares no .NET é uma ferramenta poderosa e repleta de recursos que processa o texto com base em correspondências de padrões em vez de em comparar e corresponder o texto literal. Na maioria dos casos, ele realiza a correspondência de padrões de forma rápida e eficiente. No entanto, em alguns casos, o mecanismo de expressões regulares pode parecer ser muito lento. Em casos extremos, pode até mesmo parecer parar de responder enquanto processa uma entrada relativamente pequena em um período de horas ou até mesmo dias. 

Este tópico descreve algumas das práticas recomendadas que os desenvolvedores podem adotar para garantir que as expressões regulares obtenham o máximo de desempenho. Ele contém as seguintes seções:

* [Considere a fonte de entrada](#consider-the-input-source)

* [Trate a instanciação de objetos adequadamente](#handle-object-instantiation-appropriately)

* [Tome conta do retrocesso](#take-charge-of-backtracking)

* [Use valores de tempo limite](#use-time-out-values)

* [Capture somente quando necessário](#capture-only-when-necessary)

* [Tópicos relacionados](#related-topics)

## <a name="consider-the-input-source"></a>Considere a fonte de entrada

Em geral, as expressões regulares podem aceitar dois tipos de entrada: restrita e não restrita. Uma entrada restrita é o texto proveniente de uma fonte conhecida ou confiável e segue um formato predefinido. Uma entrada irrestrita é um texto que se origina de uma origem não confiável como um usuário não confiável e não pode seguir um formato predefinido ou esperado.

Os padrões de expressões regulares geralmente são escritos para corresponder a entradas válidas. Ou seja, os desenvolvedores examinam o texto que desejam corresponder e escrevem um padrão de expressão regular que corresponde a ele. Os desenvolvedores então determinam se esse padrão requer correção ou uma elaboração adicional testando-o com vários itens de entrada válidos. Quando o padrão corresponde a todas as entradas válidas presumidas, é declarado como pronto para produção e pode ser incluído em um aplicativo final. Isso torna um padrão de expressão regular apropriado para corresponder uma entrada restrita. No entanto, ele não o torna adequado para corresponder à entrada sem restrição.

Para corresponder a uma entrada sem restrição, uma expressão regular deve ser capaz de manipular três tipos de texto:

• Texto que corresponda ao padrão da expressão regular.

• Texto que não corresponda ao padrão da expressão regular.

• Texto que quase corresponda ao padrão da expressão regular.

O último tipo de texto é particularmente problemático para uma expressão regular que foi escrita para lidar com entradas restritas. Se essa expressão regular também depender de [retrocesso](backtracking.md) abrangente, o mecanismo de expressões regulares poderá gastar um período fora do normal (em alguns casos, muitas horas ou dias) processando texto aparentemente inócuo. 

> [!WARNING]
> O exemplo a seguir usa uma expressão regular que é propensa a retrocesso excessivo e que pode rejeitar endereços de email válidos. Você não deve usá-lo em uma rotina de validação de email. Se você desejar uma expressão regular que valida endereços de email, confira [Como verificar se cadeias de caracteres estão em um formato de email válido](verify-format.md). 


Por exemplo, considere uma expressão regular muito usada, mas extremamente problemática, para validar o alias de um endereço de email. A expressão regular `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` é escrita para processar o que é considerado um endereço de email válido, o que consiste em um caractere alfanumérico seguido por zero ou mais caracteres que podem ser alfanuméricos, pontos ou hifens. A expressão regular deve terminar com um caractere alfanumérico. No entanto, como mostra o exemplo a seguir, embora esta expressão regular manipule entradas válidas facilmente, seu desempenho é muito ineficiente ao processar uma entrada quase válida.

```csharp
using System;
using System.Diagnostics;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      Stopwatch sw;    
      string[] addresses = { "AAAAAAAAAAA@contoso.com", 
                             "AAAAAAAAAAaaaaaaaaaa!@contoso.com" };
      // The following regular expression should not actually be used to 
      // validate an email address.
      string pattern = @"^[0-9A-Z]([-.\w]*[0-9A-Z])*$";
      string input; 

      foreach (var address in addresses) {
         string mailBox = address.Substring(0, address.IndexOf("@"));       
         int index = 0;
         for (int ctr = mailBox.Length - 1; ctr >= 0; ctr--) {
            index++;

            input = mailBox.Substring(ctr, index); 
            sw = Stopwatch.StartNew();
            Match m = Regex.Match(input, pattern, RegexOptions.IgnoreCase);
            sw.Stop();
            if (m.Success)
               Console.WriteLine("{0,2}. Matched '{1,25}' in {2}", 
                                 index, m.Value, sw.Elapsed);
            else                     
               Console.WriteLine("{0,2}. Failed  '{1,25}' in {2}", 
                                 index, input, sw.Elapsed);
         }
         Console.WriteLine();
      }
   }
}

// The example displays output similar to the following:
//     1. Matched '                        A' in 00:00:00.0007122
//     2. Matched '                       AA' in 00:00:00.0000282
//     3. Matched '                      AAA' in 00:00:00.0000042
//     4. Matched '                     AAAA' in 00:00:00.0000038
//     5. Matched '                    AAAAA' in 00:00:00.0000042
//     6. Matched '                   AAAAAA' in 00:00:00.0000042
//     7. Matched '                  AAAAAAA' in 00:00:00.0000042
//     8. Matched '                 AAAAAAAA' in 00:00:00.0000087
//     9. Matched '                AAAAAAAAA' in 00:00:00.0000045
//    10. Matched '               AAAAAAAAAA' in 00:00:00.0000045
//    11. Matched '              AAAAAAAAAAA' in 00:00:00.0000045
//    
//     1. Failed  '                        !' in 00:00:00.0000447
//     2. Failed  '                       a!' in 00:00:00.0000071
//     3. Failed  '                      aa!' in 00:00:00.0000071
//     4. Failed  '                     aaa!' in 00:00:00.0000061
//     5. Failed  '                    aaaa!' in 00:00:00.0000081
//     6. Failed  '                   aaaaa!' in 00:00:00.0000126
//     7. Failed  '                  aaaaaa!' in 00:00:00.0000359
//     8. Failed  '                 aaaaaaa!' in 00:00:00.0000414
//     9. Failed  '                aaaaaaaa!' in 00:00:00.0000758
//    10. Failed  '               aaaaaaaaa!' in 00:00:00.0001462
//    11. Failed  '              aaaaaaaaaa!' in 00:00:00.0002885
//    12. Failed  '             Aaaaaaaaaaa!' in 00:00:00.0005780
//    13. Failed  '            AAaaaaaaaaaa!' in 00:00:00.0011628
//    14. Failed  '           AAAaaaaaaaaaa!' in 00:00:00.0022851
//    15. Failed  '          AAAAaaaaaaaaaa!' in 00:00:00.0045864
//    16. Failed  '         AAAAAaaaaaaaaaa!' in 00:00:00.0093168
//    17. Failed  '        AAAAAAaaaaaaaaaa!' in 00:00:00.0185993
//    18. Failed  '       AAAAAAAaaaaaaaaaa!' in 00:00:00.0366723
//    19. Failed  '      AAAAAAAAaaaaaaaaaa!' in 00:00:00.1370108
//    20. Failed  '     AAAAAAAAAaaaaaaaaaa!' in 00:00:00.1553966
//    21. Failed  '    AAAAAAAAAAaaaaaaaaaa!' in 00:00:00.3223372
```

```vb
Imports System.Diagnostics
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim sw As Stopwatch    
      Dim addresses() As String = { "AAAAAAAAAAA@contoso.com", 
                                 "AAAAAAAAAAaaaaaaaaaa!@contoso.com" }
      ' The following regular expression should not actually be used to 
      ' validate an email address.
      Dim pattern As String = "^[0-9A-Z]([-.\w]*[0-9A-Z])*$"
      Dim input As String 

      For Each address In addresses
         Dim mailBox As String = address.Substring(0, address.IndexOf("@"))       
         Dim index As Integer = 0
         For ctr As Integer = mailBox.Length - 1 To 0 Step -1
            index += 1
            input = mailBox.Substring(ctr, index) 
            sw = Stopwatch.StartNew()
            Dim m As Match = Regex.Match(input, pattern, RegexOptions.IgnoreCase)
            sw.Stop()
            if m.Success Then
               Console.WriteLine("{0,2}. Matched '{1,25}' in {2}", 
                                 index, m.Value, sw.Elapsed)
            Else                     
               Console.WriteLine("{0,2}. Failed  '{1,25}' in {2}", 
                                 index, input, sw.Elapsed)
            End If                  
         Next
         Console.WriteLine()
      Next
   End Sub
End Module
' The example displays output similar to the following:
'     1. Matched '                        A' in 00:00:00.0007122
'     2. Matched '                       AA' in 00:00:00.0000282
'     3. Matched '                      AAA' in 00:00:00.0000042
'     4. Matched '                     AAAA' in 00:00:00.0000038
'     5. Matched '                    AAAAA' in 00:00:00.0000042
'     6. Matched '                   AAAAAA' in 00:00:00.0000042
'     7. Matched '                  AAAAAAA' in 00:00:00.0000042
'     8. Matched '                 AAAAAAAA' in 00:00:00.0000087
'     9. Matched '                AAAAAAAAA' in 00:00:00.0000045
'    10. Matched '               AAAAAAAAAA' in 00:00:00.0000045
'    11. Matched '              AAAAAAAAAAA' in 00:00:00.0000045
'    
'     1. Failed  '                        !' in 00:00:00.0000447
'     2. Failed  '                       a!' in 00:00:00.0000071
'     3. Failed  '                      aa!' in 00:00:00.0000071
'     4. Failed  '                     aaa!' in 00:00:00.0000061
'     5. Failed  '                    aaaa!' in 00:00:00.0000081
'     6. Failed  '                   aaaaa!' in 00:00:00.0000126
'     7. Failed  '                  aaaaaa!' in 00:00:00.0000359
'     8. Failed  '                 aaaaaaa!' in 00:00:00.0000414
'     9. Failed  '                aaaaaaaa!' in 00:00:00.0000758
'    10. Failed  '               aaaaaaaaa!' in 00:00:00.0001462
'    11. Failed  '              aaaaaaaaaa!' in 00:00:00.0002885
'    12. Failed  '             Aaaaaaaaaaa!' in 00:00:00.0005780
'    13. Failed  '            AAaaaaaaaaaa!' in 00:00:00.0011628
'    14. Failed  '           AAAaaaaaaaaaa!' in 00:00:00.0022851
'    15. Failed  '          AAAAaaaaaaaaaa!' in 00:00:00.0045864
'    16. Failed  '         AAAAAaaaaaaaaaa!' in 00:00:00.0093168
'    17. Failed  '        AAAAAAaaaaaaaaaa!' in 00:00:00.0185993
'    18. Failed  '       AAAAAAAaaaaaaaaaa!' in 00:00:00.0366723
'    19. Failed  '      AAAAAAAAaaaaaaaaaa!' in 00:00:00.1370108
'    20. Failed  '     AAAAAAAAAaaaaaaaaaa!' in 00:00:00.1553966
'    21. Failed  '    AAAAAAAAAAaaaaaaaaaa!' in 00:00:00.3223372
```

Conforme mostrado pela saída do exemplo, o mecanismo de expressões regulares processa o alias de email válido quase no mesmo tempo, independentemente do seu comprimento. Por outro lado, quando o endereço de email quase válido tem mais de cinco caracteres, o tempo de processamento chega a dobrar para cada caractere adicional na cadeia de caracteres. Isso significa que uma cadeia de 28 caracteres quase válidos levaria mais de uma hora para ser processada e uma cadeia de 33 caracteres quase válidos demoraria quase um dia. 

Como essa expressão regular foi desenvolvida considerando apenas a correspondência com o formato da entrada, ela não leva em consideração entradas que não correspondem ao padrão. Isso, por sua vez, pode permitir que entradas não restritas quase correspondentes ao padrão da expressão regular prejudiquem significativamente o desempenho.

Para resolver este problema, você pode fazer o seguinte:

* Ao desenvolver um padrão, você deve considerar como o retrocesso pode afetar o desempenho do mecanismo de expressões regulares, especialmente se a expressão regular for criada para processar entradas sem restrição. Para obter mais informações, consulte a seção [Tome conta do retrocesso](#take-charge-of-backtracking).

* Teste rigorosamente sua expressão regular usando entradas inválidas e quase válidas, bem como entradas válidas. Para gerar entradas para uma expressão regular específica aleatoriamente, você pode usar [Rex](http://research.microsoft.com/en-us/projects/rex/), que é uma ferramenta de exploração de expressões regulares da Microsoft Research.

## <a name="handle-object-instantiation-appropriately"></a>Trate a instanciação de objetos adequadamente

No centro do modelo de objeto de expressões regulares do .NET está a classe [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex), que representa o mecanismo de expressões regulares. Muitas vezes, o maior fator individual que afeta o desempenho das expressões regulares é a forma como o mecanismo [Regex](xref:System.Text.RegularExpressions.Regex) é usado. Definir uma expressão regular envolve o acoplamento vigoroso do mecanismo de expressões regulares com um padrão de expressão regular. Esse processo de acoplamento, seja envolvendo a instanciação de um objeto [Regex](xref:System.Text.RegularExpressions.Regex) ao passar para seu construtor um padrão de expressão regular ou seja chamando um método estático ao passar o padrão de expressão regular com a cadeia de caracteres a ser analisada, é necessariamente caro.

É possível acoplar o mecanismo de expressões regulares com um padrão específico de expressão regular e usar o mecanismo para fazer a correspondência com texto de várias maneiras:

* Você pode chamar um método estático de correspondência de padrões, como [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String)). Isso não requer a instanciação de um objeto de expressão regular.

* É possível criar uma instância de um objeto [Regex](xref:System.Text.RegularExpressions.Regex) e chamar um método de instância de correspondência de padrões de uma expressão regular interpretada. Esse é o método padrão para associar o mecanismo de expressões regulares a uma expressão regular padrão. Isso ocorre quando um objeto [Regex](xref:System.Text.RegularExpressions.Regex) é instanciado sem um argumento de opções que inclui o sinalizador [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled).

* Você pode criar uma instância de um objeto [Regex](xref:System.Text.RegularExpressions.Regex) e chamar um método de instância de correspondência de padrões de uma expressão regular compilada. Os objetos de expressão regular representam padrões compilados quando um objeto [Regex](xref:System.Text.RegularExpressions.Regex) é instanciado com um argumento de opções que inclui o sinalizador [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled).

> [!IMPORTANT]
> A forma da chamada de método (estático, interpretada, compilada) afeta o desempenho se a mesma expressão regular é usada repetidamente em chamadas de método ou se um aplicativo faz uso extensivo de objetos de expressão regular.
 
### <a name="static-regular-expressions"></a>Expressões regulares estáticas

Os métodos de expressões regulares estáticas são recomendados como uma alternativa a criar repetidamente instâncias de um objeto de expressão regular com a mesma expressão regular. Ao contrário de padrões de expressões regulares usados por objetos de expressões regulares, os códigos de operação ou a linguagem intermediária compilada da Microsoft (MSIL) de padrões usados em chamadas de métodos são armazenados em cache internamente pelo mecanismo de expressões regulares. 

Por exemplo, você pode chamar um método para validar a entrada do usuário. Neste exemplo, um método chamado `IsValidCurrency` verifica se o usuário inseriu um símbolo de moeda seguido por pelo menos um dígito decimal. Uma implementação bem ineficiente do método `IsValidCurrency` é mostrada no exemplo a seguir. Observe que cada chamada de método reinstancia um objeto [Regex](xref:System.Text.RegularExpressions.Regex) com o mesmo padrão. Isso, por sua vez, significa que o padrão de expressão regular deve ser recompilado toda vez que o método é chamado.

```csharp
using System;
using System.Text.RegularExpressions;

public class RegexLib
{
   public static bool IsValidCurrency(string currencyValue)
   {
      string pattern = @"\p{Sc}+\s*\d+";
      Regex currencyRegex = new Regex(pattern);
      return currencyRegex.IsMatch(currencyValue);
   }
}
```

```vb
Public Sub OKButton_Click(sender As Object, e As EventArgs) _ 
           Handles OKButton.Click

   If Not String.IsNullOrEmpty(sourceCurrency.Text) Then
      If RegexLib.IsValidCurrency(sourceCurrency.Text) Then
         PerformConversion()
      Else
         status.Text = "The source currency value is invalid."
      End If          
   End If
End Sub
```

Você deve substituir esse código ineficiente por uma chamada ao método estático [Regex.IsMatch(String, String)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String)). Isso elimina a necessidade de criar uma instância de um objeto [Regex](xref:System.Text.RegularExpressions.Regex) toda vez que você desejar chamar um método de correspondência de padrões e permite que o mecanismo de expressões regulares recupere uma versão compilada da expressão regular do cache.

```csharp
using System;
using System.Text.RegularExpressions;

public class RegexLib
{
   public static bool IsValidCurrency(string currencyValue)
   {
      string pattern = @"\p{Sc}+\s*\d+";
      return Regex.IsMatch(currencyValue, pattern); 
   }
}
```

```vb
Imports System.Text.RegularExpressions

Public Module RegexLib
   Public Function IsValidCurrency(currencyValue As String) As Boolean
      Dim pattern As String = "\p{Sc}+\s*\d+"
      Return Regex.IsMatch(currencyValue, pattern)
   End Function
End Module
```

Por padrão, os 15 padrões de expressões regulares estáticas usados mais recentemente são armazenados no cache. Para aplicativos que requerem um número maior de expressões regulares estáticas armazenadas no cache, o tamanho do cache pode ser ajustado com a definição da propriedade [Regex.CacheSize](xref:System.Text.RegularExpressions.Regex.CacheSize).

A expressão regular `\p{Sc}+\s*\d+` que é usada neste exemplo verifica que a cadeia de caracteres de entrada consiste em um símbolo de moeda e pelo menos um dígito decimal. O padrão é definido conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\p{Sc}+` | Corresponde a um ou mais caracteres no símbolo Unicode, categoria de moeda.
`\s*` | Corresponder a zero ou mais caracteres de espaço em branco.
`\d+` | Corresponde a um ou mais dígitos decimais.
 
### <a name="interpreted-vs-compiled-regular-expressions"></a>Expressões regulares compiladas vs. interpretadas

Os padrões de expressões regulares que não são associados ao mecanismo de expressões regulares com a especificação da opção [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) são interpretados. Quando um objeto de expressão regular é instanciado, o mecanismo de expressões regulares converte a expressão regular em um conjunto de códigos de operação. Quando um método de instância é chamado, os códigos de operação são convertidos para MSIL e executados pelo compilador JIT. Da mesma forma, quando um método estático de expressão regular é chamado e a expressão regular não pode ser encontrada no cache, o mecanismo de expressão regular converte a expressão regular em um conjunto de códigos operacionais e os armazena no cache. Em seguida, converte esses códigos de operação para MSIL de modo que o compilador JIT possa executá-los. As expressões regulares interpretadas reduzem o tempo de inicialização ao custo de um tempo de execução mais lento. Devido a isso, eles são melhores utilizados quando a expressão regular é usada em um pequeno número de chamadas de método ou se o número exato de chamadas para métodos de expressão regular é desconhecido, mas com a expectativa de ser pequeno. À medida que número de chamadas de método aumenta, o ganho de desempenho do tempo de inicialização reduzido é superado pela velocidade de execução mais lenta.

Os padrões de expressões regulares que são associados ao mecanismo de expressões regulares com a especificação da opção [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) são compilados. Isso significa que, quando um objeto de expressão regular é instanciado ou quando um método de expressão regular estática é chamado e a expressão regular não pode ser encontrada no cache, o mecanismo de expressões regulares converte a expressão regular para um conjunto intermediário de códigos de operação, que em seguida é convertido para MSIL. Quando um método é chamado, o compilador JIT executa o MSIL. Em contraste com as expressões regulares interpretadas, as expressões regulares compiladas aumentam o tempo de inicialização, mas executam os métodos individuais de correspondência padrão de forma mais rápida. Como resultado, o benefício de desempenho que resulta da compilação da expressão regular aumenta em proporção ao número de métodos de expressões regulares chamados.

Para resumir, recomendamos que você use expressões regulares interpretadas ao chamar métodos de expressões regulares com uma expressão regular específica com relativa pouca frequência. Você deve usar expressões regulares compiladas ao chamar os métodos de expressões regulares com uma expressão regular específica com uma relativa frequência. É difícil determinar o limite exato em que as velocidades de execução mais lentas das expressões regulares interpretadas suplantam os ganhos proporcionados pelo tempo de inicialização reduzido ou o limite em que os tempos de inicialização mais lentos das expressões regulares compiladas suplantam os ganhos gerados por suas velocidades de execução mais rápida. O limite depende de vários fatores, incluindo a complexidade da expressão regular e dos dados específicos que são processados. Para determinar se as expressões regulares interpretadas ou compiladas oferecem o melhor desempenho para seu cenário de aplicativo específico, você pode usar a classe [Stopwatch](xref:System.Diagnostics.Stopwatch) para comparar seus tempos de execução.

O exemplo a seguir compara o desempenho de expressões regulares compiladas e interpretadas ao ler as dez primeiras frases e ao ler todas as frases no texto The Financier de Theodore Dreiser. Conforme mostrado pela saída do exemplo, quando apenas dez chamadas são feitas para os métodos correspondentes de expressão regular, uma expressão regular interpretada oferece um desempenho melhor do que uma expressão regular compilada. No entanto, uma expressão regular compilada oferece melhor desempenho quando um grande número de chamadas (neste caso, mais 13.000) é feito. 

```csharp
using System;
using System.Diagnostics;
using System.IO;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]";
      Stopwatch sw;
      Match match;
      int ctr;

      StreamReader inFile = new StreamReader(@".\Dreiser_TheFinancier.txt");
      string input = inFile.ReadToEnd();
      inFile.Close();

      // Read first ten sentences with interpreted regex.
      Console.WriteLine("10 Sentences with Interpreted Regex:");
      sw = Stopwatch.StartNew();
      Regex int10 = new Regex(pattern, RegexOptions.Singleline);
      match = int10.Match(input);
      for (ctr = 0; ctr <= 9; ctr++) {
         if (match.Success)
            // Do nothing with the match except get the next match.
            match = match.NextMatch();
         else
            break;
      }
      sw.Stop();
      Console.WriteLine("   {0} matches in {1}", ctr, sw.Elapsed);

      // Read first ten sentences with compiled regex.
      Console.WriteLine("10 Sentences with Compiled Regex:");
      sw = Stopwatch.StartNew();
      Regex comp10 = new Regex(pattern, 
                   RegexOptions.Singleline | RegexOptions.Compiled);
      match = comp10.Match(input);
      for (ctr = 0; ctr <= 9; ctr++) {
         if (match.Success)
            // Do nothing with the match except get the next match.
            match = match.NextMatch();
         else
            break;
      }
      sw.Stop();
      Console.WriteLine("   {0} matches in {1}", ctr, sw.Elapsed);

      // Read all sentences with interpreted regex.
      Console.WriteLine("All Sentences with Interpreted Regex:");
      sw = Stopwatch.StartNew();
      Regex intAll = new Regex(pattern, RegexOptions.Singleline);
      match = intAll.Match(input);
      int matches = 0;
      while (match.Success) {
         matches++;
         // Do nothing with the match except get the next match.
         match = match.NextMatch();
      }
      sw.Stop();
      Console.WriteLine("   {0:N0} matches in {1}", matches, sw.Elapsed);

      // Read all sentnces with compiled regex.
      Console.WriteLine("All Sentences with Compiled Regex:");
      sw = Stopwatch.StartNew();
      Regex compAll = new Regex(pattern, 
                      RegexOptions.Singleline | RegexOptions.Compiled);
      match = compAll.Match(input);
      matches = 0;
      while (match.Success) {
         matches++;
         // Do nothing with the match except get the next match.
         match = match.NextMatch();
      }
      sw.Stop();
      Console.WriteLine("   {0:N0} matches in {1}", matches, sw.Elapsed);      
   }
}
// The example displays the following output:
//       10 Sentences with Interpreted Regex:
//          10 matches in 00:00:00.0047491
//       10 Sentences with Compiled Regex:
//          10 matches in 00:00:00.0141872
//       All Sentences with Interpreted Regex:
//          13,443 matches in 00:00:01.1929928
//       All Sentences with Compiled Regex:
//          13,443 matches in 00:00:00.7635869
//       
//       >compare1
//       10 Sentences with Interpreted Regex:
//          10 matches in 00:00:00.0046914
//       10 Sentences with Compiled Regex:
//          10 matches in 00:00:00.0143727
//       All Sentences with Interpreted Regex:
//          13,443 matches in 00:00:01.1514100
//       All Sentences with Compiled Regex:
//          13,443 matches in 00:00:00.7432921
```

```vb
Imports System.Diagnostics
Imports System.IO
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]"
      Dim sw As Stopwatch
      Dim match As Match
      Dim ctr As Integer

      Dim inFile As New StreamReader(".\Dreiser_TheFinancier.txt")
      Dim input As String = inFile.ReadToEnd()
      inFile.Close()

      ' Read first ten sentences with interpreted regex.
      Console.WriteLine("10 Sentences with Interpreted Regex:")
      sw = Stopwatch.StartNew()
      Dim int10 As New Regex(pattern, RegexOptions.SingleLine)
      match = int10.Match(input)
      For ctr = 0 To 9
         If match.Success Then
            ' Do nothing with the match except get the next match.
            match = match.NextMatch()
         Else
            Exit For
         End If
      Next
      sw.Stop()
      Console.WriteLine("   {0} matches in {1}", ctr, sw.Elapsed)

      ' Read first ten sentences with compiled regex.
      Console.WriteLine("10 Sentences with Compiled Regex:")
      sw = Stopwatch.StartNew()
      Dim comp10 As New Regex(pattern, 
                   RegexOptions.SingleLine Or RegexOptions.Compiled)
      match = comp10.Match(input)
      For ctr = 0 To 9
         If match.Success Then
            ' Do nothing with the match except get the next match.
            match = match.NextMatch()
         Else
            Exit For
         End If
      Next
      sw.Stop()
      Console.WriteLine("   {0} matches in {1}", ctr, sw.Elapsed)

      ' Read all sentences with interpreted regex.
      Console.WriteLine("All Sentences with Interpreted Regex:")
      sw = Stopwatch.StartNew()
      Dim intAll As New Regex(pattern, RegexOptions.SingleLine)
      match = intAll.Match(input)
      Dim matches As Integer = 0
      Do While match.Success
         matches += 1
         ' Do nothing with the match except get the next match.
         match = match.NextMatch()
      Loop
      sw.Stop()
      Console.WriteLine("   {0:N0} matches in {1}", matches, sw.Elapsed)

      ' Read all sentnces with compiled regex.
      Console.WriteLine("All Sentences with Compiled Regex:")
      sw = Stopwatch.StartNew()
      Dim compAll As New Regex(pattern, 
                     RegexOptions.SingleLine Or RegexOptions.Compiled)
      match = compAll.Match(input)
      matches = 0
      Do While match.Success
         matches += 1
         ' Do nothing with the match except get the next match.
         match = match.NextMatch()
      Loop
      sw.Stop()
      Console.WriteLine("   {0:N0} matches in {1}", matches, sw.Elapsed)      
   End Sub
End Module
' The example displays output like the following:
'       10 Sentences with Interpreted Regex:
'          10 matches in 00:00:00.0047491
'       10 Sentences with Compiled Regex:
'          10 matches in 00:00:00.0141872
'       All Sentences with Interpreted Regex:
'          13,443 matches in 00:00:01.1929928
'       All Sentences with Compiled Regex:
'          13,443 matches in 00:00:00.7635869
'       
'       >compare1
'       10 Sentences with Interpreted Regex:
'          10 matches in 00:00:00.0046914
'       10 Sentences with Compiled Regex:
'          10 matches in 00:00:00.0143727
'       All Sentences with Interpreted Regex:
'          13,443 matches in 00:00:01.1514100
'       All Sentences with Compiled Regex:
'          13,443 matches in 00:00:00.7432921
```

O padrão de expressão regular usado neste exemplo, `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`, é definido como mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Começa a correspondência em um limite de palavra.
`\w+` | Fazer a correspondência a um ou mais caracteres de palavra.
`(\r?\n)|,?\s)` | Corresponde a um zero ou um retorno de carro seguido por um caractere de nova linha, ou zero ou uma vírgula seguida por um caractere de espaço em branco.
`(\w+((\r?\n)|,?\s))*` | Corresponde a zero ou mais ocorrências de um ou mais caracteres de palavra que são seguidos por zero ou por retornos de carro e por um caractere de nova linha ou por zero ou uma vírgula seguida por um caractere de espaço em branco.
`\w+` | Fazer a correspondência a um ou mais caracteres de palavra.
`[.?:;!]` | Corresponde a um ponto, um ponto de interrogação, dois-pontos, ponto-e-vírgula ou ponto de exclamação.
 
## <a name="take-charge-of-backtracking"></a>Tome conta do retrocesso

Normalmente, o mecanismo de expressões regulares usa progressão linear para percorrer uma cadeia de caracteres de entrada e compará-la a uma expressão regular padrão. No entanto, quando quantificadores indefinidos, como __*__, **+**, e **?** são usados em uma expressão regular padrão, o mecanismo de expressões regulares pode desistir de uma parte das correspondências parciais com êxito e retornar a um estado salvo anteriormente para pesquisar uma correspondência com êxito para o padrão inteiro. Esse processo é conhecido como retrocesso.

> [!NOTE]
> Para obter mais informações sobre o retrocesso, confira [Detalhes do comportamento de expressões regulares](regex-behavior.md) e [Retrocesso em expressões regulares](backtracking.md).
 
O suporte ao retrocesso proporciona poder e flexibilidade às expressões regulares. Ele também coloca a responsabilidade por controlar o funcionamento do mecanismo de expressões regulares nas mãos dos desenvolvedores de expressões regulares. Como os desenvolvedores geralmente não estão cientes dessa responsabilidade, o uso indevido do retrocesso ou a confiança no retrocesso excessivo geralmente exerce o papel mais significativo na degradação do desempenho da expressão regular. Em um cenário de pior caso, o tempo de execução pode dobrar para cada caractere adicional na cadeia de caracteres de entrada. Na verdade, quando o retrocesso é usado excessivamente, é fácil criar o equivalente programático de um loop infinito se a entrada quase corresponder ao padrão da expressão regular; o mecanismo de expressões regulares pode levar horas ou mesmo dias para processar uma cadeia de caracteres de entrada relativamente curta.

Frequentemente, os aplicativos pagam uma penalidade de desempenho por usar o retrocesso, mesmo ele não sendo essencial para uma correspondência. Por exemplo, a expressão regular `\b\p{Lu}\w*\b` corresponde a todas as palavras que começam com um caractere maiúsculo, como mostra a tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Começar a correspondência em um limite de palavra.
`\p{Lu}` | Corresponder a um caractere maiúsculo.
`\w*` | Corresponder a zero ou mais caracteres de palavra.
`\b` | Termina a correspondência em um limite de palavra.
 
Como um limite de palavra não é o mesmo que ou um subconjunto de, um caractere de palavra, não há nenhuma possibilidade de o mecanismo de expressões regulares cruzar um limite de palavra ao corresponder caracteres de palavra. Isso significa que, para esta expressão regular, o retrocesso nunca pode contribuir para o êxito total de qualquer correspondência – ele só pode prejudicar o desempenho, pois o mecanismo de expressões regulares é forçado a salvar o estado para cada correspondência preliminar bem-sucedida de um caractere de palavra.

Se você determinar que o retrocesso não é necessário, poderá desabilitá-lo usando o elemento de linguagem **(?>**_subexpression_**)**. O exemplo a seguir analisa uma cadeia de caracteres de entrada usando duas expressões regulares. A primeira, `\b\p{Lu}\w*\b`, depende do retrocesso. A segunda, `\b\p{Lu}(?>\w*)\b`, desabilita o retrocesso. Conforme mostrado pela saída do exemplo, ambas produzem o mesmo resultado.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This this word Sentence name Capital";
      string pattern = @"\b\p{Lu}\w*\b";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);

      Console.WriteLine();

      pattern = @"\b\p{Lu}(?>\w*)\b";   
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       This
//       Sentence
//       Capital
//       
//       This
//       Sentence
//       Capital
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This this word Sentence name Capital"
      Dim pattern As String = "\b\p{Lu}\w*\b"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next
      Console.WriteLine()

      pattern = "\b\p{Lu}(?>\w*)\b"   
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       This
'       Sentence
'       Capital
'       
'       This
'       Sentence
'       Capital
```

Em muitos casos, o retrocesso é essencial para corresponder um padrão de expressão regular ao texto de entrada. No entanto, o retrocesso excessivo pode prejudicar severamente o desempenho e criar a impressão de que um aplicativo parou de responder. Em particular, isso acontece quando quantificadores são aninhados e o texto que corresponde à subexpressão externa é um subconjunto do texto que corresponde à subexpressão interna. 

> [!WARNING]
> Além de evitar retrocessos excessivos, você deve usar o recurso de tempo limite para garantir que retrocessos excessivos não degradem severamente o desempenho da expressão regular. Para obter mais informações, confira a seção [Use valores de tempo limite](#use-time-out-values).
 
Por exemplo, o padrão de expressão regular `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` destina-se a corresponder a um número de peça que consiste em pelo menos um caractere alfanumérico. Todos os demais caracteres podem consistir em um caractere alfanumérico, um hífen, um sublinhado ou um ponto, embora o último caractere deva ser alfanumérico. Um cifrão termina o número da peça. Em alguns casos, esse padrão de expressão regular pode exibir um desempenho muito ruim porque os quantificadores estão aninhados e porque a subexpressão `[0-9A-Z]` é um subconjunto da subexpressão `[-.\w]*`.

Nesses casos, você pode otimizar o desempenho da expressão regular ao remover os quantificadores aninhados e substituir a subexpressão externa por uma declaração de lookahead ou lookbehind de largura zero. As asserções lookahead e lookbehind são âncoras; elas não movem o ponteiro na cadeia de caracteres de entrada, mas fazem uma verificação para verificar se uma condição especificada foi atendida. Por exemplo, a expressão regular do número de peça pode ser reescrita como `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`. Esse padrão de expressão regular é definido conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`^` | Começar a correspondência no início da cadeia de caracteres de entrada.
`[0-9A-Z]` | Corresponde a um caractere alfanumérico. O número de peça deve consistir em pelo menos este caractere.
`[-.\w]*` | Corresponde a zero ou mais ocorrências de qualquer caractere de palavra, hífen ou ponto.
`\$] | Corresponde a um cifrão.
`(?<=[0-9A-Z])` | Examine além do cifrão final para garantir que o caractere anterior seja alfanumérico.
`$` Finalizar a correspondência no final da cadeia de caracteres de entrada.
 
O exemplo a seguir ilustra o uso dessa expressão regular para corresponder a uma que contém possíveis números de peças.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$";
      string[] partNos = { "A1C$", "A4", "A4$", "A1603D$", "A1603D#" };

      foreach (var input in partNos) {
         Match match = Regex.Match(input, pattern);
         if (match.Success)
            Console.WriteLine(match.Value);
         else
            Console.WriteLine("Match not found.");
      }      
   }
}
// The example displays the following output:
//       A1C$
//       Match not found.
//       A4$
//       A1603D$
//       Match not found.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$"
      Dim partNos() As String = { "A1C$", "A4", "A4$", "A1603D$", 
                                  "A1603D#" }

      For Each input As String In partNos
         Dim match As Match = Regex.Match(input, pattern)
         If match.Success Then
            Console.WriteLine(match.Value)
         Else
            Console.WriteLine("Match not found.")
         End If
      Next      
   End Sub
End Module
' The example displays the following output:
'       A1C$
'       Match not found.
'       A4$
'       A1603D$
'       Match not found.
```

A linguagem de expressões regulares no .NET inclui os seguintes elementos de linguagem que você pode usar para eliminar quantificadores aninhados. Para obter mais informações, consulte [Constructos de agrupamento em expressões regulares](grouping.md).

Elemento de linguagem | Descrição
---------------- | ----------- 
**(?**=_subexpression_**)** | Lookahead positivo de largura zero. Examina além da posição atual para determinar se a *subexpression* corresponde à cadeia de caracteres de entrada.
**(?!**_subexpression_**)** | Lookahead negativo de largura zero. Examina além da posição atual para determinar se a *subexpressão* não corresponde à cadeia de caracteres de entrada.
**(?<**=_subexpression_**)** | Lookbehind positivo de largura zero. Examina o conteúdo que antecede a posição atual para determinar se a *subexpression* corresponde à cadeia de caracteres de entrada.
**(?<!**_subexpression_**)** | Lookbehind negativo de largura zero. Examina o conteúdo que antecede a posição atual para determinar se a *subexpressão* não corresponde à cadeia de caracteres de entrada.
 
## <a name="use-time-out-values"></a>Use valores de tempo limite

Se suas expressões regulares processarem entradas quase correspondentes ao padrão da expressão regular, elas poderão frequentemente confiar no retrocesso excessivo, o que afeta significativamente o desempenho. Além de considerar cuidadosamente o uso do retrocesso e testar a expressão regular contra entradas quase correspondentes, você deve sempre definir um valor de tempo limite para garantir que o impacto do retrocesso excessivo, caso ocorra, seja minimizado.

O intervalo de tempo limite da expressão regular define o período durante o qual o mecanismo de expressões regulares procurará uma única correspondência antes que o tempo limite seja atingido. O intervalo de tempo limite padrão é [Regex.InfiniteMatchTimeout](xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout), o que significa que a expressão regular não atingirá o tempo limite. É possível substituir esse valor e definir um intervalo de tempo limite da seguinte forma: 

* Fornecendo um valor de tempo limite ao criar uma instância de um objeto [Regex](xref:System.Text.RegularExpressions.Regex) chamando o construtor [Regex(String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.%23ctor(System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)).

* Chamando um padrão estático que corresponde ao método, como [Regex.Match(String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) ou [Regex.Replace(String, String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)), que inclui um parâmetro *matchTimeout*.

Se você tiver definido um intervalo de tempo limite e uma correspondência não for localizada no final do intervalo, o método de expressão regular gerará uma exceção [RegexMatchTimeoutException](xref:System.Text.RegularExpressions.RegexMatchTimeoutException). No manipulador de exceção, você pode optar por tentar fazer novamente a correspondência com um intervalo de tempo limite mais longo, abandonar a tentativa de correspondência e assumir que não há nenhuma correspondência ou abandonar a tentativa de correspondência e registrar as informações de exceção para análise futura.

O exemplo a seguir define um método `GetWordData` que instancia uma expressão regular com um intervalo de tempo limite de 350 milissegundos para calcular o número de palavras e o número médio de caracteres em uma palavra em um documento de texto. Se a operação de correspondência exceder o tempo limite, o intervalo de tempo limite será aumentado em 350 milissegundos e o objeto de [Regex](xref:System.Text.RegularExpressions.Regex) será reinstanciado. Se o novo intervalo de tempo limite exceder 1 segundo, o método gerará novamente a exceção no chamador.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      RegexUtilities util = new RegexUtilities();
      string title = "Doyle - The Hound of the Baskervilles.txt";
      try {
         var info = util.GetWordData(title);
         Console.WriteLine("Words:               {0:N0}", info.Item1);
         Console.WriteLine("Average Word Length: {0:N2} characters", info.Item2); 
      }
      catch (IOException e) {
         Console.WriteLine("IOException reading file '{0}'", title);
         Console.WriteLine(e.Message);
      }
      catch (RegexMatchTimeoutException e) {
         Console.WriteLine("The operation timed out after {0:N0} milliseconds", 
                           e.MatchTimeout.TotalMilliseconds);
      }
   }
}

public class RegexUtilities
{
   public Tuple<int, double> GetWordData(string filename)
   { 
      const int MAX_TIMEOUT = 1000;   // Maximum timeout interval in milliseconds.
      const int INCREMENT = 350;      // Milliseconds increment of timeout.

      List<string> exclusions = new List<string>( new string[] { "a", "an", "the" });
      int[] wordLengths = new int[29];        // Allocate an array of more than ample size.
      string input = null;
      StreamReader sr = null;
      try { 
         sr = new StreamReader(filename);
         input = sr.ReadToEnd();
      }
      catch (FileNotFoundException e) {
         string msg = String.Format("Unable to find the file '{0}'", filename);
         throw new IOException(msg, e);
      }
      catch (IOException e) {
         throw new IOException(e.Message, e);
      }
      finally {
         if (sr != null) sr.Close(); 
      }

      int timeoutInterval = INCREMENT;
      bool init = false;
      Regex rgx = null;
      Match m = null;
      int indexPos = 0;  
      do {
         try {
            if (! init) {
               rgx = new Regex(@"\b\w+\b", RegexOptions.None, 
                               TimeSpan.FromMilliseconds(timeoutInterval));
               m = rgx.Match(input, indexPos);
               init = true;
            }
            else { 
               m = m.NextMatch();
            }
            if (m.Success) {    
               if ( !exclusions.Contains(m.Value.ToLower()))
                  wordLengths[m.Value.Length]++;

               indexPos += m.Length + 1;   
            }
         }
         catch (RegexMatchTimeoutException e) {
            if (e.MatchTimeout.TotalMilliseconds < MAX_TIMEOUT) {
               timeoutInterval += INCREMENT;
               init = false;
            }
            else {
               // Rethrow the exception.
               throw; 
            }   
         }          
      } while (m.Success);

      // If regex completed successfully, calculate number of words and average length.
      int nWords = 0; 
      long totalLength = 0;

      for (int ctr = wordLengths.GetLowerBound(0); ctr <= wordLengths.GetUpperBound(0); ctr++) {
         nWords += wordLengths[ctr];
         totalLength += ctr * wordLengths[ctr];
      }
      return new Tuple<int, double>(nWords, totalLength/nWords);
   }
}
```

```vb
Imports System.Collections.Generic
Imports System.IO
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim util As New RegexUtilities()
      Dim title As String = "Doyle - The Hound of the Baskervilles.txt"
      Try
         Dim info = util.GetWordData(title)
         Console.WriteLine("Words:               {0:N0}", info.Item1)
         Console.WriteLine("Average Word Length: {0:N2} characters", info.Item2) 
      Catch e As IOException
         Console.WriteLine("IOException reading file '{0}'", title)
         Console.WriteLine(e.Message)
      Catch e As RegexMatchTimeoutException
         Console.WriteLine("The operation timed out after {0:N0} milliseconds", 
                           e.MatchTimeout.TotalMilliseconds)
      End Try
   End Sub
End Module

Public Class RegexUtilities
   Public Function GetWordData(filename As String) As Tuple(Of Integer, Double) 
      Const MAX_TIMEOUT As Integer = 1000  ' Maximum timeout interval in milliseconds.
      Const INCREMENT As Integer = 350     ' Milliseconds increment of timeout.

      Dim exclusions As New List(Of String)({"a", "an", "the" })
      Dim wordLengths(30) As Integer        ' Allocate an array of more than ample size.
      Dim input As String = Nothing
      Dim sr As StreamReader = Nothing
      Try 
         sr = New StreamReader(filename)
         input = sr.ReadToEnd()
      Catch e As FileNotFoundException
         Dim msg As String = String.Format("Unable to find the file '{0}'", filename)
         Throw New IOException(msg, e)
      Catch e As IOException
         Throw New IOException(e.Message, e)
      Finally
         If sr IsNot Nothing Then sr.Close() 
      End Try

      Dim timeoutInterval As Integer = INCREMENT
      Dim init As Boolean = False
      Dim rgx As Regex = Nothing
      Dim m As Match = Nothing
      Dim indexPos As Integer = 0  
      Do
         Try
            If Not init Then
               rgx = New Regex("\b\w+\b", RegexOptions.None, 
                               TimeSpan.FromMilliseconds(timeoutInterval))
               m = rgx.Match(input, indexPos)
               init = True
            Else 
               m = m.NextMatch()
            End If
            If m.Success Then    
               If Not exclusions.Contains(m.Value.ToLower()) Then
                  wordLengths(m.Value.Length) += 1
               End If
               indexPos += m.Length + 1   
            End If
         Catch e As RegexMatchTimeoutException
            If e.MatchTimeout.TotalMilliseconds < MAX_TIMEOUT Then
               timeoutInterval += INCREMENT
               init = False
            Else
               ' Rethrow the exception.
               Throw 
            End If   
         End Try          
      Loop While m.Success

      ' If regex completed successfully, calculate number of words and average length.
      Dim nWords As Integer
      Dim totalLength As Long

      For ctr As Integer = wordLengths.GetLowerBound(0) To wordLengths.GetUpperBound(0)
         nWords += wordLengths(ctr)
         totalLength += ctr * wordLengths(ctr)
      Next
      Return New Tuple(Of Integer, Double)(nWords, totalLength/nWords)
   End Function
End Class
```

## <a name="capture-only-when-necessary"></a>Capture somente quando necessário

As expressões regulares no .NET dão suporte a vários constructos de agrupamento, que permitem a você agrupar um padrão de expressão regular em uma ou mais subexpressões. Os constructos de agrupamentos mais usados na linguagem de expressões regulares no .NET **(**_subexpression_**)**, que define um grupo de captura numerado e **(?<*_name_**>**_subexpression_**)**, que define um grupo de captura nomeado. Os construtores de agrupamento são essenciais para criar referências reversas e definir uma subexpressão à qual um quantificador é aplicado. 

No entanto, o uso desses elementos de linguagem tem um custo. Eles fazem com que o objeto [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) retornado pela propriedade [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) seja populado com as capturas sem nome ou nomeadas mais recentes. Além disso, se um único constructo de agrupamento tiver capturado várias subcadeias de caracteres na cadeia de caracteres de entrada, também populam o objeto [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) retornado pela propriedade [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) de um grupo de captura específico com vários objetos [Capture](xref:System.Text.RegularExpressions.Capture).

Muitas vezes, os construtores de agrupamento são usados somente em uma expressão regular de modo que quantificadores possam ser aplicados a eles e os grupos capturados por essas subexpressão não são usados posteriormente. Por exemplo, a expressão regular `\b(\w+[;,]?\s?)+[.?!]` é criada para capturar uma frase inteira. A tabela a seguir descreve os elementos de linguagem nesse padrão de expressão regular e seu efeito nas coleções [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) e [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) do objeto [Match](xref:System.Text.RegularExpressions.Match).

Padrão | Descrição
------- | -----------
`\b` | Começa a correspondência em um limite de palavra.
`\w+` | Fazer a correspondência a um ou mais caracteres de palavra.
`[;,]?` | Corresponde a zero ou uma vírgula ou ponto e vírgula.
`\s?` | Corresponder a zero ou a um caractere de espaço em branco.
`(\w+[;,]?\s?)+` | Corresponde a uma ou mais ocorrências de um ou mais caracteres de palavra seguidos por uma vírgula opcional ou por ponto-e-vírgula seguido por um caractere de espaço em branco opcional. Isso define o primeiro grupo de captura, que é necessário para que a combinação de vários caracteres de palavra (ou seja, uma palavra) seguido por um símbolo de pontuação opcional seja repetida até que o mecanismo de expressões regulares atinja o final de uma sentença.
`[.?!]` | Corresponde a um ponto, um ponto de interrogação ou um ponto de exclamação.
 
Como o exemplo a seguir mostra, quando uma correspondência é encontrada, os objetos [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) e [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) são populados com as capturas da correspondência. Nesse caso, o grupo de captura `(\w+[;,]?\s?)` existe para que o quantificador **+** possa ser aplicado a ele, o que permite que o padrão de expressão regular corresponda a cada palavra em uma sentença. Caso contrário, ele corresponderia à última palavra em uma sentença.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is one sentence. This is another.";
      string pattern = @"\b(\w+[;,]?\s?)+[.?!]";

      foreach (Match match in Regex.Matches(input, pattern)) {
         Console.WriteLine("Match: '{0}' at index {1}.", 
                           match.Value, match.Index);
         int grpCtr = 0;
         foreach (Group grp in match.Groups) {
            Console.WriteLine("   Group {0}: '{1}' at index {2}.",
                              grpCtr, grp.Value, grp.Index);
            int capCtr = 0;
            foreach (Capture cap in grp.Captures) {
               Console.WriteLine("      Capture {0}: '{1}' at {2}.",
                                 capCtr, cap.Value, cap.Index);
               capCtr++;
            }
            grpCtr++;
         }          
         Console.WriteLine();        
      }
   }
}
// The example displays the following output:
//       Match: 'This is one sentence.' at index 0.
//          Group 0: 'This is one sentence.' at index 0.
//             Capture 0: 'This is one sentence.' at 0.
//          Group 1: 'sentence' at index 12.
//             Capture 0: 'This ' at 0.
//             Capture 1: 'is ' at 5.
//             Capture 2: 'one ' at 8.
//             Capture 3: 'sentence' at 12.
//       
//       Match: 'This is another.' at index 22.
//          Group 0: 'This is another.' at index 22.
//             Capture 0: 'This is another.' at 22.
//          Group 1: 'another' at index 30.
//             Capture 0: 'This ' at 22.
//             Capture 1: 'is ' at 27.
//             Capture 2: 'another' at 30.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is one sentence. This is another."
      Dim pattern As String = "\b(\w+[;,]?\s?)+[.?!]"

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Match: '{0}' at index {1}.", 
                           match.Value, match.Index)
         Dim grpCtr As Integer = 0
         For Each grp As Group In match.Groups
            Console.WriteLine("   Group {0}: '{1}' at index {2}.",
                              grpCtr, grp.Value, grp.Index)
            Dim capCtr As Integer = 0
            For Each cap As Capture In grp.Captures
               Console.WriteLine("      Capture {0}: '{1}' at {2}.",
                                 capCtr, cap.Value, cap.Index)
               capCtr += 1
            Next
            grpCtr += 1
         Next          
         Console.WriteLine()        
      Next    
   End Sub
End Module
' The example displays the following output:
'       Match: 'This is one sentence.' at index 0.
'          Group 0: 'This is one sentence.' at index 0.
'             Capture 0: 'This is one sentence.' at 0.
'          Group 1: 'sentence' at index 12.
'             Capture 0: 'This ' at 0.
'             Capture 1: 'is ' at 5.
'             Capture 2: 'one ' at 8.
'             Capture 3: 'sentence' at 12.
'       
'       Match: 'This is another.' at index 22.
'          Group 0: 'This is another.' at index 22.
'             Capture 0: 'This is another.' at 22.
'          Group 1: 'another' at index 30.
'             Capture 0: 'This ' at 22.
'             Capture 1: 'is ' at 27.
'             Capture 2: 'another' at 30.
```

Quando você usa subexpressões apenas para aplicar quantificadores a elas e não está interessado em texto capturado, desabilite as capturas de grupo. Por exemplo, o elemento de linguagem **(?:**_subexpression_**)** evita que o grupo ao qual ele se aplica capture subcadeias de caracteres correspondidas. No exemplo a seguir, o padrão de expressão regular do exemplo anterior é alterado para `\b(?:\w+[;,]?\s?)+[.?!]`. Conforme mostrado pela saída, ele impede que o mecanismo de expressões regulares popule as coleções [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) e [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection).

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is one sentence. This is another.";
      string pattern = @"\b(?:\w+[;,]?\s?)+[.?!]";

      foreach (Match match in Regex.Matches(input, pattern)) {
         Console.WriteLine("Match: '{0}' at index {1}.", 
                           match.Value, match.Index);
         int grpCtr = 0;
         foreach (Group grp in match.Groups) {
            Console.WriteLine("   Group {0}: '{1}' at index {2}.",
                              grpCtr, grp.Value, grp.Index);
            int capCtr = 0;
            foreach (Capture cap in grp.Captures) {
               Console.WriteLine("      Capture {0}: '{1}' at {2}.",
                                 capCtr, cap.Value, cap.Index);
               capCtr++;
            }
            grpCtr++;
         }          
         Console.WriteLine();        
      }
   }
}
// The example displays the following output:
//       Match: 'This is one sentence.' at index 0.
//          Group 0: 'This is one sentence.' at index 0.
//             Capture 0: 'This is one sentence.' at 0.
//       
//       Match: 'This is another.' at index 22.
//          Group 0: 'This is another.' at index 22.
//             Capture 0: 'This is another.' at 22.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is one sentence. This is another."
      Dim pattern As String = "\b(?:\w+[;,]?\s?)+[.?!]"

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Match: '{0}' at index {1}.", 
                           match.Value, match.Index)
         Dim grpCtr As Integer = 0
         For Each grp As Group In match.Groups
            Console.WriteLine("   Group {0}: '{1}' at index {2}.",
                              grpCtr, grp.Value, grp.Index)
            Dim capCtr As Integer = 0
            For Each cap As Capture In grp.Captures
               Console.WriteLine("      Capture {0}: '{1}' at {2}.",
                                 capCtr, cap.Value, cap.Index)
               capCtr += 1
            Next
            grpCtr += 1
         Next          
         Console.WriteLine()        
      Next    
   End Sub
End Module
' The example displays the following output:
'       Match: 'This is one sentence.' at index 0.
'          Group 0: 'This is one sentence.' at index 0.
'             Capture 0: 'This is one sentence.' at 0.
'       
'       Match: 'This is another.' at index 22.
'          Group 0: 'This is another.' at index 22.
'             Capture 0: 'This is another.' at 22.
```

É possível desabilitar as capturas de uma das seguintes formas:

* Use o elemento de linguagem **(?:**_subexpression_**)**. Esse elemento impede a captura de subcadeias de caracteres correspondidas no grupo ao qual se ele aplica. Ele não desabilita capturas de subcadeias de caracteres em grupos aninhados.

* Use a opção [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture). Ela desabilita todas as capturas sem nome ou implícitas no padrão de expressão regular. Quando você usa essa opção, somente as subcadeias de caracteres que correspondem aos grupos nomeados definidos com o elemento de linguagem **(?<**_name_**>**_subexpression_**)** podem ser capturadas. O sinalizador [ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) pode ser passado para o parâmetro de opções de um construtor de classe [Regex](xref:System.Text.RegularExpressions.Regex) ou para o parâmetro de opções de um método de correspondência estático [Regex](xref:System.Text.RegularExpressions.Regex).

* Use a opção **n** no elemento de linguagem **(?imnsx)**. Esta opção desabilita todas as capturas sem nome ou implícitas a partir do ponto no padrão de expressão regular em que o elemento aparece. As capturas são desabilitadas até o final do padrão ou até a opção **(-n)** habilitar capturas sem nome ou implícitas. Para obter mais informações, consulte [Constructos diversos em expressões regulares](miscellaneous.md).

* Use a opção **n** no elemento de linguagem **(?imnsx:**_subexpression_**)**. Esta opção desabilita todas as capturas sem nome ou implícitas na *subexpressão*. As capturas por grupos de capturas aninhadas sem nome ou implícitas também são desabilitadas.

## <a name="related-topics"></a>Tópicos relacionados

Título | Descrição
----- | ----------- 
[Detalhes do comportamento de expressões regulares](regex-behavior.md) | Examina a implementação do mecanismo de expressões regulares no .NET. O tópico concentra-se na flexibilidade de expressões regulares e explica a responsabilidade do desenvolvedor para garantir o funcionamento eficiente e robusto do mecanismo de expressões regulares.
[Retrocesso em expressões regulares](backtracking.md) | Explica o que é o retrocesso é como ele afeta o desempenho da expressão regular e examina os elementos de linguagem que fornecem alternativas ao retrocesso.
[Linguagem de expressão regular – referência rápida](quick-ref.md) | Descreve os elementos de linguagem de expressões regulares do .NET e fornece links para a documentação detalhada de cada elemento da linguagem.
 




<!--HONumber=Nov16_HO5-->


