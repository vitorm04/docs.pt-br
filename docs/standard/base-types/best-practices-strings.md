---
title: "Práticas recomendadas para o uso de cadeias de caracteres"
description: "Práticas recomendadas para o uso de cadeias de caracteres"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: b3cefaa4-0a3f-4a96-aba9-1de30fb07c29
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 3efd30bade564fe1b7dbf93237a9ff40c58c5f1e

---

# <a name="best-practices-for-using-strings"></a>Práticas recomendadas para o uso de cadeias de caracteres

O .NET dá um amplo suporte para desenvolvimento de aplicativos localizados e globalizados e torna mais fácil aplicar as convenções da cultura atual ou de uma cultura específica ao executar operações comuns, como a classificação e a exibição cadeias de caracteres. Mas a classificação ou a comparação de cadeias de caracteres nem sempre é uma operação que leva em conta a cultura. Por exemplo, cadeias de caracteres que são usadas internamente por um aplicativo normalmente devem ser manipuladas de maneira idêntica em todas as culturas. Quando os dados de cadeias de caracteres culturalmente independentes, como marcações XML, marcações HTML, nomes de usuário, caminhos de arquivo e nomes de objetos do sistema, são interpretados como se levassem em conta a cultura, o código do aplicativo pode estar sujeito a bugs sutis, desempenho ruim e, em alguns casos, problemas de segurança.

Este artigo examina os métodos de classificação, comparação e o uso de maiúsculas e minúsculas de cadeias de caracteres no .NET, apresenta recomendações para a seleção de um método de manipulação de cadeia de caracteres adequado e fornece informações adicionais sobre os métodos de manipulação de cadeia de caracteres. Ela também examina como os dados formatados, como dados numéricos e dados de data e hora, são manipulados para exibição e armazenamento. 

Este artigo contém as seguintes seções:

