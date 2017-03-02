---
title: "Quantificadores em expressões regulares"
description: "Quantificadores em expressões regulares"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 8e5124c4-20b5-4c57-ab68-301d1d7311c4
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: cd47cc351fb926bcf444bdcbd12f3cd61d9fb327
ms.lasthandoff: 03/02/2017

---

# <a name="quantifiers-in-regular-expressions"></a>Quantificadores em expressões regulares

Os quantificadores especificam quantas instâncias de um caractere, grupo ou classe de caracteres devem estar presentes na entrada para encontrar uma correspondência. A tabela a seguir lista os quantificadores tem suporte no .NET.

Quantificador Greedy | Quantificador lento | Descrição
----------------- | --------------- | ----------- 
**\*** | **\*?** | Corresponder a zero ou mais vezes.
**+** | **+?** | Corresponder a um ou mais vezes.
**?** | **??** | Corresponder a zero ou uma vez.
**{**_n_**}** | **{**_n_**}?** | Corresponder exatamente a n vezes.
**{**_n_**,}** | **{**_n_**,}?** | Corresponder a pelo menos n vezes.
**{**_n_**,**_m_**}** | **{**_n_**,**_m_**}?** | Corresponder de n a m vezes.
 
As quantidades *n* e *m* são constantes inteiras. Normalmente, os quantificadores são Greedy; eles fazem com que o mecanismo de expressões regulares corresponda a quantas ocorrências de padrões determinados forem possíveis. Acrescentar o caractere `?` a um quantificador o torna lento; faz com que o mecanismo de expressões regulares corresponda ao mínimo de ocorrências possíveis. Para obter uma descrição completa da diferença entre quantificadores Greedy e lentos, consulte a seção [Quantificadores Greedy e lentos](#greedy-and-lazy-quantifiers) mais adiante neste tópico.

> [!IMPORTANT]
> O aninhamento de quantificadores (por exemplo, como o padrão de expressão regular `(a*)*` faz) pode aumentar o número de comparações que o mecanismo de expressões regulares deve executar, como uma função exponencial do número de caracteres na cadeia de caracteres de entrada. Para obter mais informações sobre esse comportamento e suas soluções alternativas, consulte [Retrocesso em expressões regulares](backtracking.md).

## <a name="regular-expression-quantifiers"></a>Quantificadores de expressões regulares

As seções a seguir listam os quantificadores com suporte nas expressões regulares no .NET. 

> [!NOTE]
> Se os caracteres \*, +, ?, { e } forem encontrados em um padrão de expressão regular, o mecanismo de expressões regulares vai interpretá-los como quantificadores ou parte de constructos de quantificador, exceto se estiverem incluídos em uma [classe de caracteres](classes.md). Para interpretá-los como caracteres literais fora de uma classe de caracteres, você precisa fazer o escape, antecedendo-os com uma barra invertida. Por exemplo, a cadeia de caracteres `\*` em um padrão de expressão regular é interpretada como um caractere asterisco (“*”) integral.

### <a name="match-zero-or-more-times-"></a>Corresponder a zero ou mais vezes: \*

O quantificador \* corresponde ao elemento anterior zero ou mais vezes. É equivalente ao quantificador **{0,}**. **\*** é um quantificador Greedy cujo equivalente lento é **\*?**.

O exemplo a seguir ilustra essa expressão regular. Dentre os nove dígitos na cadeia de caracteres de entrada, cinco correspondem ao padrão e quatro (`95`, `929`, `9129` e `9919`) não.

```csharp
string pattern = @"\b91*9*\b";   
string input = "99 95 919 929 9119 9219 999 9919 91119";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

// The example displays the following output:   
//       '99' found at position 0.
//       '919' found at position 6.
//       '9119' found at position 14.
//       '999' found at position 24.
//       '91119' found at position 33.
```

```vb
Dim pattern As String = "\b91*9*\b"   
Dim input As String = "99 95 919 929 9119 9219 999 9919 91119"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next     
' The example displays the following output:   
'       '99' found at position 0.
'       '919' found at position 6.
'       '9119' found at position 14.
'       '999' found at position 24.
'       '91119' found at position 33.
```

O padrão de expressão regular é definido como mostra a tabela a seguir.

Padrão | Descrição
------- | ----------- 
`\b` | Iniciar em um limite de palavra.
`91*` | Corresponder a “9” seguido por zero ou mais caracteres “1”.
`9*` | Corresponder a zero ou mais caracteres “9”.
`\b` | Terminar em um limite de palavra.
 
### <a name="match-one-or-more-times-"></a>Corresponder a um ou mais vezes: +

O quantificador **+** corresponde ao elemento anterior uma ou mais vezes. É equivalente a **{1,}**. **+** é um quantificador Greedy cujo equivalente lento é **+?**.

Por exemplo, a expressão regular `\ban+\w*?\b` tenta corresponder a palavras inteiras que começam com a letra `a` seguidas por uma ou mais instâncias da letra `n`. O exemplo a seguir ilustra essa expressão regular. A expressão regular corresponde às palavras `an`, `annual`, `announcement` e `antique`, e não correspondem corretamente a `autumn` e `all`.

```csharp
string pattern = @"\ban+\w*?\b";

string input = "Autumn is a great time for an annual announcement to all antique collectors.";
foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

// The example displays the following output:   
//       'an' found at position 27.
//       'annual' found at position 30.
//       'announcement' found at position 37.
//       'antique' found at position 57.      
```

```vb
Dim pattern As String = "\ban+\w*?\b"

Dim input As String = "Autumn is a great time for an annual announcement to all antique collectors."
For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next   
' The example displays the following output:   
'       'an' found at position 27.
'       'annual' found at position 30.
'       'announcement' found at position 37.
'       'antique' found at position 57. 
```

O padrão de expressão regular é definido como mostra a tabela a seguir.

Padrão | Descrição
------- | ----------- 
`\b` | Iniciar em um limite de palavra.
`an+` | Corresponder a um “a” seguido por um ou mais caracteres “n”. 
`\w*?` | Corresponder a um caractere de palavra zero ou mais vezes, mas o menor número de vezes possível.
`\b` | Terminar em um limite de palavra.
 
### <a name="match-zero-or-one-time-"></a>Corresponder a zero ou uma vez: ?

O quantificador **?** corresponde ao elemento anterior zero ou uma vez. É equivalente **{0,1}**. **?** é um quantificador Greedy cujo equivalente lento é **??**.

Por exemplo, a expressão regular `\ban?\b` tenta corresponder a palavras inteiras que começam com a letra `a` seguidas por zero ou uma instância da letra `n`. Em outras palavras, ele tenta corresponder às palavras `a` e `an`. O exemplo a seguir ilustra essa expressão regular.

```csharp
string pattern = @"\ban?\b";
string input = "An amiable animal with a large snount and an animated nose.";
foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

// The example displays the following output:   
//        'An' found at position 0.
//        'a' found at position 23.
//        'an' found at position 42.
```

```vb
Dim pattern As String = "\ban?\b"
Dim input As String = "An amiable animal with a large snount and an animated nose."
For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next  
' The example displays the following output:   
'       'An' found at position 0.
'       'a' found at position 23.
'       'an' found at position 42.
```

O padrão de expressão regular é definido como mostra a tabela a seguir.

Padrão | Descrição
------- | ----------- 
`\b` | Iniciar em um limite de palavra.
`an?` | Corresponder a um “a” seguido por zero ou um caractere “n”. 
`\b` | Terminar em um limite de palavra.
 
### <a name="match-exactly-n-times-n"></a>Corresponder exatamente a n vezes: {n}

O quantificador **{**_n_**}** corresponde ao elemento anterior exatamente *n* vezes, em que *n* é qualquer inteiro. **{**_n_**}** é um quantificador Greedy cujo equivalente lento é **{**_n_**}?**.

Por exemplo, a expressão regular `\b\d+\,\d{3}\b` tenta corresponder a um limite de palavra seguido por um ou mais dígitos decimais seguidos por três dígitos decimais seguidos por um limite de palavra. O exemplo a seguir ilustra essa expressão regular. 

```csharp
string pattern = @"\b\d+\,\d{3}\b";
string input = "Sales totaled 103,524 million in January, " + 
                      "106,971 million in February, but only " + 
                      "943 million in March.";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:   
//        '103,524' found at position 14.
//        '106,971' found at position 45.
```

```vb
Dim pattern As String = "\b\d+\,\d{3}\b"
Dim input As String = "Sales totaled 103,524 million in January, " + _
                      "106,971 million in February, but only " + _
                      "943 million in March."
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next     
' The example displays the following output:   
'       '103,524' found at position 14.
'       '106,971' found at position 45.
```

O padrão de expressão regular é definido como mostra a tabela a seguir.

Padrão | Descrição
------- | ----------- 
`\b` | Iniciar em um limite de palavra.
`\d+` | Corresponde a um ou mais dígitos decimais. 
`\,` | Corresponder a um caractere de vírgula.
`\d{3}` | Corresponder a três dígitos decimais.
`\b` | Terminar em um limite de palavra.
 
### <a name="match-at-least-n-times-n"></a>Corresponder a pelo menos n vezes: {n,}

O quantificador **{**_n_**,}** corresponde ao elemento anterior pelo menos *n* vezes, em que *n* é qualquer inteiro. **{**_n_**,}** é um quantificador Greedy cujo equivalente lento é **{**_n_**}?**.

Por exemplo, a expressão regular `\b\d{2,}\b\D+` tenta corresponder a um limite de palavra seguido por pelo menos dois dígitos seguidos por um limite de palavra e um caractere não dígito. O exemplo a seguir ilustra essa expressão regular. A expressão regular não corresponde à frase “7 dias” porque contém apenas um dígito decimal, mas corresponde com êxito às frases “10 semanas e 300 anos”.

```csharp
string pattern = @"\b\d{2,}\b\D+";   
string input = "7 days, 10 weeks, 300 years";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        '10 weeks, ' found at position 8.
// 
``` 

```vb
Dim pattern As String = "\b\d{2,}\b\D+"  
 Dim input As String = "7 days, 10 weeks, 300 years"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       '10 weeks, ' found at position 8.
'       '300 years' found at position 18.
      '300 years' found at position 18.
```

O padrão de expressão regular é definido como mostra a tabela a seguir.

Padrão | Descrição
------- | ----------- 
`\b` | Iniciar em um limite de palavra.
`\d{2,}` | Corresponder a pelo menos dois dígitos decimais. 
`\b` | Corresponder a um limite de palavra.
`\D+` | Corresponder a pelo menos uma casa não decimal.
 
### <a name="match-between-n-and-m-times-nm"></a>Corresponder entre n e m vezes: {n,m}

O quantificador **{**_n_**,**_m_**}** corresponde ao elemento anterior pelo menos *n* vezes, mas não mais de *m* vezes, em que *n* e *m* são inteiros. **{**_n_**,**_m_**}** é um quantificador Greedy cujo equivalente lento é **{**_n_**,**_m_**}?**.

No exemplo a seguir, a expressão regular `(00\s){2,4}` tenta corresponder a entre duas e quatro ocorrências de dois dígitos zero seguidos por um espaço. Observe que a parte final da cadeia de caracteres de entrada inclui esse padrão de cinco vezes em vez de no máximo quatro. No entanto, apenas a parte inicial dessa subcadeia de caracteres (até o espaço e o quinto par de zeros) corresponde ao padrão de expressão regular.

```csharp
string pattern = @"(00\s){2,4}";
string input = "0x00 FF 00 00 18 17 FF 00 00 00 21 00 00 00 00 00";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        '00 00 ' found at position 8.
//        '00 00 00 ' found at position 23.
//        '00 00 00 00 ' found at position 35.
```

```vb
Dim pattern As String = "(00\s){2,4}"
Dim input As String = "0x00 FF 00 00 18 17 FF 00 00 00 21 00 00 00 00 00"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       '00 00 ' found at position 8.
'       '00 00 00 ' found at position 23.
'       '00 00 00 00 ' found at position 35.
```

### <a name="match-zero-or-more-times-lazy-match-"></a>Corresponder a zero ou mais vezes (correspondência lenta): \*?

O quantificador **\*?** corresponde ao elemento anterior zero ou mais vezes, mas o menor número de vezes possível. É a contraparte lenta do quantificador Greedy **\***.

No exemplo a seguir, a expressão regular `\b\w*?oo\w*?\b` corresponde a todas as palavras que contêm a cadeia de caracteres `oo`. 

```csharp
 string pattern = @"\b\w*?oo\w*?\b";
 string input = "woof root root rob oof woo woe";
 foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
    Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

 //  The example displays the following output:
//        'woof' found at position 0.
//        'root' found at position 5.
//        'root' found at position 10.
//        'oof' found at position 19.
//        'woo' found at position 23.
```

```vb
Dim pattern As String = "\b\w*?oo\w*?\b"
 Dim input As String = "woof root root rob oof woo woe"
 For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
    Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
 Next 
 ' The example displays the following output:
'       'woof' found at position 0.
'       'root' found at position 5.
'       'root' found at position 10.
'       'oof' found at position 19.
'       'woo' found at position 23.
```

O padrão de expressão regular é definido como mostra a tabela a seguir.

Padrão | Descrição
------- | ----------- 
`\b` | Iniciar em um limite de palavra.
`\w*?` | Corresponder a zero ou mais caracteres de palavra, mas o menor número de caracteres possível. 
`oo` | Corresponder à cadeia de caracteres “oo”.
`\w*?` | Corresponder a zero ou mais caracteres de palavra, mas o menor número de caracteres possível.
`\b` | Terminar em um limite de palavra.
 
### <a name="match-one-or-more-times-lazy-match-"></a>Corresponder a uma ou mais vezes (correspondência lenta): +?

O quantificador **+?** corresponde ao elemento anterior uma ou mais vezes, mas o menor número de vezes possível. É a contraparte lenta do quantificador Greedy **+**.

Por exemplo, a expressão regular `\b\w+?\b` corresponde a um ou mais caracteres separados por limites de palavra. O exemplo a seguir ilustra essa expressão regular.

```csharp
string pattern = @"\b\w+?\b";
string input = "Aa Bb Cc Dd Ee Ff";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        'Aa' found at position 0.
//        'Bb' found at position 3.
//        'Cc' found at position 6.
//        'Dd' found at position 9.
//        'Ee' found at position 12.
//        'Ff' found at position 15.
```

```vb
Dim pattern As String = "\b\w+?\b"
 Dim input As String = "Aa Bb Cc Dd Ee Ff"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       'Aa' found at position 0.
'       'Bb' found at position 3.
'       'Cc' found at position 6.
'       'Dd' found at position 9.
'       'Ee' found at position 12.
'       'Ff' found at position 15.
```

### <a name="match-zero-or-one-time-lazy-match-"></a>Corresponder a zero ou uma vez (correspondência lenta): ??

O quantificador **??** corresponde ao elemento anterior zero ou uma vez, mas o menor número de vezes possível. É a contraparte lenta do quantificador Greedy **?**.

Por exemplo, a expressão regular `^\s*(System.)??Console.Write(Line)??\(??` tenta corresponder às cadeias de caracteres “Console.Write” ou “Console.WriteLine”. A cadeia de caracteres também pode incluir "System." antes de “Console” e pode ser seguida por um parêntese de abertura. A cadeia de caracteres deve estar no início de uma linha, embora possa ser antecedida por espaço em branco. O exemplo a seguir ilustra essa expressão regular.

```csharp
string pattern = @"^\s*(System.)??Console.Write(Line)??\(??";
string input = "System.Console.WriteLine(\"Hello!\")\n" + 
                      "Console.Write(\"Hello!\")\n" + 
                      "Console.WriteLine(\"Hello!\")\n" + 
                      "Console.ReadLine()\n" + 
                      "   Console.WriteLine";
foreach (Match match in Regex.Matches(input, pattern, 
                                      RegexOptions.IgnorePatternWhitespace | 
                                      RegexOptions.IgnoreCase | 
                                      RegexOptions.Multiline))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        'System.Console.Write' found at position 0.
//        'Console.Write' found at position 36.
//        'Console.Write' found at position 61.
//        '   Console.Write' found at position 110.
```

```vb
Dim pattern As String = "^\s*(System.)??Console.Write(Line)??\(??"
Dim input As String = "System.Console.WriteLine(""Hello!"")" + vbCrLf + _
                      "Console.Write(""Hello!"")" + vbCrLf + _
                      "Console.WriteLine(""Hello!"")" + vbCrLf + _
                      "Console.ReadLine()" + vbCrLf + _
                      "   Console.WriteLine"
For Each match As Match In Regex.Matches(input, pattern, _
                                         RegexOptions.IgnorePatternWhitespace Or RegexOptions.IgnoreCase Or RegexOptions.MultiLine)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       'System.Console.Write' found at position 0.
'       'Console.Write' found at position 36.
'       'Console.Write' found at position 61.
'       '   Console.Write' found at position 110.
```

O padrão de expressão regular é definido como mostra a tabela a seguir.

Padrão | Descrição
------- | ----------- 
`^` | Corresponder ao início do fluxo de entrada.
`\s*` | Corresponder a zero ou mais caracteres de espaço em branco.
`(System.)??` | Corresponde a zero ou uma ocorrência da cadeia de caracteres “System.”.
`Console.Write` | Corresponder à cadeia de caracteres “Console.Write”.
`(Line)??` | Corresponde a zero ou uma ocorrência da cadeia de caracteres “Line”.
`\(??` | Corresponder a zero ou uma ocorrência do parêntese de abertura.
 
### <a name="match-exactly-n-times-lazy-match-n"></a>Corresponder exatamente a n vezes (correspondência lenta): {n}?

O quantificador **{**_n_**}?** corresponde ao elemento anterior exatamente *n* vezes, em que *n* é qualquer inteiro. É a contraparte lenta do quantificador Greedy **{**_n_**}+**.

No exemplo a seguir, a expressão regular `\b(\w{3,}?\.){2}?\w{3,}?\b` é usada para identificar um endereço de site. Observe que corresponde a “www.microsoft.com” e “msdn.microsoft.com”, mas não corresponde a “mywebsite” ou “mycompany.com”.

```csharp
string pattern = @"\b(\w{3,}?\.){2}?\w{3,}?\b";
string input = "www.microsoft.com msdn.microsoft.com mywebsite mycompany.com";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        'www.microsoft.com' found at position 0.
//        'msdn.microsoft.com' found at position 18.
```

```vb
Dim pattern As String = "\b(\w{3,}?\.){2}?\w{3,}?\b"
 Dim input As String = "www.microsoft.com msdn.microsoft.com mywebsite mycompany.com"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next     
' The example displays the following output:
'       'www.microsoft.com' found at position 0.
'       'msdn.microsoft.com' found at position 18.
```

O padrão de expressão regular é definido como mostra a tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Iniciar em um limite de palavra.
`(\w{3,}?\.)` | Corresponder a pelo menos três caracteres de palavra, mas o menor número de caracteres possível, seguido por um caractere de ponto. Este é o primeiro grupo de captura.
`(\w{3,}?\.){2}?` | Corresponder ao padrão no primeiro grupo duas vezes, mas o menor número de vezes possível.
`\b` | Termina a correspondência em um limite de palavra.
 
### <a name="match-at-least-n-times-lazy-match-n"></a>Corresponder a pelo menos n vezes (correspondência lenta): {n,}?

O quantificador **{**_n_**,}?** corresponde ao elemento anterior pelo menos *n* vezes, em que *n* é qualquer número inteiro, mas o menor número de vezes possível. É a contraparte lenta do quantificador Greedy **{**_n_**,}**.

Consulte o exemplo para o quantificador **{**_n_**}?** na seção anterior, para uma ilustração. A expressão regular nesse exemplo usa o quantificador **{**_n_**,}** para corresponder a uma cadeia de caracteres que tem pelo menos três caracteres seguidos por um ponto.

### <a name="match-between-n-and-m-times-lazy-match-nm"></a>Corresponder entre n e m vezes (correspondência lenta): {n,m}?

O quantificador **{**_n_**,**_m_**}?** corresponde ao elemento anterior entre *n* e *m* vezes, em que *n* e *m* são inteiros, mas o menor número de vezes possível. É a contraparte lenta do quantificador Greedy **{**_n_**,**_m_**}**.

No exemplo a seguir, a expressão regular `\b[A-Z](\w*\s+){1,10}?[.!?]` corresponde a frases que contêm entre uma e dez palavras. Corresponde a todas as frases na cadeia de caracteres de entrada, exceto por uma frase que contém 18 palavras.

```csharp
string pattern = @"\b[A-Z](\w*?\s*?){1,10}[.!?]";
string input = "Hi. I am writing a short note. Its purpose is " + 
                      "to test a regular expression that attempts to find " + 
                      "sentences with ten or fewer words. Most sentences " + 
                      "in this note are short.";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        'Hi.' found at position 0.
//        'I am writing a short note.' found at position 4.
//        'Most sentences in this note are short.' found at position 132.
```

```vb
Dim pattern As String = "\b[A-Z](\w*\s?){1,10}?[.!?]"
Dim input As String = "Hi. I am writing a short note. Its purpose is " + _
                      "to test a regular expression that attempts to find " + _
                      "sentences with ten or fewer words. Most sentences " + _
                      "in this note are short."
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       'Hi.' found at position 0.
'       'I am writing a short note.' found at position 4.
'       'Most sentences in this note are short.' found at position 132.
```

O padrão de expressão regular é definido como mostra a tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Iniciar em um limite de palavra.
`[A-Z]` | Corresponder a um caractere maiúscula de A a Z.
`(\w*\s+)` | Corresponder a zero ou mais caracteres de palavra, seguidos por um ou mais caracteres de espaço em branco. Este é o primeiro grupo de captura.
`{1,10}?` | Corresponder ao padrão anterior entre 1 e 10 vezes, mas o menor número de vezes possível.
`[.!?]` | Corresponder a qualquer um dos caracteres de pontuação “.”, “!” ou “?”.
 
## <a name="greedy-and-lazy-quantifiers"></a>Quantificadores Greedy e lentos

Alguns quantificadores têm duas versões: 

* Uma versão Greedy. 

  Um quantificador Greedy tenta corresponder a um elemento tantas vezes quanto possível. 


* •Uma versão não Greedy (ou lenta). 

 Um quantificador não Greedy tenta corresponder a um elemento o menor número de vezes possível. Você pode transformar um quantificador Greedy em um quantificador lento simplesmente adicionando um **?**.

Considere uma expressão regular simples que se destina a extrair os últimos quatro dígitos de uma cadeia de caracteres de números, como um número de cartão de crédito. A versão da expressão regular que usa o quantificador Greedy **\*** é `\b.*([0-9]{4})\b`. No entanto, se uma cadeia de caracteres contiver dois números, essa expressão regular corresponde aos últimos quatro dígitos do segundo número, como mostra o exemplo a seguir.

```csharp
string greedyPattern = @"\b.*([0-9]{4})\b";
string input1 = "1112223333 3992991999";
foreach (Match match in Regex.Matches(input1, greedyPattern))
   Console.WriteLine("Account ending in ******{0}.", match.Groups[1].Value);

// The example displays the following output:
//       Account ending in ******1999.
```

```vb
Dim greedyPattern As String = "\b.*([0-9]{4})\b"
Dim input1 As String = "1112223333 3992991999"
For Each match As Match In Regex.Matches(input1, greedypattern)
   Console.WriteLine("Account ending in ******{0}.", match.Groups(1).Value)
Next
' The example displays the following output:
'       Account ending in ******1999.
```

A expressão regular não corresponde ao primeiro número porque o quantificador **\*** tenta corresponder ao elemento anterior tantas vezes quanto possível em toda a cadeia de caracteres e encontra sua correspondência no final da cadeia de caracteres.

Esse não é o comportamento desejado. Em vez disso, você pode usar o quantificador lento **\*?** para extrair dígitos de ambos os números, como mostra o exemplo a seguir.

```csharp
string lazyPattern = @"\b.*?([0-9]{4})\b";
string input2 = "1112223333 3992991999";
foreach (Match match in Regex.Matches(input2, lazyPattern))
   Console.WriteLine("Account ending in ******{0}.", match.Groups[1].Value);

// The example displays the following output:
//       Account ending in ******3333.
//       Account ending in ******1999.
```

```vb
Dim lazyPattern As String = "\b.*?([0-9]{4})\b"
Dim input2 As String = "1112223333 3992991999"
For Each match As Match In Regex.Matches(input2, lazypattern)
   Console.WriteLine("Account ending in ******{0}.", match.Groups(1).Value)
Next     
' The example displays the following output:
'       Account ending in ******3333.
'       Account ending in ******1999.
```

Na maioria dos casos, expressões regulares com quantificadores Greedy e lentos retornam as mesmas correspondências. Geralmente retornam resultados diferentes quando são usadas com o metacaractere curinga (**.**), que corresponde a qualquer caractere. 

## <a name="quantifiers-and-empty-matches"></a>Quantificadores e correspondências vazias

Os quantificadores **\***, **+** e **{**_n_**,**_m_**}** e suas contrapartes lentas nunca se repetem depois de uma correspondência vazia quando o número mínimo de capturas foi encontrado. Essa regra impede que quantificadores entrem em loops infinitos em correspondências vazias de subexpressão quando o número máximo de capturas de grupo possíveis é infinito ou quase infinito.

Por exemplo, o código a seguir mostra o resultado de uma chamada para o método [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) com o padrão de expressão regular `(a?)*,` que corresponde a zero ou a um caractere “a” zero ou mais vezes. Observe que o grupo de captura único captura cada “a” bem como [String.Empty](xref:System.String.Empty), mas que não há uma segunda correspondência vazia, porque a primeira correspondência vazia faz com que o quantificador pare de se repetir.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "(a?)*";
      string input = "aaabbb";
      Match match = Regex.Match(input, pattern);
      Console.WriteLine("Match: '{0}' at index {1}", 
                        match.Value, match.Index);
      if (match.Groups.Count > 1) {
         GroupCollection groups = match.Groups;
         for (int grpCtr = 1; grpCtr <= groups.Count - 1; grpCtr++) {
            Console.WriteLine("   Group {0}: '{1}' at index {2}", 
                              grpCtr, 
                              groups[grpCtr].Value,
                              groups[grpCtr].Index);
            int captureCtr = 0;
            foreach (Capture capture in groups[grpCtr].Captures) {
               captureCtr++;
               Console.WriteLine("      Capture {0}: '{1}' at index {2}", 
                                 captureCtr, capture.Value, capture.Index);
            }
         } 
      }   
   }
}
// The example displays the following output:
//       Match: 'aaa' at index 0
//          Group 1: '' at index 3
//             Capture 1: 'a' at index 0
//             Capture 2: 'a' at index 1
//             Capture 3: 'a' at index 2
//             Capture 4: '' at index 3
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(a?)*"
      Dim input As String = "aaabbb"
      Dim match As Match = Regex.Match(input, pattern)
      Console.WriteLine("Match: '{0}' at index {1}", 
                        match.Value, match.Index)
      If match.Groups.Count > 1 Then
         Dim groups As GroupCollection = match.Groups
         For grpCtr As Integer = 1 To groups.Count - 1
            Console.WriteLine("   Group {0}: '{1}' at index {2}", 
                              grpCtr, 
                              groups(grpCtr).Value,
                              groups(grpCtr).Index)
            Dim captureCtr As Integer = 0
            For Each capture As Capture In groups(grpCtr).Captures
               captureCtr += 1
               Console.WriteLine("      Capture {0}: '{1}' at index {2}", 
                                 captureCtr, capture.Value, capture.Index)
            Next
         Next 
      End If   
   End Sub
