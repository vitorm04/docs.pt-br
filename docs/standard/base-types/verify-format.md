---
title: "Como verificar se cadeias de caracteres estão em um formato de email válido"
description: "Como verificar se cadeias de caracteres estão em um formato de email válido"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 6d735520-4059-4754-b34c-d117299d36f1
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: bedd1d281256545776c874a38ccb71ad594467c2

---

# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Como verificar se cadeias de caracteres estão em um formato de email válido

O exemplo a seguir usa uma expressão regular para verificar se uma cadeia de caracteres está no formato de email válido.

## <a name="example"></a>Exemplo

O exemplo define um método `IsValidEmail`, que retornará `true` se a cadeia de caracteres contiver um endereço de email válido e `false` se não contiver, mas não realiza outra ação. 

Para verificar se o endereço de email é válido, o método `IsValidEmail` chama o método [Regex.Replace(String, String, MatchEvaluator)](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.Text.RegularExpressions.MatchEvaluator)) com o padrão da expressão regular `(@)(.+)$` para separar o nome de domínio do endereço de email. O terceiro parâmetro é um delegado [MatchEvaluator](xref:System.Text.RegularExpressions.MatchEvaluator), que representa o método que processa e substitui o texto correspondente. O padrão da expressão regular é interpretado da seguinte maneira. 

Padrão | Descrição
------- | ----------- 
`(@)` | Coincida o caractere @. Este é o primeiro grupo de captura.
`(.+)` | Coincida uma ou mais ocorrências de qualquer caractere. Este é o segundo grupo de captura.
`$` | Encerrar a correspondência ao final da cadeia de caracteres.
 
O nome de domínio com o caractere @ é passado para o método `DomainMapper`, que usa a classe [IdnMapping](xref:System.Globalization.IdnMapping) para converter caracteres Unicode fora do intervalo de caracteres US-ASCII em Punycode. O método também define o sinalizador `invalid` como `true`, caso o método [IdnMapping.GetAscii](xref:System.Globalization.IdnMapping.GetAscii(System.String)) detecte algum caractere inválido no nome de domínio. O método retorna o nome de domínio Punycode precedido pelo símbolo @ para o método `IsValidEmail`. 

Em seguida, o método `IsValidEmail` chama o método [Regex.IsMatch(String, String)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String)) para verificar se o endereço está em conformidade com um padrão de expressão regular. 