* [Recomendações para uso da cadeia de caracteres](#recommendations-for-string-usage)

* [Especificação explícita de comparações da cadeia de caracteres](#specifying-string-comparisons-explicitly)

* [Os detalhes da comparação de cadeia de caracteres](#the-details-of-string-comparison)

* [Escolha de um membro StringComparison para a chamada de método](#choosing-a-stringcomparison-member-for-your-method-call)

* [Métodos comuns de comparação da cadeia de caracteres](#common-string-comparison-methods)

* [Métodos que realizam comparação indireta de cadeia de caracteres](#methods-that-perform-string-comparison-indirectly)

* [Exibição e persistência de dados formatados](#displaying-and-persisting-formatted-data)

## <a name="recommendations-for-string-usage"></a>Recomendações para uso da cadeia de caracteres

Ao desenvolver com o .NET, siga estas recomendações simples quando usar cadeias de caracteres: 

* Use sobrecargas que especificam explicitamente as regras de comparação de cadeias de caracteres para operações de cadeia de caracteres. Normalmente, isso envolve chamar uma sobrecarga de método que tem um parâmetro do tipo [StringComparison](xref:System.StringComparison).

* Use [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) ou [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) para comparações como seu padrão seguro para a correspondência de cadeia de caracteres independente de cultura.

* Use comparações com [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) ou [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) para melhorar o desempenho.

* Use operações de cadeia de caracteres que se baseiam em [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) ao exibir a saída para o usuário.

* Use valores [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) ou [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) não linguísticos em vez de operações de cadeias de caracteres com base em [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) quando a comparação for linguisticamente irrelevante (simbólica, por exemplo).

* Use o método [String.ToUpperInvariant](xref:System.String.ToUpperInvariant) em vez do método [String.ToLowerInvariant](xref:System.String.ToLowerInvariant) ao normalizar cadeias de caracteres para comparação.

* Use uma sobrecarga do método [String](xref:System.String) `Equals` para testar se duas cadeias de caracteres são iguais.

* Use uma sobrecarga dos métodos [String](xref:System.String) `Compare` e [String.CompareTo](xref:System.String.CompareTo(System.String)) para classificar as cadeias de caracteres, não para verificar a igualdade.

* Use a formatação que leva em conta a cultura para exibir dados que não são de cadeias de caracteres, como números e datas, em uma interface do usuário. Use a formatação com a cultura invariável para persistir os dados que não são de cadeias de caracteres no formato de cadeia de caracteres.

Evite as práticas a seguir ao usar cadeias de caracteres:

* Não use sobrecargas que não especificam explicita ou implicitamente as regras de comparação de cadeias de caracteres para operações de cadeia de caracteres. 

* Não use uma sobrecarga dos métodos [String](xref:System.String) `Compare` ou [String.CompareTo](xref:System.String.CompareTo(System.String)) e teste para um valor retornado de zero para determinar se duas cadeias de caracteres são iguais.

* Não use a formatação que leva em conta a cultura para persistir dados numéricos ou dados de data e hora no formato de cadeia de caracteres.

## <a name="specifying-string-comparisons-explicitly"></a>Especificação explícita de comparações da cadeia de caracteres

A maioria dos métodos de manipulação de cadeia de caracteres no .NET é sobrecarregada. Normalmente, uma ou mais sobrecargas aceitam as configurações padrão, enquanto outras não aceitam nenhum padrão e definem a maneira exata em que as cadeias de caracteres devem ser comparadas ou manipuladas. A maioria dos métodos que não dependem de padrões inclui um parâmetro do tipo [StringComparison](xref:System.StringComparison), que é uma enumeração que especifica explicitamente as regras de comparação de cadeia de caracteres por cultura e maiúsculas e minúsculas. A tabela a seguir descreve os membros de enumeração de [StringComparison](xref:System.StringComparison). 

Membro de StringComparison | Descrição
----------------------- | -----------
[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) | Executa uma comparação que diferencia maiúsculas de minúsculas usando a cultura atual.
[CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase) | Executa uma comparação que não diferencia maiúsculas de minúsculas usando a cultura atual.
[StringComparison.Ordinal](xref:System.StringComparison.Ordinal) | Executa uma comparação ordinal.
[StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) | Executa uma comparação ordinal que não diferencia maiúsculas de minúsculas.

Por exemplo, o método [String](xref:System.String) `IndexOf`, que retorna um índice de uma subcadeia de caracteres em um objeto [String](xref:System.String) que corresponde a um caractere ou cadeia de caracteres, tem nove sobrecargas:

* [IndexOf(Char)](xref:System.String.IndexOf(System.Char)), [IndexOf(Char, Int32)](xref:System.String.IndexOf(System.Char,System.Int32)) e [IndexOf(Char, Int32, Int32)](xref:System.String.IndexOf(System.Char,System.Int32,System.Int32)), que por padrão executam uma pesquisa ordinal (diferencia maiúsculas de minúsculas e não leva em consideração a cultura) para um caractere na cadeia de caracteres.

* [IndexOf(String)](xref:System.String.IndexOf(System.String)), [IndexOf(String, Int32)](xref:System.String.IndexOf(System.String,System.Int32)) e [IndexOf(String, Int32, Int32)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32)), que por padrão executam uma pesquisa que diferencia maiúsculas de minúsculas e leva em consideração a cultura para uma subcadeia de caracteres na cadeia de caracteres.

* [IndexOf(String, StringComparison)](xref:System.String.IndexOf(System.String,System.StringComparison)), [IndexOf(String, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.StringComparison)) e [IndexOf(String, Int32, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32,System.StringComparison)), que incluem um parâmetro de tipo StringComparison que permite que a forma de comparação seja especificada.

É recomendável que você selecione uma sobrecarga que não usa valores padrão, pelos seguintes motivos:

* Algumas sobrecargas com parâmetros padrão (aqueles que pesquisam um [Char](xref:System.Char) na instância de cadeia de caracteres) realizam uma comparação ordinal, enquanto outras (aquelas que pesquisam uma cadeia de caracteres na instância de cadeia de caracteres) levam em consideração a cultura. É difícil lembrar qual método usa o valor padrão e é fácil confundir as sobrecargas.

* A intenção do código que depende de valores padrão para chamadas de método não é clara. No exemplo a seguir, que se baseia em padrões, é difícil saber se o desenvolvedor realmente planejava uma comparação ordinal ou linguística de duas cadeias de caracteres ou se uma diferença entre maiúsculas e minúsculas entre `protocol` e “http” pode fazer com que o teste de igualdade retorne `false`.

  ```csharp
  string protocol = GetProtocol(url);       
  if (String.Equals(protocol, "http", StringComparison.OrdinalIgnoreCase)) {
     // ...Code to handle HTTP protocol.
  }
  else {
     throw new InvalidOperationException();
  }
  ```

  ```vb
  Dim protocol As String = GetProtocol(url)       
  If String.Equals(protocol, "http") Then
    ' ...Code to handle HTTP protocol.
  Else
     Throw New InvalidOperationException()
  End If
  ```

Em geral, é recomendável que você chame um método que não se baseie em padrões, pois ele torna a intenção do código clara. Isso, por sua vez, torna o código mais legível e fácil de depurar e manter. O exemplo a seguir aborda as questões levantadas sobre o exemplo anterior. Ele deixa claro que a comparação ordinal é usada e que as diferenças de maiúsculas e minúsculas são ignoradas. 

```csharp
string protocol = GetProtocol(url);       
if (String.Equals(protocol, "http", StringComparison.OrdinalIgnoreCase)) {
   // ...Code to handle HTTP protocol.
}
else {
   throw new InvalidOperationException();
}
```

```vb
Dim protocol As String = GetProtocol(url)       
If String.Equals(protocol, "http", StringComparison.OrdinalIgnoreCase) Then
   ' ...Code to handle HTTP protocol.
Else
   Throw New InvalidOperationException()
End If
```

## <a name="the-details-of-string-comparison"></a>Os detalhes da comparação de cadeia de caracteres

A comparação de cadeia de caracteres é o centro de muitas operações relacionadas à cadeia de caracteres, especialmente a classificação e teste de igualdade. As cadeias de caracteres são classificadas em uma determinada ordem: se “my” aparece antes de “string” em uma lista classificada de cadeias de caracteres, “my” deve comparar menos que ou igual a “string”. Além disso, a comparação define implicitamente a igualdade. A operação de comparação retorna zero para cadeias de caracteres que considerar iguais. Uma boa interpretação é que nenhuma cadeia de caracteres é menor que a outra. Operações mais significativas envolvendo cadeias de caracteres incluem um ou ambos destes procedimentos: comparação com outra cadeia de caracteres e execução de uma operação de classificação bem definida.

No entanto, avaliar duas cadeias de caracteres quanto à igualdade ou ordem de classificação não gera um único resultado correto, o resultado depende dos critérios usados para comparar as cadeias de caracteres. Em particular, as comparações de cadeia de caracteres ordinais ou baseadas no uso de maiúsculas e minúsculas e convenções classificação da cultura atual ou da cultura invariável (uma cultura independente de localidade com base no idioma inglês) podem gerar resultados diferentes.

### <a name="string-comparisons-that-use-the-current-culture"></a>Comparações de cadeia de caracteres que usam a cultura atual

Um critério envolve o uso das convenções da cultura atual ao comparar cadeias de caracteres. As comparações que se baseiam na cultura atual usam a localidade ou a cultura atual do thread. Você deve sempre usar comparações que se baseiam na cultura atual quando os dados forem linguisticamente relevantes e quando eles refletirem a interação do usuário que leva em conta a cultura. 

No entanto, o comportamento da comparação e do uso de maiúsculas e minúsculas no .NET muda quando a cultura muda. Isso acontece quando um aplicativo é executado em um computador que tem uma cultura diferente do computador em que o aplicativo foi desenvolvido ou quando o thread em execução muda sua cultura. Esse comportamento é intencional, mas permanece não óbvio para muitos desenvolvedores. O exemplo a seguir ilustra as diferenças na ordem de classificação entre as culturas de inglês dos EUA ("en-US") e sueco ("sv-SE"). Observe que as palavras "ångström", "Windows" e "Visual Studio" aparecem em posições diferentes nas matrizes de cadeias de caracteres classificadas.

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] values= { "able", "ångström", "apple", "Æble", 
                         "Windows", "Visual Studio" };
      Array.Sort(values);
      DisplayArray(values);

      // Change culture to Swedish (Sweden).
      string originalCulture = CultureInfo.CurrentCulture.Name;
      Thread.CurrentThread.CurrentCulture = new CultureInfo("sv-SE");
      Array.Sort(values);
      DisplayArray(values);

      // Restore the original culture.
      Thread.CurrentThread.CurrentCulture = new CultureInfo(originalCulture);
    }

    private static void DisplayArray(string[] values)
    {
      Console.WriteLine("Sorting using the {0} culture:",  
                        CultureInfo.CurrentCulture.Name);
      foreach (string value in values)
         Console.WriteLine("   {0}", value);

      Console.WriteLine();
    }
}
// The example displays the following output:
//       Sorting using the en-US culture:
//          able
//          Æble
//          ångström
//          apple
//          Visual Studio
//          Windows
//       
//       Sorting using the sv-SE culture:
//          able
//          Æble
//          apple
//          Windows
//          Visual Studio
//          ångström
```

```vb
Imports System.Globalization
Imports System.Threading

Module Example
   Public Sub Main()
      Dim values() As String = { "able", "ångström", "apple", _
                                 "Æble", "Windows", "Visual Studio" }
      Array.Sort(values)
      DisplayArray(values)

      ' Change culture to Swedish (Sweden).
      Dim originalCulture As String = CultureInfo.CurrentCulture.Name
      Thread.CurrentThread.CurrentCulture = New CultureInfo("sv-SE")
      Array.Sort(values)
      DisplayArray(values)

      ' Restore the original culture.
      Thread.CurrentThread.CurrentCulture = New CultureInfo(originalCulture)
    End Sub

    Private Sub DisplayArray(values() As String)
      Console.WRiteLine("Sorting using the {0} culture:", _ 
                        CultureInfo.CurrentCulture.Name)
      For Each value As String In values
         Console.WriteLine("   {0}", value)
      Next
      Console.WriteLine()   
    End Sub
End Module
' The example displays the following output:
'       Sorting using the en-US culture:
'          able
'          Æble
'          ångström
'          apple
'          Visual Studio
'          Windows
'       
'       Sorting using the sv-SE culture:
'          able
'          Æble
'          apple
'          Windows
'          Visual Studio
'          ångström
```

As comparações que não diferenciam maiúsculas de minúsculas que usam a cultura atual são iguais às comparações que levam em conta a cultura, exceto que elas ignoram as maiúsculas e minúsculas conforme determinado pela cultura atual do thread. Esse comportamento pode se manifestar em ordens de classificação também. 

As comparações que usam a semântica de cultura atual são o padrão para os seguintes métodos:

* Sobrecargas [String](xref:System.String) `Compare` que não incluem um parâmetro [StringComparison](xref:System.StringComparison).

* Sobrecargas [String.CompareTo](xref:System.String.CompareTo(System.String)).

* O método [String.StartsWith(String)](xref:System.String.StartsWith(System.String)) padrão. 

* O método [String.EndsWith(String)](xref:System.String.EndsWith(System.String)) padrão.

* Sobrecargas [String](xref:System.String) `IndexOf` que aceitam uma [String](xref:System.String) como um parâmetro de pesquisa e que não têm um parâmetro [StringComparison](xref:System.StringComparison).

* Sobrecargas [String](xref:System.String) `LastIndexOf` que aceitam uma [String](xref:System.String) como um parâmetro de pesquisa e que não têm um parâmetro [StringComparison](xref:System.StringComparison).

Em qualquer caso, é recomendável que você chame uma sobrecarga que tenha um parâmetro [StringComparison](xref:System.StringComparison) para deixar a intenção da chamada do método clara. 

Bugs sutis e não tão sutis podem surgir quando dados de cadeias de caracteres não linguísticas são interpretados linguisticamente ou quando os dados da cadeia de caracteres de uma cultura específica são interpretados usando as convenções de outra cultura. O exemplo canônico é o problema do I turco.

Para quase todos os alfabetos latinos, incluindo o do inglês dos EUA, o caractere "i" (\u0069) é a versão em letra minúscula do caractere "I" (\u0049). Essa regra de maiúsculas e minúsculas rapidamente se torna o padrão para alguém programando em tal cultura. No entanto, o alfabeto turco ("tr-TR") inclui um caractere "I com um ponto", "İ" (\u0130), que é a versão maiúscula de "i". O turco também inclui um caractere minúsculo "i sem um ponto", "ı" (\u0131), que em maiúscula é “I”. Esse comportamento também ocorre na cultura azerbaidjana ("az").

Portanto, as suposições feitas sobre a colocação do "i" em maiúscula ou do "I" em minúscula não são válidas entre todas as culturas. Se você usar as sobrecargas padrão para rotinas de comparação de cadeias de caracteres, elas estarão sujeitas à variação entre culturas. Se os dados a serem comparados são forem linguísticos, o uso das sobrecargas padrão pode gerar resultados indesejáveis, como a tentativa a seguir de realizar uma comparação que não diferencia maiúsculas de minúsculas das cadeias de caracteres “file” e “FILE” ilustra.

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string fileUrl = "file";
      Thread.CurrentThread.CurrentCulture = new CultureInfo("en-US");
      Console.WriteLine("Culture = {0}",
                        Thread.CurrentThread.CurrentCulture.DisplayName);
      Console.WriteLine("(file == FILE) = {0}", 
                       fileUrl.StartsWith("FILE", true, null));
      Console.WriteLine();

      Thread.CurrentThread.CurrentCulture = new CultureInfo("tr-TR");
      Console.WriteLine("Culture = {0}",
                        Thread.CurrentThread.CurrentCulture.DisplayName);
      Console.WriteLine("(file == FILE) = {0}", 
                        fileUrl.StartsWith("FILE", true, null));
   }
}
// The example displays the following output:
//       Culture = English (United States)
//       (file == FILE) = True
//       
//       Culture = Turkish (Turkey)
//       (file == FILE) = False
```

```vb
Imports System.Globalization
Imports System.Threading

Module Example
   Public Sub Main()
      Dim fileUrl = "file"
      Thread.CurrentThread.CurrentCulture = New CultureInfo("en-US")
      Console.WriteLine("Culture = {0}", _
                        Thread.CurrentThread.CurrentCulture.DisplayName)
      Console.WriteLine("(file == FILE) = {0}", _ 
                       fileUrl.StartsWith("FILE", True, Nothing))
      Console.WriteLine()

      Thread.CurrentThread.CurrentCulture = New CultureInfo("tr-TR")
      Console.WriteLine("Culture = {0}", _
                        Thread.CurrentThread.CurrentCulture.DisplayName)
      Console.WriteLine("(file == FILE) = {0}", _ 
                        fileUrl.StartsWith("FILE", True, Nothing))
   End Sub
End Module
' The example displays the following output:
'       Culture = English (United States)
'       (file == FILE) = True
'       
'       Culture = Turkish (Turkey)
'       (file == FILE) = False
```

Essa comparação pode causar problemas significativos se a cultura for usada inadvertidamente nas configurações sensíveis à segurança, como no exemplo a seguir. Uma chamada de método, como `IsFileURI("file:")` retorna `true` se a cultura atual for inglês dos EUA, mas `false` se a cultura atual for turco. Assim, em sistemas turcos, alguém poderia driblar as medidas de segurança que bloqueiam o acesso a URIs que não diferenciam maiúsculas de minúsculas que começam com “FILE:”.

```csharp
public static bool IsFileURI(String path) 
{
   return path.StartsWith("FILE:", true, null);
}
```

```vb
Public Shared Function IsFileURI(path As String) As Boolean 
   Return path.StartsWith("FILE:", True, Nothing)
End Function
```

Nesse caso, como "file:" deve ser interpretado como um identificador não linguístico que não leva em conta a cultura, o código deveria ser escrito como mostrado no exemplo a seguir.

```csharp
public static bool IsFileURI(string path) 
{
   return path.StartsWith("FILE:", StringComparison.OrdinalIgnoreCase);
}
```

```vb
Public Shared Function IsFileURI(path As String) As Boolean 
    Return path.StartsWith("FILE:", StringComparison.OrdinalIgnoreCase)
End Function
```

## <a name="ordinal-string-operations"></a>Operações Ordinais da Cadeia de Caracteres

Especificar o valor [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) ou [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) em uma chamada de método significa uma comparação não linguística em que as funcionalidades de idiomas naturais são ignoradas. Os métodos que são invocados com esses valores de [StringComparison](xref:System.StringComparison) baseiam as decisões de operação da cadeia de caracteres em comparações de byte simples em vez de no uso de maiúsculas e minúsculas ou tabelas de equivalência que são parametrizadas pela cultura. Na maioria dos casos, essa abordagem se adapta melhor à interpretação pretendida de cadeias de caracteres, enquanto torna o código mais rápido e confiável. 

Comparações ordinais são comparações de cadeia de caracteres nas quais cada byte de cada cadeia de caracteres é comparado sem a interpretação linguística, por exemplo, “windows” não corresponde a “Windows”. Use essa comparação quando o contexto determinar que as cadeias de caracteres devem corresponder exatamente ou exigir uma política de correspondência conservadora. Além disso, a comparação ordinal é a operação de comparação mais rápida porque ela não aplica nenhuma regra linguística ao determinar um resultado.

As cadeias de caracteres no .NET podem conter caracteres nulos inseridos. Uma das diferenças mais clara entre a comparação ordinal e a que leva em conta a cultura (incluindo comparações que usam a cultura invariável) diz respeito à manipulação de caracteres nulos inseridos em uma cadeia de caracteres. Esses caracteres são ignorados quando você usa os métodos [String](xref:System.String) `Compare` e [String](xref:System.String) `Equals` para realizar comparações que levam em conta a cultura (incluindo comparações que usam a cultura invariável). Como resultado, em comparações que levam em conta a cultura, cadeias de caracteres que contêm caracteres nulos inseridos podem ser consideradas iguais a cadeias de caracteres que não contêm. 

> [!IMPORTANT]
> Embora os métodos de comparação de cadeia de caracteres ignorem caracteres nulos inseridos, os métodos de pesquisa de cadeia de caracteres como [String.Contains](xref:System.String.Contains(System.String)), [String.EndsWith](xref:System.String.EndsWith(System.String)), [String.IndexOf](xref:System.String.IndexOf(System.Char)), [String.LastIndexOf](xref:System.String.LastIndexOf(System.String)) e [String.StartsWith](xref:System.String.StartsWith(System.String)) não. 

O exemplo a seguir executa uma comparação que leva em conta a cultura da cadeia de caracteres "Aa" com uma cadeia de caracteres semelhante que contém vários caracteres nulos inseridos entre "A" e "a" e mostra como as duas cadeias de caracteres são consideradas iguais. 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string str1 = "Aa";
      string str2 = "A" + new String('\u0000', 3) + "a";
      Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", 
                        str1, ShowBytes(str1), str2, ShowBytes(str2));
      Console.WriteLine("   With String.Compare:");
      Console.WriteLine("      Current Culture: {0}", 
                        String.Compare(str1, str2, StringComparison.CurrentCulture));
      Console.WriteLine("      Invariant Culture: {0}", 
                        String.Compare(str1, str2, StringComparison.InvariantCulture));

      Console.WriteLine("   With String.Equals:");
      Console.WriteLine("      Current Culture: {0}", 
                        String.Equals(str1, str2, StringComparison.CurrentCulture));
      Console.WriteLine("      Invariant Culture: {0}", 
                        String.Equals(str1, str2, StringComparison.InvariantCulture));
   }

   private static string ShowBytes(string str)
   {
      string hexString = String.Empty;
      for (int ctr = 0; ctr < str.Length; ctr++)
      {
         string result = String.Empty;
         result = Convert.ToInt32(str[ctr]).ToString("X4");
         result = " " + result.Substring(0,2) + " " + result.Substring(2, 2);
         hexString += result;
      }
      return hexString.Trim();
   }
}
// The example displays the following output:
//    Comparing 'Aa' (00 41 00 61) and 'A   a' (00 41 00 00 00 00 00 00 00 61):
//       With String.Compare:
//          Current Culture: 0
//          Invariant Culture: 0
//       With String.Equals:
//          Current Culture: True
//          Invariant Culture: True
```

```vb
Module Example
   Public Sub Main()
      Dim str1 As String = "Aa"
      Dim str2 As String = "A" + New String(Convert.ToChar(0), 3) + "a"
      Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", _
                        str1, ShowBytes(str1), str2, ShowBytes(str2))
      Console.WriteLine("   With String.Compare:")
      Console.WriteLine("      Current Culture: {0}", _
                        String.Compare(str1, str2, StringComparison.CurrentCulture))
      Console.WriteLine("      Invariant Culture: {0}", _
                        String.Compare(str1, str2, StringComparison.InvariantCulture))

      Console.WriteLine("   With String.Equals:")
      Console.WriteLine("      Current Culture: {0}", _
                        String.Equals(str1, str2, StringComparison.CurrentCulture))
      Console.WriteLine("      Invariant Culture: {0}", _
                        String.Equals(str1, str2, StringComparison.InvariantCulture))
   End Sub

   Private Function ShowBytes(str As String) As String
      Dim hexString As String = String.Empty
      For ctr As Integer = 0 To str.Length - 1
         Dim result As String = String.Empty
         result = Convert.ToInt32(str.Chars(ctr)).ToString("X4")
         result = " " + result.Substring(0,2) + " " + result.Substring(2, 2)
         hexString += result
      Next
      Return hexString.Trim()
   End Function