End Module
' The example displays the following output:
'       Match: 'aaa' at index 0
'          Group 1: '' at index 3
'             Capture 1: 'a' at index 0
'             Capture 2: 'a' at index 1
'             Capture 3: 'a' at index 2
'             Capture 4: '' at index 3
```

Para ver a diferença prática entre um grupo de captura que define um número mínimo e máximo de captura e um que define um número fixo de capturas, considere os padrões de expressão regular `(a\1|(?(1)\1)){0,2}` e `(a\1|(?(1)\1)){2}`. Ambas as expressões regulares consistem em um único grupo de captura, que é definido como mostrado na tabela a seguir. 

Padrão | Descrição
------- | -----------
`(a\1` | Faça qualquer correspondência a “a” juntamente com o valor do primeiro grupo capturado…
`&#124;(?(1)` | … ou teste se o primeiro grupo capturado foi definido. (Observe que o constructo **(?(1)** não define um grupo de captura.)
`\1))` | Se o primeiro grupo capturado existir, faça uma correspondência ao valor. Se o grupo não existir, será correspondente a [String.Empty](xref:System.String.Empty). 
 
A primeira expressão regular tenta corresponder a esse padrão entre zero e duas vezes; a segunda, exatamente duas vezes. Como o primeiro padrão atinge o número mínimo de capturas com a primeira captura de [String.Empty](xref:System.String.Empty), ele nunca se repete para tentar corresponder a `a\1;`; o quantificador `{0,2}` permite apenas correspondências vazias na última iteração. Por outro lado, a segunda expressão regular corresponde a “a” porque avalia `a\1` uma segunda vez; o número mínimo de iterações, 2, força o mecanismo a se repetir após uma correspondência vazia.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern, input;

      pattern = @"(a\1|(?(1)\1)){0,2}";
      input = "aaabbb"; 

      Console.WriteLine("Regex pattern: {0}", pattern);
      Match match = Regex.Match(input, pattern);
      Console.WriteLine("Match: '{0}' at position {1}.", 
                        match.Value, match.Index);
      if (match.Groups.Count > 1) {
         for (int groupCtr = 1; groupCtr <= match.Groups.Count - 1; groupCtr++)
         {
            Group group = match.Groups[groupCtr];         
            Console.WriteLine("   Group: {0}: '{1}' at position {2}.", 
                              groupCtr, group.Value, group.Index);
            int captureCtr = 0;
            foreach (Capture capture in group.Captures) {
               captureCtr++;
               Console.WriteLine("      Capture: {0}: '{1}' at position {2}.", 
                                 captureCtr, capture.Value, capture.Index);
            }   
         }
      }
      Console.WriteLine();

      pattern = @"(a\1|(?(1)\1)){2}";
      Console.WriteLine("Regex pattern: {0}", pattern);
      match = Regex.Match(input, pattern);
         Console.WriteLine("Matched '{0}' at position {1}.", 
                           match.Value, match.Index);
      if (match.Groups.Count > 1) {
         for (int groupCtr = 1; groupCtr <= match.Groups.Count - 1; groupCtr++)
         {
            Group group = match.Groups[groupCtr];         
            Console.WriteLine("   Group: {0}: '{1}' at position {2}.", 
                              groupCtr, group.Value, group.Index);
            int captureCtr = 0;
            foreach (Capture capture in group.Captures) {
               captureCtr++;
               Console.WriteLine("      Capture: {0}: '{1}' at position {2}.", 
                                 captureCtr, capture.Value, capture.Index);
            }   
         }
      }
   }
}
// The example displays the following output:
//       Regex pattern: (a\1|(?(1)\1)){0,2}
//       Match: '' at position 0.
//          Group: 1: '' at position 0.
//             Capture: 1: '' at position 0.
//       
//       Regex pattern: (a\1|(?(1)\1)){2}
//       Matched 'a' at position 0.
//          Group: 1: 'a' at position 0.
//             Capture: 1: '' at position 0.
//             Capture: 2: 'a' at position 0.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern, input As String

      pattern = "(a\1|(?(1)\1)){0,2}"
      input = "aaabbb" 

      Console.WriteLine("Regex pattern: {0}", pattern)
      Dim match As Match = Regex.Match(input, pattern)
      Console.WriteLine("Match: '{0}' at position {1}.", 
                        match.Value, match.Index)
      If match.Groups.Count > 1 Then
         For groupCtr As Integer = 1 To match.Groups.Count - 1
            Dim group As Group = match.Groups(groupCtr)         
            Console.WriteLine("   Group: {0}: '{1}' at position {2}.", 
                              groupCtr, group.Value, group.Index)
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               captureCtr += 1
               Console.WriteLine("      Capture: {0}: '{1}' at position {2}.", 
                                 captureCtr, capture.Value, capture.Index)
            Next   
         Next
      End If
      Console.WriteLine()

      pattern = "(a\1|(?(1)\1)){2}"
      Console.WriteLine("Regex pattern: {0}", pattern)
      match = Regex.Match(input, pattern)
         Console.WriteLine("Matched '{0}' at position {1}.", 
                           match.Value, match.Index)
      If match.Groups.Count > 1 Then
         For groupCtr As Integer = 1 To match.Groups.Count - 1
            Dim group As Group = match.Groups(groupCtr)         
            Console.WriteLine("   Group: {0}: '{1}' at position {2}.", 
                              groupCtr, group.Value, group.Index)
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               captureCtr += 1
               Console.WriteLine("      Capture: {0}: '{1}' at position {2}.", 
                                 captureCtr, capture.Value, capture.Index)
            Next   
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Regex pattern: (a\1|(?(1)\1)){0,2}
'       Match: '' at position 0.
'          Group: 1: '' at position 0.
'             Capture: 1: '' at position 0.
'       
'       Regex pattern: (a\1|(?(1)\1)){2}
'       Matched 'a' at position 0.
'          Group: 1: 'a' at position 0.
'             Capture: 1: '' at position 0.
'             Capture: 2: 'a' at position 0.
```

## <a name="see-also"></a>Consulte também

[Linguagem de expressão regular – referência rápida](quick-ref.md)

[Retrocesso em expressões regulares](backtracking.md)


