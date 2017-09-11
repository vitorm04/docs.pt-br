---
title: "Práticas recomendadas para expressões regulares"
description: "Práticas recomendadas para expressões regulares"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 096fd614-91bf-4296-be24-12f62b062294
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: cf9c83de791fa4990a991689a26d4bbdd84cfe7d
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="best-practices-for-regular-expressions"></a><span data-ttu-id="f4a99-104">Práticas recomendadas para expressões regulares</span><span class="sxs-lookup"><span data-stu-id="f4a99-104">Best practices for regular expressions</span></span>

<span data-ttu-id="f4a99-105">O mecanismo de expressões regulares no .NET é uma ferramenta poderosa e repleta de recursos que processa o texto com base em correspondências de padrões em vez de em comparar e corresponder o texto literal.</span><span class="sxs-lookup"><span data-stu-id="f4a99-105">The regular expression engine in .NET is a powerful, full-featured tool that processes text based on pattern matches rather than on comparing and matching literal text.</span></span> <span data-ttu-id="f4a99-106">Na maioria dos casos, ele realiza a correspondência de padrões de forma rápida e eficiente.</span><span class="sxs-lookup"><span data-stu-id="f4a99-106">In most cases, it performs pattern matching rapidly and efficiently.</span></span> <span data-ttu-id="f4a99-107">No entanto, em alguns casos, o mecanismo de expressões regulares pode parecer ser muito lento.</span><span class="sxs-lookup"><span data-stu-id="f4a99-107">However, in some cases, the regular expression engine can appear to be very slow.</span></span> <span data-ttu-id="f4a99-108">Em casos extremos, pode até mesmo parecer parar de responder enquanto processa uma entrada relativamente pequena em um período de horas ou até mesmo dias.</span><span class="sxs-lookup"><span data-stu-id="f4a99-108">In extreme cases, it can even appear to stop responding as it processes a relatively small input over the course of hours or even days.</span></span> 

<span data-ttu-id="f4a99-109">Este tópico descreve algumas das práticas recomendadas que os desenvolvedores podem adotar para garantir que as expressões regulares obtenham o máximo de desempenho.</span><span class="sxs-lookup"><span data-stu-id="f4a99-109">This topic outlines some of the best practices that developers can adopt to ensure that their regular expressions achieve optimal performance.</span></span> <span data-ttu-id="f4a99-110">Ele contém as seguintes seções:</span><span class="sxs-lookup"><span data-stu-id="f4a99-110">It contains the following sections:</span></span>