End Module
```

No entanto, as cadeias de caracteres não são consideradas iguais ao usar a comparação ordinal, como mostra o exemplo a seguir.

```csharp
Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", 
                  str1, ShowBytes(str1), str2, ShowBytes(str2));
Console.WriteLine("   With String.Compare:");
Console.WriteLine("      Ordinal: {0}", 
                  String.Compare(str1, str2, StringComparison.Ordinal));

Console.WriteLine("   With String.Equals:");
Console.WriteLine("      Ordinal: {0}", 
                  String.Equals(str1, str2, StringComparison.Ordinal));
// The example displays the following output:
//    Comparing 'Aa' (00 41 00 61) and 'A   a' (00 41 00 00 00 00 00 00 00 61):
//       With String.Compare:
//          Ordinal: 97
//       With String.Equals:
//          Ordinal: False
```

```vb
Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", _
                  str1, ShowBytes(str1), str2, ShowBytes(str2))
Console.WriteLine("   With String.Compare:")
Console.WriteLine("      Ordinal: {0}", _
                  String.Compare(str1, str2, StringComparison.Ordinal))

Console.WriteLine("   With String.Equals:")
Console.WriteLine("      Ordinal: {0}", _
                  String.Equals(str1, str2, StringComparison.Ordinal))
' The example displays the following output:
'    Comparing 'Aa' (00 41 00 61) and 'A   a' (00 41 00 00 00 00 00 00 00 61):
'       With String.Compare:
'          Ordinal: 97
'       With String.Equals:
'          Ordinal: False
```

As comparações ordinais que não diferenciam maiúsculas de minúsculas são a próxima abordagem conservadora. Essas comparações ignoram a maioria das maiúsculas e minúsculas, por exemplo, "windows" corresponde a "Windows". Ao lidar com caracteres ASCII, essa política é equivalente a [StringComparison.Ordinal](xref:System.StringComparison.Ordinal), exceto que ela ignora as maiúsculas e minúsculas de ASCII normais. Portanto, qualquer caractere em [A, Z] (\u0041-\u005A) corresponde ao caractere correspondente em [a,z] (\u0061-\007A). As maiúsculas e minúsculas fora do intervalo de ASCII usam as tabelas de cultura invariável. Portanto, a comparação a seguir:

```csharp
String.Compare(strA, strB, StringComparison.OrdinalIgnoreCase);
```

```vb
String.Compare(strA, strB, StringComparison.OrdinalIgnoreCase)
```

é equivalente a (mas mais rápida do que) esta comparação: 

```csharp
String.Compare(strA.ToUpperInvariant(), strB.ToUpperInvariant(), 
               StringComparison.Ordinal);