O método `IsValidEmail` não realiza a autenticação para validar o endereço de email. Ele simplesmente determina se o formato é válido para um endereço de email. Além disso, o método `IsValidEmail` não verifica se o nome de domínio primário é um nome de domínio válido listado no [IANA Root Zone Database](https://www.iana.org/domains/root/db) (Banco de dados de zona raiz da IANA), o que exigiria uma operação de pesquisa. Em vez disso, a expressão regular apenas verifica se o nome de domínio primário consiste entre dois e vinte e quatro caracteres ASCII, com caracteres alfanuméricos sendo os primeiros e os últimos e o restante dos caracteres sendo alfanuméricos ou um hífen (-). 

```csharp
using System;
using System.Globalization;
using System.Text.RegularExpressions;

public class RegexUtilities
{
   bool invalid = false;

   public bool IsValidEmail(string strIn)
   {
       invalid = false;
       if (String.IsNullOrEmpty(strIn))
          return false;

       // Use IdnMapping class to convert Unicode domain names.
       try {
          strIn = Regex.Replace(strIn, @"(@)(.+)$", this.DomainMapper,
                                RegexOptions.None, TimeSpan.FromMilliseconds(200));
       }
       catch (RegexMatchTimeoutException) {
         return false;
       }

        if (invalid)
           return false;

       // Return true if strIn is in valid e-mail format.
       try {
          return Regex.IsMatch(strIn,
                @"^(?("")("".+?(?<!\\)""@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))" +
                @"(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-\w]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$",
                RegexOptions.IgnoreCase, TimeSpan.FromMilliseconds(250));
       }
       catch (RegexMatchTimeoutException) {
          return false;
       }
   }

   private string DomainMapper(Match match)
   {
      // IdnMapping class with default property values.
      IdnMapping idn = new IdnMapping();

      string domainName = match.Groups[2].Value;
      try {
         domainName = idn.GetAscii(domainName);
      }
      catch (ArgumentException) {
         invalid = true;
      }
      return match.Groups[1].Value + domainName;
   }
}
```

```vb
Imports System.Globalization
Imports System.Text.RegularExpressions

Public Class RegexUtilities
   Dim invalid As Boolean = False

   public Function IsValidEmail(strIn As String) As Boolean
       invalid = False
       If String.IsNullOrEmpty(strIn) Then Return False

       ' Use IdnMapping class to convert Unicode domain names.
       Try
          strIn = Regex.Replace(strIn, "(@)(.+)$", AddressOf Me.DomainMapper, 
                                RegexOptions.None, TimeSpan.FromMilliseconds(200))
       Catch e As RegexMatchTimeoutException
          Return False
       End Try

       If invalid Then Return False

       ' Return true if strIn is in valid e-mail format.
       Try
          Return Regex.IsMatch(strIn,
                 "^(?("")("".+?(?<!\\)""@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))" +
                 "(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-\w]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$",
                 RegexOptions.IgnoreCase, TimeSpan.FromMilliseconds(250))
       Catch e As RegexMatchTimeoutException
          Return False
       End Try  
   End Function

   Private Function DomainMapper(match As Match) As String
      ' IdnMapping class with default property values.
      Dim idn As New IdnMapping()

      Dim domainName As String = match.Groups(2).Value
      Try
         domainName = idn.GetAscii(domainName)
      Catch e As ArgumentException
         invalid = True      
      End Try      
      Return match.Groups(1).Value + domainName
   End Function
End Class
```

Neste exemplo, o padrão de expressão regular `^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-\w]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$` é interpretado como mostrado na tabela a seguir. Observe que a expressão regular é compilada usando o sinalizador [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase).

Padrão | Descrição
------- | ----------- 
`^` | Comece a correspondência no início da cadeia de caracteres.
`(?(")` | Determine se o primeiro caractere é aspas. `(?(")` é o início de um construtor de alternância.
`(?("")("".+?(?<!\\)""@)` | Se o primeiro caractere for aspas, coincida as aspas iniciais seguidas de pelo menos uma ocorrência de qualquer caractere, seguido de uma marca de aspas finais. As aspas finais não devem ser precedidas por um caractere de barra invertida `(\). (?<!` é o início de uma asserção lookbehind negativa de largura zero. A cadeia de caracteres deve terminar com um sinal (@).
`&#124;(([0-9a-z] | Se o primeiro caractere não for aspas, coincida qualquer caractere alfabético de a até z ou de A até Z (a comparação não diferencia maiúsculas de minúsculas) ou qualquer caractere numérico entre 0 e 9.
`(\.(?!\.))` | Se o próximo caractere for um ponto final, coincida com ele. Se ele não for um ponto final, observe o próximo caractere e continue a correspondência. `(?!\.)` é uma asserção lookahead negativa de largura zero que impede dois pontos finais consecutivos de serem exibidos na parte local de um endereço de email.
`&#124;[-!#\$%&'\*\+/=\?\^`\{\}\&#124;~\w] | Se o próximo caractere não for um ponto final, corresponda qualquer caractere da palavra ou um dos seguintes caracteres: -!#$%'*+=?^`{}&#124;~. 
`((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^`\{\}\&#124;~\w])* | Coincida o padrão de alternância (um ponto final seguido de um não ponto final ou um de um número de caracteres) zero ou mais vezes.
`@` | Coincida o caractere @.
`(?<=[0-9a-z])` | Continue a correspondência se o caractere que precede o caractere @ for de A a Z, de a até z ou de 0 a 9. O constructo `(?<=[0-9a-z])` define uma asserção lookbehind positiva de largura zero.
`(?(\[)` | Verifique se o caractere que segue @ é um colchete de abertura.
`(\[(\d{1,3}\.){3}\d{1,3}\])` | Se ele for um colchete de abertura, coincida o colchete de abertura seguido de um endereço IP (quatro conjuntos de um a três dígitos, com cada conjunto separado por um ponto final) e um colchete de fechamento.
`&#124;(([0-9a-z][-\w]*[0-9a-z]*\.)+` | Se o caractere depois de @ não for um colchete de abertura, coincida um caractere alfanumérico com um valor de A até Z, de a até z ou entre 0 e 9, seguido de zero ou mais ocorrências de um caractere de palavra ou um hífen, seguido de zero ou um caractere alfanumérico com um valor de A até Z, de a até z ou entre 0 e 9, seguido de um ponto final. Esse padrão pode ser repetido uma ou mais vezes e deve ser seguido pelo nome de domínio primário. 
`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))` | O nome de domínio primário deve começar e terminar com um caractere alfanumérico (a-z, A-Z e 0-9). Ele também pode incluir de zero a 22 caracteres ASCII que são alfanuméricos ou hifens. 
`$` | Encerrar a correspondência ao final da cadeia de caracteres.
 
Você pode chamar os métodos `IsValidEmail` e `DomainMapper` usando código como o seguinte:

```csharp
public class Application
{
   public static void Main()
   {
      RegexUtilities util = new RegexUtilities();
      string[] emailAddresses = { "david.jones@proseware.com", "d.j@server1.proseware.com",
                                  "jones@ms1.proseware.com", "j.@server1.proseware.com",
                                  "j@proseware.com9", "js#internal@proseware.com",
                                  "j_9@[129.126.118.1]", "j..s@proseware.com",
                                  "js*@proseware.com", "js@proseware..com",
                                  "js@proseware.com9", "j.s@server1.proseware.com",
                                   "\"j\\\"s\\\"\"@proseware.com", "js@contoso.中国" };

      foreach (var emailAddress in emailAddresses) {
         if (util.IsValidEmail(emailAddress))
            Console.WriteLine("Valid: {0}", emailAddress);
         else
            Console.WriteLine("Invalid: {0}", emailAddress);
      }                                            
   }
}
// The example displays the following output:
//       Valid: david.jones@proseware.com
//       Valid: d.j@server1.proseware.com
//       Valid: jones@ms1.proseware.com
//       Invalid: j.@server1.proseware.com
//       Valid: j@proseware.com9
//       Valid: js#internal@proseware.com
//       Valid: j_9@[129.126.118.1]
//       Invalid: j..s@proseware.com
//       Invalid: js*@proseware.com
//       Invalid: js@proseware..com
//       Valid: js@proseware.com9
//       Valid: j.s@server1.proseware.com
//       Valid: "j\"s\""@proseware.com
//       Valid: js@contoso.ä¸­å›½
```

```vb
Public Class Application
   Public Shared Sub Main()
      Dim util As New RegexUtilities()
      Dim emailAddresses() As String = { "david.jones@proseware.com", "d.j@server1.proseware.com", _
                                         "jones@ms1.proseware.com", "j.@server1.proseware.com", _
                                         "j@proseware.com9", "js#internal@proseware.com", _
                                         "j_9@[129.126.118.1]", "j..s@proseware.com", _
                                         "js*@proseware.com", "js@proseware..com", _
                                         "js@proseware.com9", "j.s@server1.proseware.com",
                                         """j\""s\""""@proseware.com", "js@contoso.中国" }

      For Each emailAddress As String In emailAddresses
         If util.IsValidEmail(emailAddress) Then
            Console.WriteLine("Valid: {0}", emailAddress)
         Else
            Console.WriteLine("Invalid: {0}", emailAddress)
         End If      
      Next                                            
   End Sub
End Class
' The example displays the following output:
'       Valid: david.jones@proseware.com
'       Valid: d.j@server1.proseware.com
'       Valid: jones@ms1.proseware.com
'       Invalid: j.@server1.proseware.com
'       Valid: j@proseware.com9
'       Valid: js#internal@proseware.com
'       Valid: j_9@[129.126.118.1]
'       Invalid: j..s@proseware.com
'       Invalid: js*@proseware.com
'       Invalid: js@proseware..com
'       Valid: js@proseware.com9
'       Valid: j.s@server1.proseware.com
'       Valid: "j\"s\""@proseware.com
'       Valid: js@contoso.ä¸­å›½
```

## <a name="see-also"></a>Consulte também

[Expressões regulares do .NET](regular-expressions.md)

[Exemplos de expressões regulares](regex-examples.md)



<!--HONumber=Nov16_HO3-->