* [<span data-ttu-id="f4a99-111">Considere a fonte de entrada</span><span class="sxs-lookup"><span data-stu-id="f4a99-111">Consider the input source</span></span>](#consider-the-input-source)

* [<span data-ttu-id="f4a99-112">Trate a instanciação de objetos adequadamente</span><span class="sxs-lookup"><span data-stu-id="f4a99-112">Handle object instantiation appropriately</span></span>](#handle-object-instantiation-appropriately)

* [<span data-ttu-id="f4a99-113">Tome conta do retrocesso</span><span class="sxs-lookup"><span data-stu-id="f4a99-113">Take charge of backtracking</span></span>](#take-charge-of-backtracking)

* [<span data-ttu-id="f4a99-114">Use valores de tempo limite</span><span class="sxs-lookup"><span data-stu-id="f4a99-114">Use time-out values</span></span>](#use-time-out-values)

* [<span data-ttu-id="f4a99-115">Capture somente quando necessário</span><span class="sxs-lookup"><span data-stu-id="f4a99-115">Capture only when necessary</span></span>](#capture-only-when-necessary)

* [<span data-ttu-id="f4a99-116">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="f4a99-116">Related topics</span></span>](#related-topics)

## <a name="consider-the-input-source"></a><span data-ttu-id="f4a99-117">Considere a fonte de entrada</span><span class="sxs-lookup"><span data-stu-id="f4a99-117">Consider the input source</span></span>

<span data-ttu-id="f4a99-118">Em geral, as expressões regulares podem aceitar dois tipos de entrada: restrita e não restrita.</span><span class="sxs-lookup"><span data-stu-id="f4a99-118">In general, regular expressions can accept two types of input: constrained or unconstrained.</span></span> <span data-ttu-id="f4a99-119">Uma entrada restrita é o texto proveniente de uma fonte conhecida ou confiável e segue um formato predefinido.</span><span class="sxs-lookup"><span data-stu-id="f4a99-119">Constrained input is text that originates from a known or reliable source and follows a predefined format.</span></span> <span data-ttu-id="f4a99-120">Uma entrada irrestrita é um texto que se origina de uma origem não confiável como um usuário não confiável e não pode seguir um formato predefinido ou esperado.</span><span class="sxs-lookup"><span data-stu-id="f4a99-120">Unconstrained input is text that originates from an unreliable source, such as a web user, and may not follow a predefined or expected format.</span></span>

<span data-ttu-id="f4a99-121">Os padrões de expressões regulares geralmente são escritos para corresponder a entradas válidas.</span><span class="sxs-lookup"><span data-stu-id="f4a99-121">Regular expression patterns are typically written to match valid input.</span></span> <span data-ttu-id="f4a99-122">Ou seja, os desenvolvedores examinam o texto que desejam corresponder e escrevem um padrão de expressão regular que corresponde a ele.</span><span class="sxs-lookup"><span data-stu-id="f4a99-122">That is, developers examine the text that they want to match and then write a regular expression pattern that matches it.</span></span> <span data-ttu-id="f4a99-123">Os desenvolvedores então determinam se esse padrão requer correção ou uma elaboração adicional testando-o com vários itens de entrada válidos.</span><span class="sxs-lookup"><span data-stu-id="f4a99-123">Developers then determine whether this pattern requires correction or further elaboration by testing it with multiple valid input items.</span></span> <span data-ttu-id="f4a99-124">Quando o padrão corresponde a todas as entradas válidas presumidas, é declarado como pronto para produção e pode ser incluído em um aplicativo final.</span><span class="sxs-lookup"><span data-stu-id="f4a99-124">When the pattern matches all presumed valid inputs, it is declared to be production-ready and can be included in a released application.</span></span> <span data-ttu-id="f4a99-125">Isso torna um padrão de expressão regular apropriado para corresponder uma entrada restrita.</span><span class="sxs-lookup"><span data-stu-id="f4a99-125">This makes a regular expression pattern suitable for matching constrained input.</span></span> <span data-ttu-id="f4a99-126">No entanto, ele não o torna adequado para corresponder à entrada sem restrição.</span><span class="sxs-lookup"><span data-stu-id="f4a99-126">However, it does not make it suitable for matching unconstrained input.</span></span>

<span data-ttu-id="f4a99-127">Para corresponder a uma entrada sem restrição, uma expressão regular deve ser capaz de manipular três tipos de texto:</span><span class="sxs-lookup"><span data-stu-id="f4a99-127">To match unconstrained input, a regular expression must be able to efficiently handle three kinds of text:</span></span>

<span data-ttu-id="f4a99-128">• Texto que corresponda ao padrão da expressão regular.</span><span class="sxs-lookup"><span data-stu-id="f4a99-128">• Text that matches the regular expression pattern.</span></span>

<span data-ttu-id="f4a99-129">• Texto que não corresponda ao padrão da expressão regular.</span><span class="sxs-lookup"><span data-stu-id="f4a99-129">• Text that does not match the regular expression pattern.</span></span>

<span data-ttu-id="f4a99-130">• Texto que quase corresponda ao padrão da expressão regular.</span><span class="sxs-lookup"><span data-stu-id="f4a99-130">• Text that nearly matches the regular expression pattern.</span></span>

<span data-ttu-id="f4a99-131">O último tipo de texto é particularmente problemático para uma expressão regular que foi escrita para lidar com entradas restritas.</span><span class="sxs-lookup"><span data-stu-id="f4a99-131">The last text type is especially problematic for a regular expression that has been written to handle constrained input.</span></span> <span data-ttu-id="f4a99-132">Se essa expressão regular também depender de [retrocesso](backtracking.md) abrangente, o mecanismo de expressões regulares poderá gastar um período fora do normal (em alguns casos, muitas horas ou dias) processando texto aparentemente inócuo.</span><span class="sxs-lookup"><span data-stu-id="f4a99-132">If that regular expression also relies on extensive [backtracking](backtracking.md), the regular expression engine can spend an inordinate amount of time (in some cases, many hours or days) processing seemingly innocuous text.</span></span> 

> [!WARNING]
> <span data-ttu-id="f4a99-133">O exemplo a seguir usa uma expressão regular que é propensa a retrocesso excessivo e que pode rejeitar endereços de email válidos.</span><span class="sxs-lookup"><span data-stu-id="f4a99-133">The following example uses a regular expression that is prone to excessive backtracking and that is likely to reject valid email addresses.</span></span> <span data-ttu-id="f4a99-134">Você não deve usá-lo em uma rotina de validação de email.</span><span class="sxs-lookup"><span data-stu-id="f4a99-134">You should not use it in an email validation routine.</span></span> <span data-ttu-id="f4a99-135">Se você desejar uma expressão regular que valida endereços de email, confira [Como verificar se cadeias de caracteres estão em um formato de email válido](verify-format.md).</span><span class="sxs-lookup"><span data-stu-id="f4a99-135">If you would like a regular expression that validates email addresses, see [How to: Verify that strings are in valid email format](verify-format.md).</span></span> 


<span data-ttu-id="f4a99-136">Por exemplo, considere uma expressão regular muito usada, mas extremamente problemática, para validar o alias de um endereço de email.</span><span class="sxs-lookup"><span data-stu-id="f4a99-136">For example, consider a very commonly used but extremely problematic regular expression for validating the alias of an email address.</span></span> <span data-ttu-id="f4a99-137">A expressão regular `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` é escrita para processar o que é considerado um endereço de email válido, o que consiste em um caractere alfanumérico seguido por zero ou mais caracteres que podem ser alfanuméricos, pontos ou hifens.</span><span class="sxs-lookup"><span data-stu-id="f4a99-137">The regular expression `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` is written to process what is considered to be a valid email address, which consists of an alphanumeric character, followed by zero or more characters that can be alphanumeric, periods, or hyphens.</span></span> <span data-ttu-id="f4a99-138">A expressão regular deve terminar com um caractere alfanumérico.</span><span class="sxs-lookup"><span data-stu-id="f4a99-138">The regular expression must end with an alphanumeric character.</span></span> <span data-ttu-id="f4a99-139">No entanto, como mostra o exemplo a seguir, embora esta expressão regular manipule entradas válidas facilmente, seu desempenho é muito ineficiente ao processar uma entrada quase válida.</span><span class="sxs-lookup"><span data-stu-id="f4a99-139">However, as the following example shows, although this regular expression handles valid input easily, its performance is very inefficient when it is processing nearly valid input.</span></span>

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

<span data-ttu-id="f4a99-140">Conforme mostrado pela saída do exemplo, o mecanismo de expressões regulares processa o alias de email válido quase no mesmo tempo, independentemente do seu comprimento.</span><span class="sxs-lookup"><span data-stu-id="f4a99-140">As the output from the example shows, the regular expression engine processes the valid email alias in about the same time interval regardless of its length.</span></span> <span data-ttu-id="f4a99-141">Por outro lado, quando o endereço de email quase válido tem mais de cinco caracteres, o tempo de processamento chega a dobrar para cada caractere adicional na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f4a99-141">On the other hand, when the nearly valid email address has more than five characters, processing time approximately doubles for each additional character in the string.</span></span> <span data-ttu-id="f4a99-142">Isso significa que uma cadeia de 28 caracteres quase válidos levaria mais de uma hora para ser processada e uma cadeia de 33 caracteres quase válidos demoraria quase um dia.</span><span class="sxs-lookup"><span data-stu-id="f4a99-142">This means that a nearly valid 28-character string would take over an hour to process, and a nearly valid 33-character string would take nearly a day to process.</span></span> 

<span data-ttu-id="f4a99-143">Como essa expressão regular foi desenvolvida considerando apenas a correspondência com o formato da entrada, ela não leva em consideração entradas que não correspondem ao padrão.</span><span class="sxs-lookup"><span data-stu-id="f4a99-143">Because this regular expression was developed solely by considering the format of input to be matched, it fails to take account of input that does not match the pattern.</span></span> <span data-ttu-id="f4a99-144">Isso, por sua vez, pode permitir que entradas não restritas quase correspondentes ao padrão da expressão regular prejudiquem significativamente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="f4a99-144">This, in turn, can allow unconstrained input that nearly matches the regular expression pattern to significantly degrade performance.</span></span>

<span data-ttu-id="f4a99-145">Para resolver este problema, você pode fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f4a99-145">To solve this problem, you can do the following:</span></span>

* <span data-ttu-id="f4a99-146">Ao desenvolver um padrão, você deve considerar como o retrocesso pode afetar o desempenho do mecanismo de expressões regulares, especialmente se a expressão regular for criada para processar entradas sem restrição.</span><span class="sxs-lookup"><span data-stu-id="f4a99-146">When developing a pattern, you should consider how backtracking might affect the performance of the regular expression engine, particularly if your regular expression is designed to process unconstrained input.</span></span> <span data-ttu-id="f4a99-147">Para obter mais informações, consulte a seção [Tome conta do retrocesso](#take-charge-of-backtracking).</span><span class="sxs-lookup"><span data-stu-id="f4a99-147">For more information, see the [Take charge of backtracking](#take-charge-of-backtracking) section.</span></span>

* <span data-ttu-id="f4a99-148">Teste rigorosamente sua expressão regular usando entradas inválidas e quase válidas, bem como entradas válidas.</span><span class="sxs-lookup"><span data-stu-id="f4a99-148">Thoroughly test your regular expression using invalid and near-valid input as well as valid input.</span></span> <span data-ttu-id="f4a99-149">Para gerar entradas para uma expressão regular específica aleatoriamente, você pode usar [Rex](http://research.microsoft.com/en-us/projects/rex/), que é uma ferramenta de exploração de expressões regulares da Microsoft Research.</span><span class="sxs-lookup"><span data-stu-id="f4a99-149">To generate input for a particular regular expression randomly, you can use [Rex](http://research.microsoft.com/en-us/projects/rex/), which is a regular expression exploration tool from Microsoft Research.</span></span>

## <a name="handle-object-instantiation-appropriately"></a><span data-ttu-id="f4a99-150">Trate a instanciação de objetos adequadamente</span><span class="sxs-lookup"><span data-stu-id="f4a99-150">Handle object instantiation appropriately</span></span>

<span data-ttu-id="f4a99-151">No centro do modelo de objeto de expressões regulares do .NET está a classe [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex), que representa o mecanismo de expressões regulares.</span><span class="sxs-lookup"><span data-stu-id="f4a99-151">At the heart of .NET’s regular expression object model is the [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) class, which represents the regular expression engine.</span></span> <span data-ttu-id="f4a99-152">Muitas vezes, o maior fator individual que afeta o desempenho das expressões regulares é a forma como o mecanismo [Regex](xref:System.Text.RegularExpressions.Regex) é usado.</span><span class="sxs-lookup"><span data-stu-id="f4a99-152">Often, the single greatest factor that affects regular expression performance is the way in which the [Regex](xref:System.Text.RegularExpressions.Regex) engine is used.</span></span> <span data-ttu-id="f4a99-153">Definir uma expressão regular envolve o acoplamento vigoroso do mecanismo de expressões regulares com um padrão de expressão regular.</span><span class="sxs-lookup"><span data-stu-id="f4a99-153">Defining a regular expression involves tightly coupling the regular expression engine with a regular expression pattern.</span></span> <span data-ttu-id="f4a99-154">Esse processo de acoplamento, seja envolvendo a instanciação de um objeto [Regex](xref:System.Text.RegularExpressions.Regex) ao passar para seu construtor um padrão de expressão regular ou seja chamando um método estático ao passar o padrão de expressão regular com a cadeia de caracteres a ser analisada, é necessariamente caro.</span><span class="sxs-lookup"><span data-stu-id="f4a99-154">That coupling process, whether it involves instantiating a [Regex](xref:System.Text.RegularExpressions.Regex) object by passing its constructor a regular expression pattern or calling a static method by passing it the regular expression pattern along with the string to be analyzed, is by necessity an expensive one.</span></span>

<span data-ttu-id="f4a99-155">É possível acoplar o mecanismo de expressões regulares com um padrão específico de expressão regular e usar o mecanismo para fazer a correspondência com texto de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="f4a99-155">You can couple the regular expression engine with a particular regular expression pattern and then use the engine to match text in several ways:</span></span>

* <span data-ttu-id="f4a99-156">Você pode chamar um método estático de correspondência de padrões, como [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String)).</span><span class="sxs-lookup"><span data-stu-id="f4a99-156">You can call a static pattern-matching method, such as [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String)).</span></span> <span data-ttu-id="f4a99-157">Isso não requer a instanciação de um objeto de expressão regular.</span><span class="sxs-lookup"><span data-stu-id="f4a99-157">This does not require instantiation of a regular expression object.</span></span>

* <span data-ttu-id="f4a99-158">É possível criar uma instância de um objeto [Regex](xref:System.Text.RegularExpressions.Regex) e chamar um método de instância de correspondência de padrões de uma expressão regular interpretada.</span><span class="sxs-lookup"><span data-stu-id="f4a99-158">You can instantiate a [Regex](xref:System.Text.RegularExpressions.Regex) object and call an instance pattern-matching method of an interpreted regular expression.</span></span> <span data-ttu-id="f4a99-159">Esse é o método padrão para associar o mecanismo de expressões regulares a uma expressão regular padrão.</span><span class="sxs-lookup"><span data-stu-id="f4a99-159">This is the default method for binding the regular expression engine to a regular expression pattern.</span></span> <span data-ttu-id="f4a99-160">Isso ocorre quando um objeto [Regex](xref:System.Text.RegularExpressions.Regex) é instanciado sem um argumento de opções que inclui o sinalizador [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled).</span><span class="sxs-lookup"><span data-stu-id="f4a99-160">It results when a [Regex](xref:System.Text.RegularExpressions.Regex) object is instantiated without an options argument that includes the [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) flag.</span></span>

* <span data-ttu-id="f4a99-161">Você pode criar uma instância de um objeto [Regex](xref:System.Text.RegularExpressions.Regex) e chamar um método de instância de correspondência de padrões de uma expressão regular compilada.</span><span class="sxs-lookup"><span data-stu-id="f4a99-161">You can instantiate a [Regex](xref:System.Text.RegularExpressions.Regex) object and call an instance pattern-matching method of a compiled regular expression.</span></span> <span data-ttu-id="f4a99-162">Os objetos de expressão regular representam padrões compilados quando um objeto [Regex](xref:System.Text.RegularExpressions.Regex) é instanciado com um argumento de opções que inclui o sinalizador [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled).</span><span class="sxs-lookup"><span data-stu-id="f4a99-162">Regular expression objects represent compiled patterns when a [Regex](xref:System.Text.RegularExpressions.Regex) object is instantiated with an options argument that includes the [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) flag.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f4a99-163">A forma da chamada de método (estático, interpretada, compilada) afeta o desempenho se a mesma expressão regular é usada repetidamente em chamadas de método ou se um aplicativo faz uso extensivo de objetos de expressão regular.</span><span class="sxs-lookup"><span data-stu-id="f4a99-163">The form of the method call (static, interpreted, compiled) affects performance if the same regular expression is used repeatedly in method calls, or if an application makes extensive use of regular expression objects.</span></span>
 
### <a name="static-regular-expressions"></a><span data-ttu-id="f4a99-164">Expressões regulares estáticas</span><span class="sxs-lookup"><span data-stu-id="f4a99-164">Static regular expressions</span></span>

<span data-ttu-id="f4a99-165">Os métodos de expressões regulares estáticas são recomendados como uma alternativa a criar repetidamente instâncias de um objeto de expressão regular com a mesma expressão regular.</span><span class="sxs-lookup"><span data-stu-id="f4a99-165">Static regular expression methods are recommended as an alternative to repeatedly instantiating a regular expression object with the same regular expression.</span></span> <span data-ttu-id="f4a99-166">Ao contrário de padrões de expressões regulares usados por objetos de expressões regulares, os códigos de operação ou a linguagem intermediária compilada da Microsoft (MSIL) de padrões usados em chamadas de métodos são armazenados em cache internamente pelo mecanismo de expressões regulares.</span><span class="sxs-lookup"><span data-stu-id="f4a99-166">Unlike regular expression patterns used by regular expression objects, either the operation codes or the compiled Microsoft intermediate language (MSIL) from patterns used in instance method calls is cached internally by the regular expression engine.</span></span> 

<span data-ttu-id="f4a99-167">Por exemplo, você pode chamar um método para validar a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="f4a99-167">For example, you might call a method to validate user input.</span></span> <span data-ttu-id="f4a99-168">Neste exemplo, um método chamado `IsValidCurrency` verifica se o usuário inseriu um símbolo de moeda seguido por pelo menos um dígito decimal.</span><span class="sxs-lookup"><span data-stu-id="f4a99-168">In this example, a method named `IsValidCurrency` checks whether the user has entered a currency symbol followed by at least one decimal digit.</span></span> <span data-ttu-id="f4a99-169">Uma implementação bem ineficiente do método `IsValidCurrency` é mostrada no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f4a99-169">A very inefficient implementation of the `IsValidCurrency` method is shown in the following example.</span></span> <span data-ttu-id="f4a99-170">Observe que cada chamada de método reinstancia um objeto [Regex](xref:System.Text.RegularExpressions.Regex) com o mesmo padrão.</span><span class="sxs-lookup"><span data-stu-id="f4a99-170">Note that each method call reinstantiates a [Regex](xref:System.Text.RegularExpressions.Regex) object with the same pattern.</span></span> <span data-ttu-id="f4a99-171">Isso, por sua vez, significa que o padrão de expressão regular deve ser recompilado toda vez que o método é chamado.</span><span class="sxs-lookup"><span data-stu-id="f4a99-171">This, in turn, means that the regular expression pattern must be recompiled each time the method is called.</span></span>

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

<span data-ttu-id="f4a99-172">Você deve substituir esse código ineficiente por uma chamada ao método estático [Regex.IsMatch(String, String)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String)).</span><span class="sxs-lookup"><span data-stu-id="f4a99-172">You should replace this inefficient code with a call to the static [Regex.IsMatch(String, String)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String)) method.</span></span> <span data-ttu-id="f4a99-173">Isso elimina a necessidade de criar uma instância de um objeto [Regex](xref:System.Text.RegularExpressions.Regex) toda vez que você desejar chamar um método de correspondência de padrões e permite que o mecanismo de expressões regulares recupere uma versão compilada da expressão regular do cache.</span><span class="sxs-lookup"><span data-stu-id="f4a99-173">This eliminates the need to instantiate a [Regex](xref:System.Text.RegularExpressions.Regex) object each time you want to call a pattern-matching method, and enables the regular expression engine to retrieve a compiled version of the regular expression from its cache.</span></span>

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

<span data-ttu-id="f4a99-174">Por padrão, os 15 padrões de expressões regulares estáticas usados mais recentemente são armazenados no cache.</span><span class="sxs-lookup"><span data-stu-id="f4a99-174">By default, the last 15 most recently used static regular expression patterns are cached.</span></span> <span data-ttu-id="f4a99-175">Para aplicativos que requerem um número maior de expressões regulares estáticas armazenadas no cache, o tamanho do cache pode ser ajustado com a definição da propriedade [Regex.CacheSize](xref:System.Text.RegularExpressions.Regex.CacheSize).</span><span class="sxs-lookup"><span data-stu-id="f4a99-175">For applications that require a larger number of cached static regular expressions, the size of the cache can be adjusted by setting the [Regex.CacheSize](xref:System.Text.RegularExpressions.Regex.CacheSize) property.</span></span>

<span data-ttu-id="f4a99-176">A expressão regular `\p{Sc}+\s*\d+` que é usada neste exemplo verifica que a cadeia de caracteres de entrada consiste em um símbolo de moeda e pelo menos um dígito decimal.</span><span class="sxs-lookup"><span data-stu-id="f4a99-176">The regular expression `\p{Sc}+\s*\d+` that is used in this example verifies that the input string consists of a currency symbol and at least one decimal digit.</span></span> <span data-ttu-id="f4a99-177">O padrão é definido conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="f4a99-177">The pattern is defined as shown in the following table.</span></span>

<span data-ttu-id="f4a99-178">Padrão</span><span class="sxs-lookup"><span data-stu-id="f4a99-178">Pattern</span></span> | <span data-ttu-id="f4a99-179">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4a99-179">Description</span></span>
------- | -----------
`\p{Sc}+` | <span data-ttu-id="f4a99-180">Corresponde a um ou mais caracteres no símbolo Unicode, categoria de moeda.</span><span class="sxs-lookup"><span data-stu-id="f4a99-180">Match one or more characters in the Unicode Symbol, Currency category.</span></span>
`\s*` | <span data-ttu-id="f4a99-181">Corresponder a zero ou mais caracteres de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="f4a99-181">Match zero or more white-space characters.</span></span>
`\d+` | <span data-ttu-id="f4a99-182">Corresponde a um ou mais dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="f4a99-182">Match one or more decimal digits.</span></span>
 
### <a name="interpreted-vs-compiled-regular-expressions"></a><span data-ttu-id="f4a99-183">Expressões regulares compiladas vs. interpretadas</span><span class="sxs-lookup"><span data-stu-id="f4a99-183">Interpreted vs. compiled regular expressions</span></span>

<span data-ttu-id="f4a99-184">Os padrões de expressões regulares que não são associados ao mecanismo de expressões regulares com a especificação da opção [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) são interpretados.</span><span class="sxs-lookup"><span data-stu-id="f4a99-184">Regular expression patterns that are not bound to the regular expression engine through the specification of the [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) option are interpreted.</span></span> <span data-ttu-id="f4a99-185">Quando um objeto de expressão regular é instanciado, o mecanismo de expressões regulares converte a expressão regular em um conjunto de códigos de operação.</span><span class="sxs-lookup"><span data-stu-id="f4a99-185">When a regular expression object is instantiated, the regular expression engine converts the regular expression to a set of operation codes.</span></span> <span data-ttu-id="f4a99-186">Quando um método de instância é chamado, os códigos de operação são convertidos para MSIL e executados pelo compilador JIT.</span><span class="sxs-lookup"><span data-stu-id="f4a99-186">When an instance method is called, the operation codes are converted to MSIL and executed by the JIT compiler.</span></span> <span data-ttu-id="f4a99-187">Da mesma forma, quando um método estático de expressão regular é chamado e a expressão regular não pode ser encontrada no cache, o mecanismo de expressão regular converte a expressão regular em um conjunto de códigos operacionais e os armazena no cache.</span><span class="sxs-lookup"><span data-stu-id="f4a99-187">Similarly, when a static regular expression method is called and the regular expression cannot be found in the cache, the regular expression engine converts the regular expression to a set of operation codes and stores them in the cache.</span></span> <span data-ttu-id="f4a99-188">Em seguida, converte esses códigos de operação para MSIL de modo que o compilador JIT possa executá-los.</span><span class="sxs-lookup"><span data-stu-id="f4a99-188">It then converts these operation codes to MSIL so that the JIT compiler can execute them.</span></span> <span data-ttu-id="f4a99-189">As expressões regulares interpretadas reduzem o tempo de inicialização ao custo de um tempo de execução mais lento.</span><span class="sxs-lookup"><span data-stu-id="f4a99-189">Interpreted regular expressions reduce startup time at the cost of slower execution time.</span></span> <span data-ttu-id="f4a99-190">Devido a isso, eles são melhores utilizados quando a expressão regular é usada em um pequeno número de chamadas de método ou se o número exato de chamadas para métodos de expressão regular é desconhecido, mas com a expectativa de ser pequeno.</span><span class="sxs-lookup"><span data-stu-id="f4a99-190">Because of this, they are best used when the regular expression is used in a small number of method calls, or if the exact number of calls to regular expression methods is unknown but is expected to be small.</span></span> <span data-ttu-id="f4a99-191">À medida que número de chamadas de método aumenta, o ganho de desempenho do tempo de inicialização reduzido é superado pela velocidade de execução mais lenta.</span><span class="sxs-lookup"><span data-stu-id="f4a99-191">As the number of method calls increases, the performance gain from reduced startup time is outstripped by the slower execution speed.</span></span>

<span data-ttu-id="f4a99-192">Os padrões de expressões regulares que são associados ao mecanismo de expressões regulares com a especificação da opção [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) são compilados.</span><span class="sxs-lookup"><span data-stu-id="f4a99-192">Regular expression patterns that are bound to the regular expression engine through the specification of the [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) option are compiled.</span></span> <span data-ttu-id="f4a99-193">Isso significa que, quando um objeto de expressão regular é instanciado ou quando um método de expressão regular estática é chamado e a expressão regular não pode ser encontrada no cache, o mecanismo de expressões regulares converte a expressão regular para um conjunto intermediário de códigos de operação, que em seguida é convertido para MSIL.</span><span class="sxs-lookup"><span data-stu-id="f4a99-193">This means that, when a regular expression object is instantiated, or when a static regular expression method is called and the regular expression cannot be found in the cache, the regular expression engine converts the regular expression to an intermediary set of operation codes, which it then converts to MSIL.</span></span> <span data-ttu-id="f4a99-194">Quando um método é chamado, o compilador JIT executa o MSIL.</span><span class="sxs-lookup"><span data-stu-id="f4a99-194">When a method is called, the JIT compiler executes the MSIL.</span></span> <span data-ttu-id="f4a99-195">Em contraste com as expressões regulares interpretadas, as expressões regulares compiladas aumentam o tempo de inicialização, mas executam os métodos individuais de correspondência padrão de forma mais rápida.</span><span class="sxs-lookup"><span data-stu-id="f4a99-195">In contrast to interpreted regular expressions, compiled regular expressions increase startup time but execute individual pattern-matching methods faster.</span></span> <span data-ttu-id="f4a99-196">Como resultado, o benefício de desempenho que resulta da compilação da expressão regular aumenta em proporção ao número de métodos de expressões regulares chamados.</span><span class="sxs-lookup"><span data-stu-id="f4a99-196">As a result, the performance benefit that results from compiling the regular expression increases in proportion to the number of regular expression methods called.</span></span>

<span data-ttu-id="f4a99-197">Para resumir, recomendamos que você use expressões regulares interpretadas ao chamar métodos de expressões regulares com uma expressão regular específica com relativa pouca frequência.</span><span class="sxs-lookup"><span data-stu-id="f4a99-197">To summarize, we recommend that you use interpreted regular expressions when you call regular expression methods with a specific regular expression relatively infrequently.</span></span> <span data-ttu-id="f4a99-198">Você deve usar expressões regulares compiladas ao chamar os métodos de expressões regulares com uma expressão regular específica com uma relativa frequência.</span><span class="sxs-lookup"><span data-stu-id="f4a99-198">You should use compiled regular expressions when you call regular expression methods with a specific regular expression relatively frequently.</span></span> <span data-ttu-id="f4a99-199">É difícil determinar o limite exato em que as velocidades de execução mais lentas das expressões regulares interpretadas suplantam os ganhos proporcionados pelo tempo de inicialização reduzido ou o limite em que os tempos de inicialização mais lentos das expressões regulares compiladas suplantam os ganhos gerados por suas velocidades de execução mais rápida.</span><span class="sxs-lookup"><span data-stu-id="f4a99-199">The exact threshold at which the slower execution speeds of interpreted regular expressions outweigh gains from their reduced startup time, or the threshold at which the slower startup times of compiled regular expressions outweigh gains from their faster execution speeds, is difficult to determine.</span></span> <span data-ttu-id="f4a99-200">O limite depende de vários fatores, incluindo a complexidade da expressão regular e dos dados específicos que são processados.</span><span class="sxs-lookup"><span data-stu-id="f4a99-200">It depends on a variety of factors, including the complexity of the regular expression and the specific data that it processes.</span></span> <span data-ttu-id="f4a99-201">Para determinar se as expressões regulares interpretadas ou compiladas oferecem o melhor desempenho para seu cenário de aplicativo específico, você pode usar a classe [Stopwatch](xref:System.Diagnostics.Stopwatch) para comparar seus tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="f4a99-201">To determine whether interpreted or compiled regular expressions offer the best performance for your particular application scenario, you can use the [Stopwatch](xref:System.Diagnostics.Stopwatch) class to compare their execution times.</span></span>

<span data-ttu-id="f4a99-202">O exemplo a seguir compara o desempenho de expressões regulares compiladas e interpretadas ao ler as dez primeiras frases e ao ler todas as frases no texto The Financier de Theodore Dreiser.</span><span class="sxs-lookup"><span data-stu-id="f4a99-202">The following example compares the performance of compiled and interpreted regular expressions when reading the first ten sentences and when reading all the sentences in the text of Theodore Dreiser's The Financier.</span></span> <span data-ttu-id="f4a99-203">Conforme mostrado pela saída do exemplo, quando apenas dez chamadas são feitas para os métodos correspondentes de expressão regular, uma expressão regular interpretada oferece um desempenho melhor do que uma expressão regular compilada.</span><span class="sxs-lookup"><span data-stu-id="f4a99-203">As the output from the example shows, when only ten calls are made to regular expression matching methods, an interpreted regular expression offers better performance than a compiled regular expression.</span></span> <span data-ttu-id="f4a99-204">No entanto, uma expressão regular compilada oferece melhor desempenho quando um grande número de chamadas (neste caso, mais 13.000) é feito.</span><span class="sxs-lookup"><span data-stu-id="f4a99-204">However, a compiled regular expression offers better performance when a large number of calls (in this case, over 13,000) are made.</span></span> 

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

<span data-ttu-id="f4a99-205">O padrão de expressão regular usado neste exemplo, `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`, é definido como mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="f4a99-205">The regular expression pattern used in the example, `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`, is defined as shown in the following table.</span></span>

<span data-ttu-id="f4a99-206">Padrão</span><span class="sxs-lookup"><span data-stu-id="f4a99-206">Pattern</span></span> | <span data-ttu-id="f4a99-207">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4a99-207">Description</span></span>
------- | -----------
`\b` | <span data-ttu-id="f4a99-208">Começa a correspondência em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="f4a99-208">Begin the match at a word boundary.</span></span>
`\w+` | <span data-ttu-id="f4a99-209">Fazer a correspondência a um ou mais caracteres de palavra.</span><span class="sxs-lookup"><span data-stu-id="f4a99-209">Match one or more word characters.</span></span>
<span data-ttu-id="f4a99-210">\`(\r?\n)</span><span class="sxs-lookup"><span data-stu-id="f4a99-210">\`(\r?\n)</span></span>|<span data-ttu-id="f4a99-211">,?\s)\`</span><span class="sxs-lookup"><span data-stu-id="f4a99-211">,?\s)\`</span></span> | <span data-ttu-id="f4a99-212">Corresponde a um zero ou um retorno de carro seguido por um caractere de nova linha, ou zero ou uma vírgula seguida por um caractere de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="f4a99-212">Match either zero or one carriage return followed by a newline character, or zero or one comma followed by a white-space character.</span></span>
<span data-ttu-id="f4a99-213">\`(\w+((\r?\n)</span><span class="sxs-lookup"><span data-stu-id="f4a99-213">\`(\w+((\r?\n)</span></span>|<span data-ttu-id="f4a99-214">,?\s))*\`</span><span class="sxs-lookup"><span data-stu-id="f4a99-214">,?\s))*\`</span></span> | <span data-ttu-id="f4a99-215">Corresponde a zero ou mais ocorrências de um ou mais caracteres de palavra que são seguidos por zero ou por retornos de carro e por um caractere de nova linha ou por zero ou uma vírgula seguida por um caractere de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="f4a99-215">Match zero or more occurrences of one or more word characters that are followed either by zero or one carriage return and a newline character, or by zero or one comma followed by a white-space character.</span></span>
`\w+` | <span data-ttu-id="f4a99-216">Fazer a correspondência a um ou mais caracteres de palavra.</span><span class="sxs-lookup"><span data-stu-id="f4a99-216">Match one or more word characters.</span></span>
`[.?:;!]` | <span data-ttu-id="f4a99-217">Corresponde a um ponto, um ponto de interrogação, dois-pontos, ponto-e-vírgula ou ponto de exclamação.</span><span class="sxs-lookup"><span data-stu-id="f4a99-217">Match a period, question mark, colon, semicolon, or exclamation point.</span></span>
 
## <a name="take-charge-of-backtracking"></a><span data-ttu-id="f4a99-218">Tome conta do retrocesso</span><span class="sxs-lookup"><span data-stu-id="f4a99-218">Take charge of backtracking</span></span>

<span data-ttu-id="f4a99-219">Normalmente, o mecanismo de expressões regulares usa progressão linear para percorrer uma cadeia de caracteres de entrada e compará-la a uma expressão regular padrão.</span><span class="sxs-lookup"><span data-stu-id="f4a99-219">Ordinarily, the regular expression engine uses linear progression to move through an input string and compare it to a regular expression pattern.</span></span> <span data-ttu-id="f4a99-220">No entanto, quando quantificadores indefinidos, como __*__, **+**, e **?**</span><span class="sxs-lookup"><span data-stu-id="f4a99-220">However, when indeterminate quantifiers such as __*__, **+**, and **?**</span></span> <span data-ttu-id="f4a99-221">são usados em uma expressão regular padrão, o mecanismo de expressões regulares pode desistir de uma parte das correspondências parciais com êxito e retornar a um estado salvo anteriormente para pesquisar uma correspondência com êxito para o padrão inteiro.</span><span class="sxs-lookup"><span data-stu-id="f4a99-221">are used in a regular expression pattern, the regular expression engine may give up a portion of successful partial matches and return to a previously saved state in order to search for a successful match for the entire pattern.</span></span> <span data-ttu-id="f4a99-222">Esse processo é conhecido como retrocesso.</span><span class="sxs-lookup"><span data-stu-id="f4a99-222">This process is known as backtracking.</span></span>

> [!NOTE]
> <span data-ttu-id="f4a99-223">Para obter mais informações sobre o retrocesso, confira [Detalhes do comportamento de expressões regulares](regex-behavior.md) e [Retrocesso em expressões regulares](backtracking.md).</span><span class="sxs-lookup"><span data-stu-id="f4a99-223">For more information on backtracking, see [Details of regular expression behavior](regex-behavior.md) and [Backtracking in regular expressions](backtracking.md).</span></span>
 
<span data-ttu-id="f4a99-224">O suporte ao retrocesso proporciona poder e flexibilidade às expressões regulares.</span><span class="sxs-lookup"><span data-stu-id="f4a99-224">Support for backtracking gives regular expressions power and flexibility.</span></span> <span data-ttu-id="f4a99-225">Ele também coloca a responsabilidade por controlar o funcionamento do mecanismo de expressões regulares nas mãos dos desenvolvedores de expressões regulares.</span><span class="sxs-lookup"><span data-stu-id="f4a99-225">It also places the responsibility for controlling the operation of the regular expression engine in the hands of regular expression developers.</span></span> <span data-ttu-id="f4a99-226">Como os desenvolvedores geralmente não estão cientes dessa responsabilidade, o uso indevido do retrocesso ou a confiança no retrocesso excessivo geralmente exerce o papel mais significativo na degradação do desempenho da expressão regular.</span><span class="sxs-lookup"><span data-stu-id="f4a99-226">Because developers are often not aware of this responsibility, their misuse of backtracking or reliance on excessive backtracking often plays the most significant role in degrading regular expression performance.</span></span> <span data-ttu-id="f4a99-227">Em um cenário de pior caso, o tempo de execução pode dobrar para cada caractere adicional na cadeia de caracteres de entrada.</span><span class="sxs-lookup"><span data-stu-id="f4a99-227">In a worst-case scenario, execution time can double for each additional character in the input string.</span></span> <span data-ttu-id="f4a99-228">Na verdade, quando o retrocesso é usado excessivamente, é fácil criar o equivalente programático de um loop infinito se a entrada quase corresponder ao padrão da expressão regular; o mecanismo de expressões regulares pode levar horas ou mesmo dias para processar uma cadeia de caracteres de entrada relativamente curta.</span><span class="sxs-lookup"><span data-stu-id="f4a99-228">In fact, by using backtracking excessively, it is easy to create the programmatic equivalent of an endless loop if input nearly matches the regular expression pattern; the regular expression engine may take hours or even days to process a relatively short input string.</span></span>

<span data-ttu-id="f4a99-229">Frequentemente, os aplicativos pagam uma penalidade de desempenho por usar o retrocesso, mesmo ele não sendo essencial para uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="f4a99-229">Often, applications pay a performance penalty for using backtracking despite the fact that backtracking is not essential for a match.</span></span> <span data-ttu-id="f4a99-230">Por exemplo, a expressão regular `\b\p{Lu}\w*\b` corresponde a todas as palavras que começam com um caractere maiúsculo, como mostra a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="f4a99-230">For example, the regular expression `\b\p{Lu}\w*\b` matches all words that begin with an uppercase character, as the following table shows.</span></span>

<span data-ttu-id="f4a99-231">Padrão</span><span class="sxs-lookup"><span data-stu-id="f4a99-231">Pattern</span></span> | <span data-ttu-id="f4a99-232">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4a99-232">Description</span></span>
------- | -----------
`\b` | <span data-ttu-id="f4a99-233">Começar a correspondência em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="f4a99-233">Begin the match at a word boundary.</span></span>
`\p{Lu}` | <span data-ttu-id="f4a99-234">Corresponder a um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="f4a99-234">Match an uppercase character.</span></span>
`\w*` | <span data-ttu-id="f4a99-235">Corresponder a zero ou mais caracteres de palavra.</span><span class="sxs-lookup"><span data-stu-id="f4a99-235">Match zero or more word characters.</span></span>
`\b` | <span data-ttu-id="f4a99-236">Termina a correspondência em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="f4a99-236">End the match at a word boundary.</span></span>
 
<span data-ttu-id="f4a99-237">Como um limite de palavra não é o mesmo que ou um subconjunto de, um caractere de palavra, não há nenhuma possibilidade de o mecanismo de expressões regulares cruzar um limite de palavra ao corresponder caracteres de palavra.</span><span class="sxs-lookup"><span data-stu-id="f4a99-237">Because a word boundary is not the same as, or a subset of, a word character, there is no possibility that the regular expression engine will cross a word boundary when matching word characters.</span></span> <span data-ttu-id="f4a99-238">Isso significa que, para esta expressão regular, o retrocesso nunca pode contribuir para o êxito total de qualquer correspondência – ele só pode prejudicar o desempenho, pois o mecanismo de expressões regulares é forçado a salvar o estado para cada correspondência preliminar bem-sucedida de um caractere de palavra.</span><span class="sxs-lookup"><span data-stu-id="f4a99-238">This means that for this regular expression, backtracking can never contribute to the overall success of any match -- it can only degrade performance, because the regular expression engine is forced to save its state for each successful preliminary match of a word character.</span></span>

<span data-ttu-id="f4a99-239">Se você determinar que o retrocesso não é necessário, poderá desabilitá-lo usando o elemento de linguagem **(?>**_subexpression_**)**.</span><span class="sxs-lookup"><span data-stu-id="f4a99-239">If you determine that backtracking is not necessary, you can disable it by using the **(?>**_subexpression_**)** language element.</span></span> <span data-ttu-id="f4a99-240">O exemplo a seguir analisa uma cadeia de caracteres de entrada usando duas expressões regulares.</span><span class="sxs-lookup"><span data-stu-id="f4a99-240">The following example parses an input string by using two regular expressions.</span></span> <span data-ttu-id="f4a99-241">A primeira, `\b\p{Lu}\w*\b`, depende do retrocesso.</span><span class="sxs-lookup"><span data-stu-id="f4a99-241">The first, `\b\p{Lu}\w*\b`, relies on backtracking.</span></span> <span data-ttu-id="f4a99-242">A segunda, `\b\p{Lu}(?>\w*)\b`, desabilita o retrocesso.</span><span class="sxs-lookup"><span data-stu-id="f4a99-242">The second, `\b\p{Lu}(?>\w*)\b`, disables backtracking.</span></span> <span data-ttu-id="f4a99-243">Conforme mostrado pela saída do exemplo, ambas produzem o mesmo resultado.</span><span class="sxs-lookup"><span data-stu-id="f4a99-243">As the output from the example shows, they both produce the same result.</span></span>

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

<span data-ttu-id="f4a99-244">Em muitos casos, o retrocesso é essencial para corresponder um padrão de expressão regular ao texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="f4a99-244">In many cases, backtracking is essential for matching a regular expression pattern to input text.</span></span> <span data-ttu-id="f4a99-245">No entanto, o retrocesso excessivo pode prejudicar severamente o desempenho e criar a impressão de que um aplicativo parou de responder.</span><span class="sxs-lookup"><span data-stu-id="f4a99-245">However, excessive backtracking can severely degrade performance and create the impression that an application has stopped responding.</span></span> <span data-ttu-id="f4a99-246">Em particular, isso acontece quando quantificadores são aninhados e o texto que corresponde à subexpressão externa é um subconjunto do texto que corresponde à subexpressão interna.</span><span class="sxs-lookup"><span data-stu-id="f4a99-246">In particular, this happens when quantifiers are nested and the text that matches the outer subexpression is a subset of the text that matches the inner subexpression.</span></span> 

> [!WARNING]
> <span data-ttu-id="f4a99-247">Além de evitar retrocessos excessivos, você deve usar o recurso de tempo limite para garantir que retrocessos excessivos não degradem severamente o desempenho da expressão regular.</span><span class="sxs-lookup"><span data-stu-id="f4a99-247">In addition to avoiding excessive backtracking, you should use the timeout feature to ensure that excessive backtracking does not severely degrade regular expression performance.</span></span> <span data-ttu-id="f4a99-248">Para obter mais informações, confira a seção [Use valores de tempo limite](#use-time-out-values).</span><span class="sxs-lookup"><span data-stu-id="f4a99-248">For more information, see the [Use time-out values](#use-time-out-values) section.</span></span>
 
<span data-ttu-id="f4a99-249">Por exemplo, o padrão de expressão regular `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` destina-se a corresponder a um número de peça que consiste em pelo menos um caractere alfanumérico.</span><span class="sxs-lookup"><span data-stu-id="f4a99-249">For example, the regular expression pattern `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` is intended to match a part number that consists of at least one alphanumeric character.</span></span> <span data-ttu-id="f4a99-250">Todos os demais caracteres podem consistir em um caractere alfanumérico, um hífen, um sublinhado ou um ponto, embora o último caractere deva ser alfanumérico.</span><span class="sxs-lookup"><span data-stu-id="f4a99-250">Any additional characters can consist of an alphanumeric character, a hyphen, an underscore, or a period, though the last character must be alphanumeric.</span></span> <span data-ttu-id="f4a99-251">Um cifrão termina o número da peça.</span><span class="sxs-lookup"><span data-stu-id="f4a99-251">A dollar sign terminates the part number.</span></span> <span data-ttu-id="f4a99-252">Em alguns casos, esse padrão de expressão regular pode exibir um desempenho muito ruim porque os quantificadores estão aninhados e porque a subexpressão `[0-9A-Z]` é um subconjunto da subexpressão `[-.\w]*`.</span><span class="sxs-lookup"><span data-stu-id="f4a99-252">In some cases, this regular expression pattern can exhibit extremely poor performance because quantifiers are nested, and because the subexpression `[0-9A-Z]` is a subset of the subexpression `[-.\w]*`.</span></span>

<span data-ttu-id="f4a99-253">Nesses casos, você pode otimizar o desempenho da expressão regular ao remover os quantificadores aninhados e substituir a subexpressão externa por uma declaração de lookahead ou lookbehind de largura zero.</span><span class="sxs-lookup"><span data-stu-id="f4a99-253">In these cases, you can optimize regular expression performance by removing the nested quantifiers and replacing the outer subexpression with a zero-width lookahead or lookbehind assertion.</span></span> <span data-ttu-id="f4a99-254">As asserções lookahead e lookbehind são âncoras; elas não movem o ponteiro na cadeia de caracteres de entrada, mas fazem uma verificação para verificar se uma condição especificada foi atendida.</span><span class="sxs-lookup"><span data-stu-id="f4a99-254">Lookahead and lookbehind assertions are anchors; they do not move the pointer in the input string, but instead look ahead or behind to check whether a specified condition is met.</span></span> <span data-ttu-id="f4a99-255">Por exemplo, a expressão regular do número de peça pode ser reescrita como `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`.</span><span class="sxs-lookup"><span data-stu-id="f4a99-255">For example, the part number regular expression can be rewritten as `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`.</span></span> <span data-ttu-id="f4a99-256">Esse padrão de expressão regular é definido conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="f4a99-256">This regular expression pattern is defined as shown in the following table.</span></span>

<span data-ttu-id="f4a99-257">Padrão</span><span class="sxs-lookup"><span data-stu-id="f4a99-257">Pattern</span></span> | <span data-ttu-id="f4a99-258">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4a99-258">Description</span></span>
------- | -----------
`^` | <span data-ttu-id="f4a99-259">Começar a correspondência no início da cadeia de caracteres de entrada.</span><span class="sxs-lookup"><span data-stu-id="f4a99-259">Begin the match at the beginning of the input string.</span></span>
`[0-9A-Z]` | <span data-ttu-id="f4a99-260">Corresponde a um caractere alfanumérico.</span><span class="sxs-lookup"><span data-stu-id="f4a99-260">Match an alphanumeric character.</span></span> <span data-ttu-id="f4a99-261">O número de peça deve consistir em pelo menos este caractere.</span><span class="sxs-lookup"><span data-stu-id="f4a99-261">The part number must consist of at least this character.</span></span>
`[-.\w]*` | <span data-ttu-id="f4a99-262">Corresponde a zero ou mais ocorrências de qualquer caractere de palavra, hífen ou ponto.</span><span class="sxs-lookup"><span data-stu-id="f4a99-262">Match zero or more occurrences of any word character, hyphen, or period.</span></span>
<span data-ttu-id="f4a99-263">\`\$]</span><span class="sxs-lookup"><span data-stu-id="f4a99-263">\`\$]</span></span> | <span data-ttu-id="f4a99-264">Corresponde a um cifrão.</span><span class="sxs-lookup"><span data-stu-id="f4a99-264">Match a dollar sign.</span></span>
`(?<=[0-9A-Z])` | <span data-ttu-id="f4a99-265">Examine além do cifrão final para garantir que o caractere anterior seja alfanumérico.</span><span class="sxs-lookup"><span data-stu-id="f4a99-265">Look ahead of the ending dollar sign to ensure that the previous character is alphanumeric.</span></span>
<span data-ttu-id="f4a99-266">`$` Finalizar a correspondência no final da cadeia de caracteres de entrada.</span><span class="sxs-lookup"><span data-stu-id="f4a99-266">`$` End the match at the end of the input string.</span></span>
 
<span data-ttu-id="f4a99-267">O exemplo a seguir ilustra o uso dessa expressão regular para corresponder a uma que contém possíveis números de peças.</span><span class="sxs-lookup"><span data-stu-id="f4a99-267">The following example illustrates the use of this regular expression to match an array containing possible part numbers.</span></span>

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

<span data-ttu-id="f4a99-268">A linguagem de expressões regulares no .NET inclui os seguintes elementos de linguagem que você pode usar para eliminar quantificadores aninhados.</span><span class="sxs-lookup"><span data-stu-id="f4a99-268">The regular expression language in .NET includes the following language elements that you can use to eliminate nested quantifiers.</span></span> <span data-ttu-id="f4a99-269">Para obter mais informações, consulte [Constructos de agrupamento em expressões regulares](grouping.md).</span><span class="sxs-lookup"><span data-stu-id="f4a99-269">For more information, see [Grouping constructs in regular expressions](grouping.md).</span></span>

<span data-ttu-id="f4a99-270">Elemento de linguagem</span><span class="sxs-lookup"><span data-stu-id="f4a99-270">Language element</span></span> | <span data-ttu-id="f4a99-271">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4a99-271">Description</span></span>
---------------- | ----------- 
<span data-ttu-id="f4a99-272">**(?**=_subexpression_**)**</span><span class="sxs-lookup"><span data-stu-id="f4a99-272">**(?**=_subexpression_**)**</span></span> | <span data-ttu-id="f4a99-273">Lookahead positivo de largura zero.</span><span class="sxs-lookup"><span data-stu-id="f4a99-273">Zero-width positive lookahead.</span></span> <span data-ttu-id="f4a99-274">Examina além da posição atual para determinar se a *subexpression* corresponde à cadeia de caracteres de entrada.</span><span class="sxs-lookup"><span data-stu-id="f4a99-274">Look ahead of the current position to determine whether *subexpression* matches the input string.</span></span>
<span data-ttu-id="f4a99-275">**(?!**_subexpression_**)**</span><span class="sxs-lookup"><span data-stu-id="f4a99-275">**(?!**_subexpression_**)**</span></span> | <span data-ttu-id="f4a99-276">Lookahead negativo de largura zero.</span><span class="sxs-lookup"><span data-stu-id="f4a99-276">Zero-width negative lookahead.</span></span> <span data-ttu-id="f4a99-277">Examina além da posição atual para determinar se a *subexpressão* não corresponde à cadeia de caracteres de entrada.</span><span class="sxs-lookup"><span data-stu-id="f4a99-277">Look ahead of the current position to determine whether *subexpression* does not match the input string.</span></span>
<span data-ttu-id="f4a99-278">**(?<**=_subexpression_**)**</span><span class="sxs-lookup"><span data-stu-id="f4a99-278">**(?<**=_subexpression_**)**</span></span> | <span data-ttu-id="f4a99-279">Lookbehind positivo de largura zero.</span><span class="sxs-lookup"><span data-stu-id="f4a99-279">Zero-width positive lookbehind.</span></span> <span data-ttu-id="f4a99-280">Examina o conteúdo que antecede a posição atual para determinar se a *subexpression* corresponde à cadeia de caracteres de entrada.</span><span class="sxs-lookup"><span data-stu-id="f4a99-280">Look behind the current position to determine whether *subexpression* matches the input string.</span></span>
<span data-ttu-id="f4a99-281">**(?<!**_subexpression_**)**</span><span class="sxs-lookup"><span data-stu-id="f4a99-281">**(?<!**_subexpression_**)**</span></span> | <span data-ttu-id="f4a99-282">Lookbehind negativo de largura zero.</span><span class="sxs-lookup"><span data-stu-id="f4a99-282">Zero-width negative lookbehind.</span></span> <span data-ttu-id="f4a99-283">Examina o conteúdo que antecede a posição atual para determinar se a *subexpressão* não corresponde à cadeia de caracteres de entrada.</span><span class="sxs-lookup"><span data-stu-id="f4a99-283">Look behind the current position to determine whether *subexpression* does not match the input string.</span></span>
 
## <a name="use-time-out-values"></a><span data-ttu-id="f4a99-284">Use valores de tempo limite</span><span class="sxs-lookup"><span data-stu-id="f4a99-284">Use time-out values</span></span>

<span data-ttu-id="f4a99-285">Se suas expressões regulares processarem entradas quase correspondentes ao padrão da expressão regular, elas poderão frequentemente confiar no retrocesso excessivo, o que afeta significativamente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="f4a99-285">If your regular expressions processes input that nearly matches the regular expression pattern, it can often rely on excessive backtracking, which impacts its performance significantly.</span></span> <span data-ttu-id="f4a99-286">Além de considerar cuidadosamente o uso do retrocesso e testar a expressão regular contra entradas quase correspondentes, você deve sempre definir um valor de tempo limite para garantir que o impacto do retrocesso excessivo, caso ocorra, seja minimizado.</span><span class="sxs-lookup"><span data-stu-id="f4a99-286">In addition to carefully considering your use of backtracking and testing the regular expression against near-matching input, you should always set a time-out value to ensure that the impact of excessive backtracking, if it occurs, is minimized.</span></span>

<span data-ttu-id="f4a99-287">O intervalo de tempo limite da expressão regular define o período durante o qual o mecanismo de expressões regulares procurará uma única correspondência antes que o tempo limite seja atingido.</span><span class="sxs-lookup"><span data-stu-id="f4a99-287">The regular expression time-out interval defines the period of time that the regular expression engine will look for a single match before it times out.</span></span> <span data-ttu-id="f4a99-288">O intervalo de tempo limite padrão é [Regex.InfiniteMatchTimeout](xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout), o que significa que a expressão regular não atingirá o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="f4a99-288">The default time-out interval is [Regex.InfiniteMatchTimeout](xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout), which means that the regular expression will not time out.</span></span> <span data-ttu-id="f4a99-289">É possível substituir esse valor e definir um intervalo de tempo limite da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="f4a99-289">You can override this value and define a time-out interval as follows:</span></span> 

* <span data-ttu-id="f4a99-290">Fornecendo um valor de tempo limite ao criar uma instância de um objeto [Regex](xref:System.Text.RegularExpressions.Regex) chamando o construtor [Regex(String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.%23ctor(System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)).</span><span class="sxs-lookup"><span data-stu-id="f4a99-290">By providing a time-out value when you instantiate a [Regex](xref:System.Text.RegularExpressions.Regex) object by calling the [Regex(String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.%23ctor(System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) constructor.</span></span>

* <span data-ttu-id="f4a99-291">Chamando um padrão estático que corresponde ao método, como [Regex.Match(String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) ou [Regex.Replace(String, String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)), que inclui um parâmetro *matchTimeout*.</span><span class="sxs-lookup"><span data-stu-id="f4a99-291">By calling a static pattern matching method, such as [Regex.Match(String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) or [Regex.Replace(String, String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)), that includes a *matchTimeout* parameter.</span></span>

<span data-ttu-id="f4a99-292">Se você tiver definido um intervalo de tempo limite e uma correspondência não for localizada no final do intervalo, o método de expressão regular gerará uma exceção [RegexMatchTimeoutException](xref:System.Text.RegularExpressions.RegexMatchTimeoutException).</span><span class="sxs-lookup"><span data-stu-id="f4a99-292">If you have defined a time-out interval and a match is not found at the end of that interval, the regular expression method throws a [RegexMatchTimeoutException](xref:System.Text.RegularExpressions.RegexMatchTimeoutException) exception.</span></span> <span data-ttu-id="f4a99-293">No manipulador de exceção, você pode optar por tentar fazer novamente a correspondência com um intervalo de tempo limite mais longo, abandonar a tentativa de correspondência e assumir que não há nenhuma correspondência ou abandonar a tentativa de correspondência e registrar as informações de exceção para análise futura.</span><span class="sxs-lookup"><span data-stu-id="f4a99-293">In your exception handler, you can choose to retry the match with a longer time-out interval, abandon the match attempt and assume that there is no match, or abandon the match attempt and log the exception information for future analysis.</span></span>

<span data-ttu-id="f4a99-294">O exemplo a seguir define um método `GetWordData` que instancia uma expressão regular com um intervalo de tempo limite de 350 milissegundos para calcular o número de palavras e o número médio de caracteres em uma palavra em um documento de texto.</span><span class="sxs-lookup"><span data-stu-id="f4a99-294">The following example defines a `GetWordData` method that instantiates a regular expression with a time-out interval of 350 milliseconds to calculate the number of words and average number of characters in a word in a text document.</span></span> <span data-ttu-id="f4a99-295">Se a operação de correspondência exceder o tempo limite, o intervalo de tempo limite será aumentado em 350 milissegundos e o objeto de [Regex](xref:System.Text.RegularExpressions.Regex) será reinstanciado.</span><span class="sxs-lookup"><span data-stu-id="f4a99-295">If the matching operation times out, the time-out interval is increased by 350 milliseconds and the [Regex](xref:System.Text.RegularExpressions.Regex) object is re-instantiated.</span></span> <span data-ttu-id="f4a99-296">Se o novo intervalo de tempo limite exceder 1 segundo, o método gerará novamente a exceção no chamador.</span><span class="sxs-lookup"><span data-stu-id="f4a99-296">If the new time-out interval exceeds 1 second, the method re-throws the exception to the caller.</span></span>

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

## <a name="capture-only-when-necessary"></a><span data-ttu-id="f4a99-297">Capture somente quando necessário</span><span class="sxs-lookup"><span data-stu-id="f4a99-297">Capture only when necessary</span></span>

<span data-ttu-id="f4a99-298">As expressões regulares no .NET dão suporte a vários constructos de agrupamento, que permitem a você agrupar um padrão de expressão regular em uma ou mais subexpressões.</span><span class="sxs-lookup"><span data-stu-id="f4a99-298">Regular expressions in .NET support a number of grouping constructs, which let you group a regular expression pattern into one or more subexpressions.</span></span> <span data-ttu-id="f4a99-299">Os constructos de agrupamentos mais usados na linguagem de expressões regulares no .NET **(**_subexpression_**)**, que define um grupo de captura numerado e **(?<*_name_**>**_subexpression_**)**, que define um grupo de captura nomeado.</span><span class="sxs-lookup"><span data-stu-id="f4a99-299">The most commonly used grouping constructs in .NET regular expression language are **(**_subexpression_**)**, which defines a numbered capturing group, and **(?<*_name_**>**_subexpression_**)**, which defines a named capturing group.</span></span> <span data-ttu-id="f4a99-300">Os construtores de agrupamento são essenciais para criar referências reversas e definir uma subexpressão à qual um quantificador é aplicado.</span><span class="sxs-lookup"><span data-stu-id="f4a99-300">Grouping constructs are essential for creating backreferences and for defining a subexpression to which a quantifier is applied.</span></span> 

<span data-ttu-id="f4a99-301">No entanto, o uso desses elementos de linguagem tem um custo.</span><span class="sxs-lookup"><span data-stu-id="f4a99-301">However, the use of these language elements has a cost.</span></span> <span data-ttu-id="f4a99-302">Eles fazem com que o objeto [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) retornado pela propriedade [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) seja populado com as capturas sem nome ou nomeadas mais recentes. Além disso, se um único constructo de agrupamento tiver capturado várias subcadeias de caracteres na cadeia de caracteres de entrada, também populam o objeto [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) retornado pela propriedade [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) de um grupo de captura específico com vários objetos [Capture](xref:System.Text.RegularExpressions.Capture).</span><span class="sxs-lookup"><span data-stu-id="f4a99-302">They cause the [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) object returned by the [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) property to be populated with the most recent unnamed or named captures, and if a single grouping construct has captured multiple substrings in the input string, they also populate the [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) object returned by the [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) property of a particular capturing group with multiple [Capture](xref:System.Text.RegularExpressions.Capture) objects.</span></span>

<span data-ttu-id="f4a99-303">Muitas vezes, os construtores de agrupamento são usados somente em uma expressão regular de modo que quantificadores possam ser aplicados a eles e os grupos capturados por essas subexpressão não são usados posteriormente.</span><span class="sxs-lookup"><span data-stu-id="f4a99-303">Often, grouping constructs are used in a regular expression only so that quantifiers can be applied to them, and the groups captured by these subexpressions are not subsequently used.</span></span> <span data-ttu-id="f4a99-304">Por exemplo, a expressão regular `\b(\w+[;,]?\s?)+[.?!]` é criada para capturar uma frase inteira.</span><span class="sxs-lookup"><span data-stu-id="f4a99-304">For example, the regular expression `\b(\w+[;,]?\s?)+[.?!]` is designed to capture an entire sentence.</span></span> <span data-ttu-id="f4a99-305">A tabela a seguir descreve os elementos de linguagem nesse padrão de expressão regular e seu efeito nas coleções [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) e [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) do objeto [Match](xref:System.Text.RegularExpressions.Match).</span><span class="sxs-lookup"><span data-stu-id="f4a99-305">The following table describes the language elements in this regular expression pattern and their effect on the [Match](xref:System.Text.RegularExpressions.Match) object's [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) and [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) collections.</span></span>

<span data-ttu-id="f4a99-306">Padrão</span><span class="sxs-lookup"><span data-stu-id="f4a99-306">Pattern</span></span> | <span data-ttu-id="f4a99-307">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4a99-307">Description</span></span>
------- | -----------
`\b` | <span data-ttu-id="f4a99-308">Começa a correspondência em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="f4a99-308">Begin the match at a word boundary.</span></span>
`\w+` | <span data-ttu-id="f4a99-309">Fazer a correspondência a um ou mais caracteres de palavra.</span><span class="sxs-lookup"><span data-stu-id="f4a99-309">Match one or more word characters.</span></span>
`[;,]?` | <span data-ttu-id="f4a99-310">Corresponde a zero ou uma vírgula ou ponto e vírgula.</span><span class="sxs-lookup"><span data-stu-id="f4a99-310">Match zero or one comma or semicolon.</span></span>
`\s?` | <span data-ttu-id="f4a99-311">Corresponder a zero ou a um caractere de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="f4a99-311">Match zero or one white-space character.</span></span>
`(\w+[;,]?\s?)+` | <span data-ttu-id="f4a99-312">Corresponde a uma ou mais ocorrências de um ou mais caracteres de palavra seguidos por uma vírgula opcional ou por ponto-e-vírgula seguido por um caractere de espaço em branco opcional.</span><span class="sxs-lookup"><span data-stu-id="f4a99-312">Match one or more occurrences of one or more word characters followed by an optional comma or semicolon followed by an optional white-space character.</span></span> <span data-ttu-id="f4a99-313">Isso define o primeiro grupo de captura, que é necessário para que a combinação de vários caracteres de palavra (ou seja, uma palavra) seguido por um símbolo de pontuação opcional seja repetida até que o mecanismo de expressões regulares atinja o final de uma sentença.</span><span class="sxs-lookup"><span data-stu-id="f4a99-313">This defines the first capturing group, which is necessary so that the combination of multiple word characters (that is, a word) followed by an optional punctuation symbol will be repeated until the regular expression engine reaches the end of a sentence.</span></span>
`[.?!]` | <span data-ttu-id="f4a99-314">Corresponde a um ponto, um ponto de interrogação ou um ponto de exclamação.</span><span class="sxs-lookup"><span data-stu-id="f4a99-314">Match a period, question mark, or exclamation point.</span></span>
 
<span data-ttu-id="f4a99-315">Como o exemplo a seguir mostra, quando uma correspondência é encontrada, os objetos [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) e [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) são populados com as capturas da correspondência.</span><span class="sxs-lookup"><span data-stu-id="f4a99-315">As the following example shows, when a match is found, both the [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) and [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) objects are populated with captures from the match.</span></span> <span data-ttu-id="f4a99-316">Nesse caso, o grupo de captura `(\w+[;,]?\s?)` existe para que o quantificador **+** possa ser aplicado a ele, o que permite que o padrão de expressão regular corresponda a cada palavra em uma sentença.</span><span class="sxs-lookup"><span data-stu-id="f4a99-316">In this case, the capturing group `(\w+[;,]?\s?)` exists so that the **+** quantifier can be applied to it, which enables the regular expression pattern to match each word in a sentence.</span></span> <span data-ttu-id="f4a99-317">Caso contrário, ele corresponderia à última palavra em uma sentença.</span><span class="sxs-lookup"><span data-stu-id="f4a99-317">Otherwise, it would match the last word in a sentence.</span></span>

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

<span data-ttu-id="f4a99-318">Quando você usa subexpressões apenas para aplicar quantificadores a elas e não está interessado em texto capturado, desabilite as capturas de grupo.</span><span class="sxs-lookup"><span data-stu-id="f4a99-318">When you use subexpressions only to apply quantifiers to them, and you are not interested in the captured text, you should disable group captures.</span></span> <span data-ttu-id="f4a99-319">Por exemplo, o elemento de linguagem **(?:**_subexpression_**)** evita que o grupo ao qual ele se aplica capture subcadeias de caracteres correspondidas.</span><span class="sxs-lookup"><span data-stu-id="f4a99-319">For example, the **(?:**_subexpression_**)** language element prevents the group to which it applies from capturing matched substrings.</span></span> <span data-ttu-id="f4a99-320">No exemplo a seguir, o padrão de expressão regular do exemplo anterior é alterado para `\b(?:\w+[;,]?\s?)+[.?!]`.</span><span class="sxs-lookup"><span data-stu-id="f4a99-320">In the following example, the regular expression pattern from the previous example is changed to `\b(?:\w+[;,]?\s?)+[.?!]`.</span></span> <span data-ttu-id="f4a99-321">Conforme mostrado pela saída, ele impede que o mecanismo de expressões regulares popule as coleções [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) e [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection).</span><span class="sxs-lookup"><span data-stu-id="f4a99-321">As the output shows, it prevents the regular expression engine from populating the [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) and [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) collections.</span></span>

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

<span data-ttu-id="f4a99-322">É possível desabilitar as capturas de uma das seguintes formas:</span><span class="sxs-lookup"><span data-stu-id="f4a99-322">You can disable captures in one of the following ways:</span></span>

* <span data-ttu-id="f4a99-323">Use o elemento de linguagem **(?:**_subexpression_**)**.</span><span class="sxs-lookup"><span data-stu-id="f4a99-323">Use the **(?:**_subexpression_**)** language element.</span></span> <span data-ttu-id="f4a99-324">Esse elemento impede a captura de subcadeias de caracteres correspondidas no grupo ao qual se ele aplica.</span><span class="sxs-lookup"><span data-stu-id="f4a99-324">This element prevents the capture of matched substrings in the group to which it applies.</span></span> <span data-ttu-id="f4a99-325">Ele não desabilita capturas de subcadeias de caracteres em grupos aninhados.</span><span class="sxs-lookup"><span data-stu-id="f4a99-325">It does not disable substring captures in any nested groups.</span></span>

* <span data-ttu-id="f4a99-326">Use a opção [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture).</span><span class="sxs-lookup"><span data-stu-id="f4a99-326">Use the [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) option.</span></span> <span data-ttu-id="f4a99-327">Ela desabilita todas as capturas sem nome ou implícitas no padrão de expressão regular.</span><span class="sxs-lookup"><span data-stu-id="f4a99-327">It disables all unnamed or implicit captures in the regular expression pattern.</span></span> <span data-ttu-id="f4a99-328">Quando você usa essa opção, somente as subcadeias de caracteres que correspondem aos grupos nomeados definidos com o elemento de linguagem **(?<**_name_**>**_subexpression_**)** podem ser capturadas.</span><span class="sxs-lookup"><span data-stu-id="f4a99-328">When you use this option, only substrings that match named groups defined with the **(?<**_name_**>**_subexpression_**)** language element can be captured.</span></span> <span data-ttu-id="f4a99-329">O sinalizador [ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) pode ser passado para o parâmetro de opções de um construtor de classe [Regex](xref:System.Text.RegularExpressions.Regex) ou para o parâmetro de opções de um método de correspondência estático [Regex](xref:System.Text.RegularExpressions.Regex).</span><span class="sxs-lookup"><span data-stu-id="f4a99-329">The [ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) flag can be passed to the options parameter of a [Regex](xref:System.Text.RegularExpressions.Regex) class constructor or to the options parameter of a [Regex](xref:System.Text.RegularExpressions.Regex) static matching method.</span></span>

* <span data-ttu-id="f4a99-330">Use a opção **n** no elemento de linguagem **(?imnsx)**.</span><span class="sxs-lookup"><span data-stu-id="f4a99-330">Use the **n** option in the **(?imnsx)** language element.</span></span> <span data-ttu-id="f4a99-331">Esta opção desabilita todas as capturas sem nome ou implícitas a partir do ponto no padrão de expressão regular em que o elemento aparece.</span><span class="sxs-lookup"><span data-stu-id="f4a99-331">This option disables all unnamed or implicit captures from the point in the regular expression pattern at which the element appears.</span></span> <span data-ttu-id="f4a99-332">As capturas são desabilitadas até o final do padrão ou até a opção **(-n)** habilitar capturas sem nome ou implícitas.</span><span class="sxs-lookup"><span data-stu-id="f4a99-332">Captures are disabled either until the end of the pattern or until the **(-n)** option enables unnamed or implicit captures.</span></span> <span data-ttu-id="f4a99-333">Para obter mais informações, consulte [Constructos diversos em expressões regulares](miscellaneous.md).</span><span class="sxs-lookup"><span data-stu-id="f4a99-333">For more information, see [Miscellaneous constructs in regular expressions](miscellaneous.md).</span></span>

* <span data-ttu-id="f4a99-334">Use a opção **n** no elemento de linguagem **(?imnsx:**_subexpression_**)**.</span><span class="sxs-lookup"><span data-stu-id="f4a99-334">Use the **n** option in the **(?imnsx:**_subexpression_**)** language element.</span></span> <span data-ttu-id="f4a99-335">Esta opção desabilita todas as capturas sem nome ou implícitas na *subexpressão*.</span><span class="sxs-lookup"><span data-stu-id="f4a99-335">This option disables all unnamed or implicit captures in *subexpression*.</span></span> <span data-ttu-id="f4a99-336">As capturas por grupos de capturas aninhadas sem nome ou implícitas também são desabilitadas.</span><span class="sxs-lookup"><span data-stu-id="f4a99-336">Captures by any unnamed or implicit nested capturing groups are disabled as well.</span></span>

## <a name="related-topics"></a><span data-ttu-id="f4a99-337">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="f4a99-337">Related topics</span></span>

<span data-ttu-id="f4a99-338">Título</span><span class="sxs-lookup"><span data-stu-id="f4a99-338">Title</span></span> | <span data-ttu-id="f4a99-339">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4a99-339">Description</span></span>
----- | ----------- 
[<span data-ttu-id="f4a99-340">Detalhes do comportamento de expressões regulares</span><span class="sxs-lookup"><span data-stu-id="f4a99-340">Details of regular expression behavior</span></span>](regex-behavior.md) | <span data-ttu-id="f4a99-341">Examina a implementação do mecanismo de expressões regulares no .NET.</span><span class="sxs-lookup"><span data-stu-id="f4a99-341">Examines the implementation of the regular expression engine in .NET.</span></span> <span data-ttu-id="f4a99-342">O tópico concentra-se na flexibilidade de expressões regulares e explica a responsabilidade do desenvolvedor para garantir o funcionamento eficiente e robusto do mecanismo de expressões regulares.</span><span class="sxs-lookup"><span data-stu-id="f4a99-342">The topic focuses on the flexibility of regular expressions and explains the developer's responsibility for ensuring the efficient and robust operation of the regular expression engine.</span></span>
[<span data-ttu-id="f4a99-343">Retrocesso em expressões regulares</span><span class="sxs-lookup"><span data-stu-id="f4a99-343">Backtracking in regular expressions</span></span>](backtracking.md) | <span data-ttu-id="f4a99-344">Explica o que é o retrocesso é como ele afeta o desempenho da expressão regular e examina os elementos de linguagem que fornecem alternativas ao retrocesso.</span><span class="sxs-lookup"><span data-stu-id="f4a99-344">Explains what backtracking is and how it affects regular expression performance, and examines language elements that provide alternatives to backtracking.</span></span>
[<span data-ttu-id="f4a99-345">Linguagem de expressão regular – referência rápida</span><span class="sxs-lookup"><span data-stu-id="f4a99-345">Regular expression language - quick reference</span></span>](quick-ref.md) | <span data-ttu-id="f4a99-346">Descreve os elementos de linguagem de expressões regulares do .NET e fornece links para a documentação detalhada de cada elemento da linguagem.</span><span class="sxs-lookup"><span data-stu-id="f4a99-346">Describes the elements of the regular expression language in .NET and provides links to detailed documentation for each language element.</span></span>
 