```

```vb
String.Compare(strA.ToUpperInvariant(), strB.ToUpperInvariant(), 
               StringComparison.Ordinal)
```

Essas comparações ainda são muito rápidas.

Ambas [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) e [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) usam os valores binários diretamente e são mais adequadas para correspondência. Quando você não tiver certeza sobre as configurações de comparação, use um destes dois valores. No entanto, como elas executam uma comparação byte por byte, elas não classificam por uma ordem de classificação linguística (como um dicionário de inglês), mas por ordem de classificação binária. Os resultados podem parecer estranhos na maioria dos contextos se exibido aos usuários.

A semântica ordinal é o padrão para sobrecargas [String](xref:System.String) `Equals` que não incluem um argumento [StringComparison](xref:System.StringComparison) (incluindo o operador de igualdade). Em qualquer caso, é recomendável que você chame uma sobrecarga que tenha um parâmetro [StringComparison](xref:System.StringComparison).

### <a name="string-operations-that-use-the-invariant-culture"></a>Operações da cadeia de caracteres que usam a cultura invariável

As comparações com a cultura invariável usam a propriedade [CompareInfo](xref:System.Globalization.CompareInfo) retornada pela propriedade [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) estática. Esse comportamento é o mesmo em todos os sistemas, ele converte qualquer caractere fora de seu intervalo no que ele acredita que sejam caracteres invariáveis equivalentes. Essa política pode ser útil para manter um conjunto de comportamentos de cadeia de caracteres entre culturas, mas geralmente fornece resultados inesperados.

As comparações que não diferenciam maiúsculas de minúsculas com a cultura invariável usam a propriedade [CompareInfo](xref:System.Globalization.CompareInfo) estática retornada pela propriedade [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) estática para informações de comparação também. As diferenças de maiúsculas e minúsculas entre esses caracteres convertidos são ignoradas.

O objeto [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) objeto faz um método [String](xref:System.String) `Compare` interpretar determinados conjuntos de caracteres como equivalentes. Por exemplo, a equivalência a seguir é válida na cultura invariável:

InvariantCulture: a + ̊ = å

O caractere da letra A minúscula latina “a” (\u0061), quando ele está próximo ao caractere de anel superior combinável "+ " ̊" (\u030a), é interpretado como a letra A minúscula latina com o caractere de anel superior "å" (\u00e5). Como mostra o exemplo a seguir, esse comportamento é diferente da comparação ordinal.

```csharp
string separated = "\u0061\u030a";
string combined = "\u00e5";

Console.WriteLine("Equal sort weight of {0} and {1} using InvariantCulture: {2}",
                  separated, combined, 
                  String.Compare(separated, combined, 
                                 StringComparison.InvariantCulture) == 0);

Console.WriteLine("Equal sort weight of {0} and {1} using Ordinal: {2}",
                  separated, combined,
                  String.Compare(separated, combined, 
                                 StringComparison.Ordinal) == 0);
// The example displays the following output:
//    Equal sort weight of a° and å using InvariantCulture: True
//    Equal sort weight of a° and å using Ordinal: False 
```

```vb
Dim separated As String = ChrW(&h61) + ChrW(&h30a)
Dim combined As String = ChrW(&he5)

Console.WriteLine("Equal sort weight of {0} and {1} using InvariantCulture: {2}", _
                  separated, combined, _
                  String.Compare(separated, combined, _ 
                                 StringComparison.InvariantCulture) = 0)

Console.WriteLine("Equal sort weight of {0} and {1} using Ordinal: {2}", _
                  separated, combined, _
                  String.Compare(separated, combined, _
                                 StringComparison.Ordinal) = 0)
' The example displays the following output:
'    Equal sort weight of a° and å using InvariantCulture: True
'    Equal sort weight of a° and å using Ordinal: False
```

Ao interpretar nomes de arquivo, cookies ou qualquer outro elemento em que uma combinação como "å" pode aparecer, as comparações ordinais ainda oferecem o comportamento mais transparente e adequado.

De forma geral, a cultura invariável tem muito poucas propriedades que a tornam útil para comparação. Ela faz a comparação de maneira linguisticamente relevante, o que impede que ela garanta a equivalência simbólica total, mas não é a opção de exibição em nenhuma cultura. Por exemplo, se um arquivo de dados grande que contém uma lista de identificadores classificados para exibição acompanha um aplicativo, a adição a essa lista exige uma inserção com a inserção de estilo invariável.

## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a>Escolha de um membro StringComparison para a chamada de método

A tabela a seguir descreve o mapeamento do contexto semântico da cadeia de caracteres para um membro de enumeração [StringComparison](xref:System.StringComparison).

Dados | Comportamento | Valor de System.StringComparison correspondente
---- | -------- | -------------------------------------------
Identificadores internos que diferenciam maiúsculas de minúsculas, identificadores que diferenciam maiúsculas de minúsculas em padrões, como XML e HTTP ou configurações relacionadas à segurança que diferenciam maiúsculas de minúsculas. | Um identificador não linguístico, em que bytes correspondem exatamente. | [StringComparison.Ordinal](xref:System.StringComparison.Ordinal)
Identificadores internos que não diferenciam maiúsculas de minúsculas, identificadores que não diferenciam maiúsculas de minúsculas em padrões, como XML e HTTP, caminhos de arquivo, valores e chave de Registro, variáveis do ambiente, identificadores de recurso (por exemplo nomes de identificador) ou configurações relacionadas à segurança que não diferenciam maiúsculas de minúsculas. | Um identificador não linguístico, em que as maiúsculas e minúsculas são irrelevantes. | [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase)
Dados exibidos para o usuário ou para a maioria das entradas do usuário. | Dados que exigem os costumes linguísticos locais. | [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) ou [CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase)

## <a name="common-string-comparison-methods"></a>Métodos comuns de comparação da cadeia de caracteres

As seções a seguir descrevem os métodos que são mais comumente usados para a comparação de cadeias de caracteres.

### <a name="stringcompare"></a>String.Compare

Interpretação padrão: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).

Como a operação mais central da interpretação de cadeia de caracteres, todas as instâncias de chamadas desse método devem ser examinadas para determinar se as cadeias de caracteres devem ser interpretadas de acordo com a cultura atual ou dissociadas da cultura (simbolicamente). Normalmente, é o último e uma comparação de [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) deve ser usada.

A classe [System.Globalization.CompareInfo](xref:System.Globalization.CompareInfo), que é retornada pela propriedade [CultureInfo.CompareInfo](xref:System.Globalization.CultureInfo.CompareInfo), também inclui um método [Compare](xref:System.Globalization.CompareInfo.Compare(System.String,System.Int32,System.String,System.Int32,System.Globalization.CompareOptions)) que fornece um grande número de opções de correspondência (ordinal, ignorando os espaços em branco, ignorando o tipo kana e assim por diante) por meio da enumeração de sinalizador [CompareOptions](xref:System.Globalization.CompareOptions). 

### <a name="stringcompareto"></a>String.CompareTo

Interpretação padrão: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).

Esse método no momento não oferece uma sobrecarga que especifica um tipo [StringComparison](xref:System.StringComparison). Normalmente é possível converter esse método para o formato [String.Compare(String, String, StringComparison)](xref:System.String.Compare(System.String,System.String,System.StringComparison)) recomendado.

Os tipos que implementam as interfaces [IComparable](xref:System.IComparable) e [IComparable&lt;T&gt;](xref:System.IComparable%601) implementam esse método. Como ele não oferece a opção de um parâmetro [StringComparison](xref:System.StringComparison), os tipos de implementação geralmente permitem que o usuário especifique um [StringComparer](xref:System.StringComparer) em seu construtor. O exemplo a seguir define uma classe `FileName` cujo construtor de classe inclui um parâmetro [StringComparer](xref:System.StringComparer). Esse objeto [StringComparer](xref:System.StringComparer) é então usado no método `FileName.CompareTo`.

```csharp
using System;

public class FileName : IComparable
{
   string fname;
   StringComparer comparer; 

   public FileName(string name, StringComparer comparer)
   {
      if (String.IsNullOrEmpty(name))
         throw new ArgumentNullException("name");

      this.fname = name;

      if (comparer != null)
         this.comparer = comparer;
      else
         this.comparer = StringComparer.OrdinalIgnoreCase;
   }

   public string Name
   {
      get { return fname; }
   }

   public int CompareTo(object obj)
   {
      if (obj == null) return 1;

      if (! (obj is FileName))
         return comparer.Compare(this.fname, obj.ToString());
      else
         return comparer.Compare(this.fname, ((FileName) obj).Name);
   }
}
```

```vb
Public Class FileName : Implements IComparable
   Dim fname As String
   Dim comparer As StringComparer 

   Public Sub New(name As String, comparer As StringComparer)
      If String.IsNullOrEmpty(name) Then
         Throw New ArgumentNullException("name")
      End If

      Me.fname = name

      If comparer IsNot Nothing Then
         Me.comparer = comparer
      Else
         Me.comparer = StringComparer.OrdinalIgnoreCase
      End If      
   End Sub

   Public ReadOnly Property Name As String
      Get
         Return fname
      End Get   
   End Property

   Public Function CompareTo(obj As Object) As Integer _
          Implements IComparable.CompareTo
      If obj Is Nothing Then Return 1

      If Not TypeOf obj Is FileName Then
         obj = obj.ToString()
      Else
         obj = CType(obj, FileName).Name
      End If         
      Return comparer.Compare(Me.fname, obj)
   End Function
End Class
```

### <a name="stringequals"></a>String.Equals

Interpretação padrão: [StringComparison.Ordinal](xref:System.StringComparison.Ordinal).

A classe [String](xref:System.String) permite que você teste a igualdade chamando as sobrecargas do método `Equals` ou estáticas ou usando o operador de igualdade estático. O operador e as sobrecargas utilizam a comparação ordinal por padrão. No entanto, ainda é recomendável que você chame uma sobrecarga que especifique explicitamente o tipo [StringComparison](xref:System.StringComparison) mesmo se você desejar executar uma comparação ordinal. Isso facilita a pesquisa de código para uma determinada interpretação da cadeia de caracteres. 

### <a name="stringtoupper-and-stringtolower"></a>String.ToUpper e String.ToLower

Interpretação padrão: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).

Você deve ter cuidado ao usar esses métodos, pois forçar uma cadeia de caracteres para maiúsculas ou minúsculas normalmente é usado como uma normalização pequena para comparar cadeias de caracteres independentemente de maiúsculas e minúsculas. Nesse caso, considere o uso de uma comparação que não diferencie maiúsculas de minúsculas. 

Os métodos [String.ToUpperInvariant](xref:System.String.ToUpperInvariant) e [String.ToLowerInvariant](xref:System.String.ToLowerInvariant) também estão disponíveis. [ToUpperInvariant](xref:System.String.ToUpperInvariant) é o modo padrão de normalizar as maiúsculas e minúsculas. Comparações feitas usando [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) são comportamentalmente a composição de duas chamadas: chamar [ToUpperInvariant](xref:System.String.ToUpperInvariant) nos dois argumentos da cadeia de caracteres e fazer uma comparação usando [StringComparison.Ordinal](xref:System.StringComparison.Ordinal).

Também há sobrecargas disponíveis para converter para maiúsculas e minúsculas em uma cultura específica, passando um objeto [CultureInfo](xref:System.Globalization.CultureInfo) que representa aquela cultura para o método.

### <a name="chartoupper-and-chartolower"></a>Char.ToUpper e Char.ToLower

Interpretação padrão: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).

Esses métodos funcionam de forma semelhante aos métodos [String.ToUpper](xref:System.String.ToUpper) e [String.ToLower](xref:System.String.ToLower) descritos na seção anterior.

### <a name="stringstartswith-and-stringendswith"></a>String.StartsWith e String.EndsWith

Interpretação padrão: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).

Por padrão, esses dois métodos executam uma comparação que leva em conta a cultura.

### <a name="stringindexof-and-stringlastindexof"></a>String.IndexOf e String.LastIndexOf

Interpretação padrão: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).

Há uma falta de consistência em como as sobrecargas padrão desses métodos realizam comparações. Todos os métodos [String](xref:System.String) `IndexOf` e [String](xref:System.String) `LastIndexOf` que incluem um parâmetro [Char](xref:System.Char) realizam uma comparação ordinal, mas os métodos [String](xref:System.String) `IndexOf` e [String`](xref:System.String) `LastIndexOf` padrão que incluem um parâmetro [String](xref:System.String) realizam uma comparação que leva em conta a cultura. 

Se você chamar o método ` `IndexOf` or `LastIndexOf` e passar a ele uma cadeia de caracteres para localizar na instância atual, é recomendável que você chame uma sobrecarga que especifique explicitamente o tipo [StringComparison](xref:System.StringComparison). As sobrecargas que incluem um argumento [Char](xref:System.Char) não permitem que você especifique um tipo [StringComparison](xref:System.StringComparison).

## <a name="methods-that-perform-string-comparison-indirectly"></a>Métodos que realizam comparação indireta de cadeia de caracteres

Alguns métodos que não de cadeias de caracteres que têm a comparação de cadeia de caracteres como uma operação central usam o tipo [StringComparer](xref:System.StringComparer). A classe [StringComparer](xref:System.StringComparer) inclui quatro propriedades estáticas que retornam instâncias [StringComparer](xref:System.StringComparer) cujos métodos `Compare` realizam os seguintes tipos de comparações de cadeias de caracteres:

* Comparações de cadeias de caracteres que levam em conta a cultura usando a cultura atual. Esse objeto [StringComparer](xref:System.StringComparer) é retornado pela propriedade [StringComparer.CurrentCulture](xref:System.StringComparer.CurrentCulture).

* Comparações que não diferenciam maiúsculas de minúsculas usando a cultura atual. Esse objeto [StringComparer](xref:System.StringComparer) é retornado pela propriedade [StringComparer.CurrentCultureIgnoreCase](xref:System.StringComparer.CurrentCultureIgnoreCase).

* Comparação ordinal. Esse objeto [StringComparer](xref:System.StringComparer) é retornado pela propriedade [StringComparer.Ordinal](xref:System.StringComparer.Ordinal). 

* Comparação ordinal que não diferencia maiúsculas de minúsculas. Esse objeto [StringComparer](xref:System.StringComparer) é retornado pela propriedade [StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase).

### <a name="arraysort-and-arraybinarysearch"></a>Array.Sort e Array.BinarySearch

Interpretação padrão: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).

Ao armazenar quaisquer dados em uma coleção ou ler dados persistentes de um arquivo ou banco de dados em uma coleção, alternar a cultura atual pode invalidar as invariáveis na coleção. O método [Array.BinarySearch](xref:System.Array.BinarySearch(System.Array,System.Object)) assume que os elementos na matriz a serem pesquisados já estão classificados. Para classificar qualquer elemento de cadeia de caracteres na matriz, o método [Array.Sort](xref:System.Array.Sort(System.Array)) chama o método [String] `Compare` para ordenar os elementos individuais. Usar um comparador que leva em conta a cultura pode ser perigoso se a cultura mudar entre o momento em que a matriz é ordenada e que seu conteúdo é pesquisado. Por exemplo, no código a seguir, o armazenamento e a recuperação operam no comparador que é fornecido implicitamente pela propriedade `Thread.CurrentThread.CurrentCulture`. Se a cultura puder mudar entre as chamadas para `StoreNames` e `DoesNameExist`, e especialmente se os conteúdos da matriz forem mantidos em algum lugar entre as duas chamadas de método, a pesquisa binária poderá falhar. 

```csharp
// Incorrect.
string []storedNames;

public void StoreNames(string [] names)
{
   int index = 0;
   storedNames = new string[names.Length];

   foreach (string name in names)
   {
      this.storedNames[index++] = name;
   }

   Array.Sort(names); // Line A.
}

public bool DoesNameExist(string name)
{
   return (Array.BinarySearch(this.storedNames, name) >= 0);  // Line B.
}
```

```vb
' Incorrect.
Dim storedNames() As String

Public Sub StoreNames(names() As String)
   Dim index As Integer = 0
   ReDim storedNames(names.Length - 1)

   For Each name As String In names
      Me.storedNames(index) = name
      index+= 1
   Next

   Array.Sort(names)          ' Line A.
End Sub

Public Function DoesNameExist(name As String) As Boolean
   Return Array.BinarySearch(Me.storedNames, name) >= 0      ' Line B.
End Function
```

Uma variação recomendada é exibida no exemplo a seguir, que usa o mesmo método de comparação (que não leva em conta a cultura) ordinal para classificar e pesquisar a matriz. O código de alteração é refletido nas linhas rotuladas como `Line A` e `Line B` nos dois exemplos.

```csharp
// Correct.
string []storedNames;

public void StoreNames(string [] names)
{
   int index = 0;
   storedNames = new string[names.Length];

   foreach (string name in names)
   {
      this.storedNames[index++] = name;
   }

   Array.Sort(names, StringComparer.Ordinal);  // Line A.
}

public bool DoesNameExist(string name)
{
   return (Array.BinarySearch(this.storedNames, name, StringComparer.Ordinal) >= 0);  // Line B.
}
```

```vb
' Correct.
Dim storedNames() As String

Public Sub StoreNames(names() As String)
   Dim index As Integer = 0
   ReDim storedNames(names.Length - 1)

   For Each name As String In names
      Me.storedNames(index) = name
      index+= 1
   Next

   Array.Sort(names, StringComparer.Ordinal)           ' Line A.
End Sub

Public Function DoesNameExist(name As String) As Boolean
   Return Array.BinarySearch(Me.storedNames, name, StringComparer.Ordinal) >= 0      ' Line B.
End Function
```

Se esses dados forem mantidos e movidos entre as culturas e a classificação for usada para apresentar esses dados para o usuário, você pode considerar usar `StringComparison.InvariantCulture`, que opera linguisticamente para a melhor saída do usuário, mas não é afetado pelas alterações na cultura. O exemplo a seguir modifica os dois exemplos anteriores para usar a cultura invariável para classificar e pesquisar a matriz.

```csharp
// Correct.
string []storedNames;

public void StoreNames(string [] names)
{
   int index = 0;
   storedNames = new string[names.Length];

   foreach (string name in names)
   {
      this.storedNames[index++] = name;
   }

   Array.Sort(names, StringComparer.InvariantCulture);  // Line A.
}

public bool DoesNameExist(string name)
{
   return (Array.BinarySearch(this.storedNames, name, StringComparer.InvariantCulture) >= 0);  // Line B.
}
```

```vb
' Correct.
Dim storedNames() As String

Public Sub StoreNames(names() As String)
   Dim index As Integer = 0
   ReDim storedNames(names.Length - 1)

   For Each name As String In names
      Me.storedNames(index) = name
      index+= 1
   Next

   Array.Sort(names, StringComparer.InvariantCulture)           ' Line A.
End Sub

Public Function DoesNameExist(name As String) As Boolean
   Return Array.BinarySearch(Me.storedNames, name, StringComparer.InvariantCulture) >= 0      ' Line B.
End Function
```

### <a name="collections-example-hashtable-constructor"></a>Exemplo de Coleções: Construtor da Tabela de Hash

As cadeias de caracteres de hash fornecem um segundo exemplo de uma operação que é afetada pela maneira como as cadeias de caracteres são comparadas. 

O exemplo a seguir instancia um objeto [Hashtable](xref:System.Collections.Hashtable) passando para ele o objeto [StringComparer](xref:System.StringComparer) que é retornado pela propriedade [StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase). Como uma classe [StringComparer](xref:System.StringComparer) que é derivada de [StringComparer](xref:System.StringComparer) implementa a interface [IEqualityComparer](xref:System.Collections.IEqualityComparer), seu método [GetHashCode](xref:System.Collections.IEqualityComparer) é usado para calcular o código hash das cadeias de caracteres na tabela de hash.

```csharp
const int initialTableCapacity = 100;
Hashtable h;

public void PopulateFileTable(string directory)
{
   h = new Hashtable(initialTableCapacity, 
                     StringComparer.OrdinalIgnoreCase);

   foreach (string file in Directory.GetFiles(directory))
         h.Add(file, File.GetCreationTime(file));
}

public void PrintCreationTime(string targetFile)
{
   Object dt = h[targetFile];
   if (dt != null)
   {
      Console.WriteLine("File {0} was created at time {1}.",
         targetFile, 
         (DateTime) dt);
   }
   else
   {
      Console.WriteLine("File {0} does not exist.", targetFile);
   }
}
```

```vb
Const initialTableCapacity As Integer = 100
Dim h As Hashtable

Public Sub PopulateFileTable(dir As String)
   h = New Hashtable(initialTableCapacity, _
                     StringComparer.OrdinalIgnoreCase)

   For Each filename As String In Directory.GetFiles(dir)
      h.Add(filename, File.GetCreationTime(filename))
   Next                        
End Sub

Public Sub PrintCreationTime(targetFile As String)
   Dim dt As Object = h(targetFile)
   If dt IsNot Nothing Then
      Console.WriteLine("File {0} was created at {1}.", _
         targetFile, _
         CDate(dt))
   Else
      Console.WriteLine("File {0} does not exist.", targetFile)
   End If
End Sub  
```

## <a name="displaying-and-persisting-formatted-data"></a>Exibição e persistência de dados formatados

Quando você exibir dados que não são de cadeias de caracteres como números e datas e horas para os usuários, formate-os usando as configurações culturais do usuário. Por padrão, o método [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) e os métodos `ToString` dos tipos numéricos e dos tipos de data e hora usam a cultura do thread atual para as operações de formatação. Para especificar explicitamente que o método de formatação deve usar a cultura atual, você pode chamar uma sobrecarga de um método de formatação que tenha um parâmetro de provedor, como [String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) ou [DateTime.ToString(IFormatProvider)](xref:System.DateTime.ToString(System.IFormatProvider)) e passar para ela a propriedade [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture). 

Você pode manter os dados que não são de cadeias de caracteres como dados binários ou como dados formatados. Se optar por salvá-los como dados formatados, você deve chamar uma sobrecarga de método de formatação que inclua um parâmetro *provider* e passar para ele a propriedade [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture). A cultura invariável fornece um formato consistente para os dados formatados que é independente da cultura e do computador. Em contraste, dados persistentes que são formatados usando culturas diferentes da cultura invariável têm várias limitações: 

* É provável que os dados não sejam utilizáveis se forem recuperados em um sistema que tem uma cultura diferente ou se o usuário do sistema atual alterar a cultura atual e tentar recuperar os dados. 

* As propriedades de uma cultura em um computador específico podem ser diferentes dos valores padrão. A qualquer momento, um usuário pode personalizar as configurações de exibição que levam em conta a cultura. Devido a isso, os dados formatados que são salvos em um sistema podem não ser legíveis após o usuário personalizar as configurações culturais. É provável que a portabilidade dos dados formatados entre computadores seja ainda mais limitada. 

* Os padrões internacionais, regionais ou nacionais que controlam a formatação de números ou datas e horas são alterados ao longo do tempo e essas alterações são incorporadas nas atualizações do sistema operacional. Quando as convenções de formatação mudam, os dados que foram formatados usando as convenções anteriores podem se tornar ilegíveis. 

O exemplo a seguir ilustra a portabilidade limitada resultante do uso da formatação que leva em conta a cultura para manter os dados. O exemplo salva uma matriz de valores de data e hora em um arquivo. Eles são formatados usando as convenções da cultura do inglês (Estados Unidos). Depois que o aplicativo altera a cultura do thread atual para francês (Suíça), ele tenta ler os valores salvos usando as convenções de formatação da cultura atual. A tentativa de ler dois dos itens de dados gera uma exceção [FormatException](xref:System.FormatException) e a matriz de datas agora contém dois elementos incorretos que são iguais a [MinValue](xref:System.DateTime.MinValue). 

```csharp
using System;
using System.Globalization;
using System.IO;
using System.Text;
using System.Threading;

public class Example
{
   private static string filename = @".\dates.dat";

   public static void Main()
   {
      DateTime[] dates = { new DateTime(1758, 5, 6, 21, 26, 0), 
                           new DateTime(1818, 5, 5, 7, 19, 0), 
                           new DateTime(1870, 4, 22, 23, 54, 0),  
                           new DateTime(1890, 9, 8, 6, 47, 0), 
                           new DateTime(1905, 2, 18, 15, 12, 0) }; 
      // Write the data to a file using the current culture.
      WriteData(dates);
      // Change the current culture.
      Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture("fr-CH");
      // Read the data using the current culture.
      DateTime[] newDates = ReadData();
      foreach (var newDate in newDates)
         Console.WriteLine(newDate.ToString("g"));
   }

   private static void WriteData(DateTime[] dates) 
   {
      StreamWriter sw = new StreamWriter(filename, false, Encoding.UTF8);    
      for (int ctr = 0; ctr < dates.Length; ctr++) {
         sw.Write("{0}", dates[ctr].ToString("g", CultureInfo.CurrentCulture));
         if (ctr < dates.Length - 1) sw.Write("|");   
      }      
      sw.Close();
   }

   private static DateTime[] ReadData() 
   {
      bool exceptionOccurred = false;

      // Read file contents as a single string, then split it.
      StreamReader sr = new StreamReader(filename, Encoding.UTF8);
      string output = sr.ReadToEnd();
      sr.Close();   

      string[] values = output.Split( new char[] { '|' } );
      DateTime[] newDates = new DateTime[values.Length]; 
      for (int ctr = 0; ctr < values.Length; ctr++) {
         try {
            newDates[ctr] = DateTime.Parse(values[ctr], CultureInfo.CurrentCulture);
         }
         catch (FormatException) {
            Console.WriteLine("Failed to parse {0}", values[ctr]);
            exceptionOccurred = true;
         }
      }      
      if (exceptionOccurred) Console.WriteLine();
      return newDates;
   }
}
// The example displays the following output:
//       Failed to parse 4/22/1870 11:54 PM
//       Failed to parse 2/18/1905 3:12 PM
//       
//       05.06.1758 21:26
//       05.05.1818 07:19
//       01.01.0001 00:00
//       09.08.1890 06:47
//       01.01.0001 00:00
//       01.01.0001 00:00
```

```vb
Imports System.Globalization
Imports System.IO
Imports System.Text
Imports System.Threading

Module Example
   Private filename As String = ".\dates.dat"

   Public Sub Main()
      Dim dates() As Date = { #5/6/1758 9:26PM#, #5/5/1818 7:19AM#, _ 
                              #4/22/1870 11:54PM#, #9/8/1890 6:47AM#, _ 
                              #2/18/1905 3:12PM# }
      ' Write the data to a file using the current culture.
      WriteData(dates)
      ' Change the current culture.
      Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture("fr-CH")
      ' Read the data using the current culture.
      Dim newDates() As Date = ReadData()
      For Each newDate In newDates
         Console.WriteLine(newDate.ToString("g"))
      Next
   End Sub

   Private Sub WriteData(dates() As Date)
      Dim sw As New StreamWriter(filename, False, Encoding.Utf8)    
      For ctr As Integer = 0 To dates.Length - 1
         sw.Write("{0}", dates(ctr).ToString("g", CultureInfo.CurrentCulture))
         If ctr < dates.Length - 1 Then sw.Write("|")   
      Next      
      sw.Close()
   End Sub

   Private Function ReadData() As Date()
      Dim exceptionOccurred As Boolean = False

      ' Read file contents as a single string, then split it.
      Dim sr As New StreamReader(filename, Encoding.Utf8)
      Dim output As String = sr.ReadToEnd()
      sr.Close()   

      Dim values() As String = output.Split( {"|"c } )
      Dim newDates(values.Length - 1) As Date 
      For ctr As Integer = 0 To values.Length - 1
         Try
            newDates(ctr) = DateTime.Parse(values(ctr), CultureInfo.CurrentCulture)
         Catch e As FormatException
            Console.WriteLine("Failed to parse {0}", values(ctr))
            exceptionOccurred = True
         End Try
      Next      
      If exceptionOccurred Then Console.WriteLine()
      Return newDates
   End Function
End Module
' The example displays the following output:
'       Failed to parse 4/22/1870 11:54 PM
'       Failed to parse 2/18/1905 3:12 PM
'       
'       05.06.1758 21:26
'       05.05.1818 07:19
'       01.01.0001 00:00
'       09.08.1890 06:47
'       01.01.0001 00:00
'       01.01.0001 00:00
'
```

No entanto, se você substituir a propriedade [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture) por [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) nas chamadas para [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) e [DateTime.Parse(String, IFormatProvider)](xref:System.DateTime.Parse(System.String,System.IFormatProvider)), os dados de data e hora mantidos serão restaurados com êxito, como a saída a seguir mostra.

```
// 06.05.1758 21:26
// 05.05.1818 07:19
// 22.04.1870 23:54
// 08.09.1890 06:47
// 18.02.1905 15:12
```

## <a name="see-also"></a>Consulte também

[Manipulação de cadeias de caracteres](manipulating-strings.md)



<!--HONumber=Nov16_HO1-->


