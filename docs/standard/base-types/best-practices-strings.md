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
ms.translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 3efd30bade564fe1b7dbf93237a9ff40c58c5f1e
ms.contentlocale: pt-br
ms.lasthandoff: 11/05/2016

---

# <a name="best-practices-for-using-strings"></a><span data-ttu-id="880d1-104">Práticas recomendadas para o uso de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="880d1-104">Best practices for using strings</span></span>

<span data-ttu-id="880d1-105">O .NET dá um amplo suporte para desenvolvimento de aplicativos localizados e globalizados e torna mais fácil aplicar as convenções da cultura atual ou de uma cultura específica ao executar operações comuns, como a classificação e a exibição cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="880d1-105">.NET provides extensive support for developing localized and globalized applications, and makes it easy to apply the conventions of either the current culture or a specific culture when performing common operations such as sorting and displaying strings.</span></span> <span data-ttu-id="880d1-106">Mas a classificação ou a comparação de cadeias de caracteres nem sempre é uma operação que leva em conta a cultura.</span><span class="sxs-lookup"><span data-stu-id="880d1-106">But sorting or comparing strings is not always a culture-sensitive operation.</span></span> <span data-ttu-id="880d1-107">Por exemplo, cadeias de caracteres que são usadas internamente por um aplicativo normalmente devem ser manipuladas de maneira idêntica em todas as culturas.</span><span class="sxs-lookup"><span data-stu-id="880d1-107">For example, strings that are used internally by an application typically should be handled identically across all cultures.</span></span> <span data-ttu-id="880d1-108">Quando os dados de cadeias de caracteres culturalmente independentes, como marcações XML, marcações HTML, nomes de usuário, caminhos de arquivo e nomes de objetos do sistema, são interpretados como se levassem em conta a cultura, o código do aplicativo pode estar sujeito a bugs sutis, desempenho ruim e, em alguns casos, problemas de segurança.</span><span class="sxs-lookup"><span data-stu-id="880d1-108">When culturally independent string data, such as XML tags, HTML tags, user names, file paths, and the names of system objects, are interpreted as if they were culture-sensitive, application code can be subject to subtle bugs, poor performance, and, in some cases, security issues.</span></span>

<span data-ttu-id="880d1-109">Este artigo examina os métodos de classificação, comparação e o uso de maiúsculas e minúsculas de cadeias de caracteres no .NET, apresenta recomendações para a seleção de um método de manipulação de cadeia de caracteres adequado e fornece informações adicionais sobre os métodos de manipulação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="880d1-109">This article examines the string sorting, comparison, and casing methods in .NET, presents recommendations for selecting an appropriate string-handling method, and provides additional information about string-handling methods.</span></span> <span data-ttu-id="880d1-110">Ela também examina como os dados formatados, como dados numéricos e dados de data e hora, são manipulados para exibição e armazenamento.</span><span class="sxs-lookup"><span data-stu-id="880d1-110">It also examines how formatted data, such as numeric data and date and time data, is handled for display and for storage.</span></span> 

<span data-ttu-id="880d1-111">Este artigo contém as seguintes seções:</span><span class="sxs-lookup"><span data-stu-id="880d1-111">This article contains the following sections:</span></span>

* [<span data-ttu-id="880d1-112">Recomendações para uso da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="880d1-112">Recommendations for string usage</span></span>](#recommendations-for-string-usage)

* [<span data-ttu-id="880d1-113">Especificação explícita de comparações da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="880d1-113">Specifying string comparisons explicitly</span></span>](#specifying-string-comparisons-explicitly)

* [<span data-ttu-id="880d1-114">Os detalhes da comparação de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="880d1-114">The details of string comparison</span></span>](#the-details-of-string-comparison)

* [<span data-ttu-id="880d1-115">Escolha de um membro StringComparison para a chamada de método</span><span class="sxs-lookup"><span data-stu-id="880d1-115">Choosing a StringComparison member for your method call</span></span>](#choosing-a-stringcomparison-member-for-your-method-call)

* [<span data-ttu-id="880d1-116">Métodos comuns de comparação da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="880d1-116">Common string comparison methods</span></span>](#common-string-comparison-methods)

* [<span data-ttu-id="880d1-117">Métodos que realizam comparação indireta de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="880d1-117">Methods that perform string comparison indirectly</span></span>](#methods-that-perform-string-comparison-indirectly)

* [<span data-ttu-id="880d1-118">Exibição e persistência de dados formatados</span><span class="sxs-lookup"><span data-stu-id="880d1-118">Displaying and persisting formatted data</span></span>](#displaying-and-persisting-formatted-data)

## <a name="recommendations-for-string-usage"></a><span data-ttu-id="880d1-119">Recomendações para uso da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="880d1-119">Recommendations for string usage</span></span>

<span data-ttu-id="880d1-120">Ao desenvolver com o .NET, siga estas recomendações simples quando usar cadeias de caracteres:</span><span class="sxs-lookup"><span data-stu-id="880d1-120">When you develop with .NET, follow these simple recommendations when you use strings:</span></span> 

* <span data-ttu-id="880d1-121">Use sobrecargas que especificam explicitamente as regras de comparação de cadeias de caracteres para operações de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="880d1-121">Use overloads that explicitly specify the string comparison rules for string operations.</span></span> <span data-ttu-id="880d1-122">Normalmente, isso envolve chamar uma sobrecarga de método que tem um parâmetro do tipo [StringComparison](xref:System.StringComparison).</span><span class="sxs-lookup"><span data-stu-id="880d1-122">Typically, this involves calling a method overload that has a parameter of type [StringComparison](xref:System.StringComparison).</span></span>

* <span data-ttu-id="880d1-123">Use [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) ou [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) para comparações como seu padrão seguro para a correspondência de cadeia de caracteres independente de cultura.</span><span class="sxs-lookup"><span data-stu-id="880d1-123">Use [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) or [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) for comparisons as your safe default for culture-agnostic string matching.</span></span>

* <span data-ttu-id="880d1-124">Use comparações com [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) ou [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) para melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="880d1-124">Use comparisons with [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) or [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) for better performance.</span></span>

* <span data-ttu-id="880d1-125">Use operações de cadeia de caracteres que se baseiam em [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) ao exibir a saída para o usuário.</span><span class="sxs-lookup"><span data-stu-id="880d1-125">Use string operations that are based on [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) when you display output to the user.</span></span>

* <span data-ttu-id="880d1-126">Use valores [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) ou [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) não linguísticos em vez de operações de cadeias de caracteres com base em [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) quando a comparação for linguisticamente irrelevante (simbólica, por exemplo).</span><span class="sxs-lookup"><span data-stu-id="880d1-126">Use the non-linguistic [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) or [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) values instead of string operations based on [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) when the comparison is linguistically irrelevant (symbolic, for example).</span></span>

* <span data-ttu-id="880d1-127">Use o método [String.ToUpperInvariant](xref:System.String.ToUpperInvariant) em vez do método [String.ToLowerInvariant](xref:System.String.ToLowerInvariant) ao normalizar cadeias de caracteres para comparação.</span><span class="sxs-lookup"><span data-stu-id="880d1-127">Use the [String.ToUpperInvariant](xref:System.String.ToUpperInvariant) method instead of the [String.ToLowerInvariant](xref:System.String.ToLowerInvariant) method when you normalize strings for comparison.</span></span>

* <span data-ttu-id="880d1-128">Use uma sobrecarga do método [String](xref:System.String) `Equals` para testar se duas cadeias de caracteres são iguais.</span><span class="sxs-lookup"><span data-stu-id="880d1-128">Use an overload of the [String](xref:System.String) `Equals` method to test whether two strings are equal.</span></span>

* <span data-ttu-id="880d1-129">Use uma sobrecarga dos métodos [String](xref:System.String) `Compare` e [String.CompareTo](xref:System.String.CompareTo(System.String)) para classificar as cadeias de caracteres, não para verificar a igualdade.</span><span class="sxs-lookup"><span data-stu-id="880d1-129">Use an overload of the [String](xref:System.String) `Compare` and [String.CompareTo](xref:System.String.CompareTo(System.String)) methods to sort strings, not to check for equality.</span></span>

* <span data-ttu-id="880d1-130">Use a formatação que leva em conta a cultura para exibir dados que não são de cadeias de caracteres, como números e datas, em uma interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="880d1-130">Use culture-sensitive formatting to display non-string data, such as numbers and dates, in a user interface.</span></span> <span data-ttu-id="880d1-131">Use a formatação com a cultura invariável para persistir os dados que não são de cadeias de caracteres no formato de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="880d1-131">Use formatting with the invariant culture to persist non-string data in string form.</span></span>

<span data-ttu-id="880d1-132">Evite as práticas a seguir ao usar cadeias de caracteres:</span><span class="sxs-lookup"><span data-stu-id="880d1-132">Avoid the following practices when you use strings:</span></span>

* <span data-ttu-id="880d1-133">Não use sobrecargas que não especificam explicita ou implicitamente as regras de comparação de cadeias de caracteres para operações de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="880d1-133">Do not use overloads that do not explicitly or implicitly specify the string comparison rules for string operations.</span></span> 

* <span data-ttu-id="880d1-134">Não use uma sobrecarga dos métodos [String](xref:System.String) `Compare` ou [String.CompareTo](xref:System.String.CompareTo(System.String)) e teste para um valor retornado de zero para determinar se duas cadeias de caracteres são iguais.</span><span class="sxs-lookup"><span data-stu-id="880d1-134">Do not use an overload of the [String](xref:System.String) `Compare` or [String.CompareTo](xref:System.String.CompareTo(System.String)) methods and test for a return value of zero to determine whether two strings are equal.</span></span>

* <span data-ttu-id="880d1-135">Não use a formatação que leva em conta a cultura para persistir dados numéricos ou dados de data e hora no formato de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="880d1-135">Do not use culture-sensitive formatting to persist numeric data or date and time data in string form.</span></span>

## <a name="specifying-string-comparisons-explicitly"></a><span data-ttu-id="880d1-136">Especificação explícita de comparações da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="880d1-136">Specifying string comparisons explicitly</span></span>

<span data-ttu-id="880d1-137">A maioria dos métodos de manipulação de cadeia de caracteres no .NET é sobrecarregada.</span><span class="sxs-lookup"><span data-stu-id="880d1-137">Most of the string manipulation methods in .NET are overloaded.</span></span> <span data-ttu-id="880d1-138">Normalmente, uma ou mais sobrecargas aceitam as configurações padrão, enquanto outras não aceitam nenhum padrão e definem a maneira exata em que as cadeias de caracteres devem ser comparadas ou manipuladas.</span><span class="sxs-lookup"><span data-stu-id="880d1-138">Typically, one or more overloads accept default settings, whereas others accept no defaults and instead define the precise way in which strings are to be compared or manipulated.</span></span> <span data-ttu-id="880d1-139">A maioria dos métodos que não dependem de padrões inclui um parâmetro do tipo [StringComparison](xref:System.StringComparison), que é uma enumeração que especifica explicitamente as regras de comparação de cadeia de caracteres por cultura e maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="880d1-139">Most of the methods that do not rely on defaults include a parameter of type [StringComparison](xref:System.StringComparison), which is an enumeration that explicitly specifies rules for string comparison by culture and case.</span></span> <span data-ttu-id="880d1-140">A tabela a seguir descreve os membros de enumeração de [StringComparison](xref:System.StringComparison).</span><span class="sxs-lookup"><span data-stu-id="880d1-140">The following table describes the [StringComparison](xref:System.StringComparison) enumeration members.</span></span> 

<span data-ttu-id="880d1-141">Membro de StringComparison</span><span class="sxs-lookup"><span data-stu-id="880d1-141">StringComparison member</span></span> | <span data-ttu-id="880d1-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="880d1-142">Description</span></span>
----------------------- | -----------
[<span data-ttu-id="880d1-143">StringComparison.CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="880d1-143">StringComparison.CurrentCulture</span></span>](xref:System.StringComparison.CurrentCulture) | <span data-ttu-id="880d1-144">Executa uma comparação que diferencia maiúsculas de minúsculas usando a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="880d1-144">Performs a case-sensitive comparison using the current culture.</span></span>
[<span data-ttu-id="880d1-145">CurrentCultureIgnoreCase</span><span class="sxs-lookup"><span data-stu-id="880d1-145">CurrentCultureIgnoreCase</span></span>](xref:System.StringComparison.CurrentCultureIgnoreCase) | <span data-ttu-id="880d1-146">Executa uma comparação que não diferencia maiúsculas de minúsculas usando a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="880d1-146">Performs a case-insensitive comparison using the current culture.</span></span>
[<span data-ttu-id="880d1-147">StringComparison.Ordinal</span><span class="sxs-lookup"><span data-stu-id="880d1-147">StringComparison.Ordinal</span></span>](xref:System.StringComparison.Ordinal) | <span data-ttu-id="880d1-148">Executa uma comparação ordinal.</span><span class="sxs-lookup"><span data-stu-id="880d1-148">Performs an ordinal comparison.</span></span>
[<span data-ttu-id="880d1-149">StringComparison.OrdinalIgnoreCase</span><span class="sxs-lookup"><span data-stu-id="880d1-149">StringComparison.OrdinalIgnoreCase</span></span>](xref:System.StringComparison.OrdinalIgnoreCase) | <span data-ttu-id="880d1-150">Executa uma comparação ordinal que não diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="880d1-150">Performs a case-insensitive ordinal comparison.</span></span>

<span data-ttu-id="880d1-151">Por exemplo, o método [String](xref:System.String) `IndexOf`, que retorna um índice de uma subcadeia de caracteres em um objeto [String](xref:System.String) que corresponde a um caractere ou cadeia de caracteres, tem nove sobrecargas:</span><span class="sxs-lookup"><span data-stu-id="880d1-151">For example, the [String](xref:System.String) `IndexOf` method, which returns the index of a substring in a [String](xref:System.String) object that matches either a character or a string, has nine overloads:</span></span>

* <span data-ttu-id="880d1-152">[IndexOf(Char)](xref:System.String.IndexOf(System.Char)), [IndexOf(Char, Int32)](xref:System.String.IndexOf(System.Char,System.Int32)) e [IndexOf(Char, Int32, Int32)](xref:System.String.IndexOf(System.Char,System.Int32,System.Int32)), que por padrão executam uma pesquisa ordinal (diferencia maiúsculas de minúsculas e não leva em consideração a cultura) para um caractere na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="880d1-152">[IndexOf(Char)](xref:System.String.IndexOf(System.Char)), [IndexOf(Char, Int32)](xref:System.String.IndexOf(System.Char,System.Int32)), and [IndexOf(Char, Int32, Int32)](xref:System.String.IndexOf(System.Char,System.Int32,System.Int32)), which by default perform an ordinal (case-sensitive and culture-insensitive) search for a character in the string.</span></span>

* <span data-ttu-id="880d1-153">[IndexOf(String)](xref:System.String.IndexOf(System.String)), [IndexOf(String, Int32)](xref:System.String.IndexOf(System.String,System.Int32)) e [IndexOf(String, Int32, Int32)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32)), que por padrão executam uma pesquisa que diferencia maiúsculas de minúsculas e leva em consideração a cultura para uma subcadeia de caracteres na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="880d1-153">[IndexOf(String)](xref:System.String.IndexOf(System.String)), [IndexOf(String, Int32)](xref:System.String.IndexOf(System.String,System.Int32)), and [IndexOf(String, Int32, Int32)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32)), which by default perform a case-sensitive and culture-sensitive search for a substring in the string.</span></span>

* <span data-ttu-id="880d1-154">[IndexOf(String, StringComparison)](xref:System.String.IndexOf(System.String,System.StringComparison)), [IndexOf(String, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.StringComparison)) e [IndexOf(String, Int32, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32,System.StringComparison)), que incluem um parâmetro de tipo StringComparison que permite que a forma de comparação seja especificada.</span><span class="sxs-lookup"><span data-stu-id="880d1-154">[IndexOf(String, StringComparison)](xref:System.String.IndexOf(System.String,System.StringComparison)), [IndexOf(String, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.StringComparison)), and [IndexOf(String, Int32, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32,System.StringComparison)), which include a parameter of type StringComparison that allows the form of the comparison to be specified.</span></span>

<span data-ttu-id="880d1-155">É recomendável que você selecione uma sobrecarga que não usa valores padrão, pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="880d1-155">We recommend that you select an overload that does not use default values, for the following reasons:</span></span>

* <span data-ttu-id="880d1-156">Algumas sobrecargas com parâmetros padrão (aqueles que pesquisam um [Char](xref:System.Char) na instância de cadeia de caracteres) realizam uma comparação ordinal, enquanto outras (aquelas que pesquisam uma cadeia de caracteres na instância de cadeia de caracteres) levam em consideração a cultura.</span><span class="sxs-lookup"><span data-stu-id="880d1-156">Some overloads with default parameters (those that search for a [Char](xref:System.Char) in the string instance) perform an ordinal comparison, whereas others (those that search for a string in the string instance) are culture-sensitive.</span></span> <span data-ttu-id="880d1-157">É difícil lembrar qual método usa o valor padrão e é fácil confundir as sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="880d1-157">It is difficult to remember which method uses which default value, and easy to confuse the overloads.</span></span>

* <span data-ttu-id="880d1-158">A intenção do código que depende de valores padrão para chamadas de método não é clara.</span><span class="sxs-lookup"><span data-stu-id="880d1-158">The intent of the code that relies on default values for method calls is not clear.</span></span> <span data-ttu-id="880d1-159">No exemplo a seguir, que se baseia em padrões, é difícil saber se o desenvolvedor realmente planejava uma comparação ordinal ou linguística de duas cadeias de caracteres ou se uma diferença entre maiúsculas e minúsculas entre `protocol` e “http” pode fazer com que o teste de igualdade retorne `false`.</span><span class="sxs-lookup"><span data-stu-id="880d1-159">In the following example, which relies on defaults, it is difficult to know whether the developer actually intended an ordinal or a linguistic comparison of two strings, or whether a case difference between `protocol` and "http" might cause the test for equality to return `false`.</span></span>

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

<span data-ttu-id="880d1-160">Em geral, é recomendável que você chame um método que não se baseie em padrões, pois ele torna a intenção do código clara.</span><span class="sxs-lookup"><span data-stu-id="880d1-160">In general, we recommend that you call a method that does not rely on defaults, because it makes the intent of the code unambiguous.</span></span> <span data-ttu-id="880d1-161">Isso, por sua vez, torna o código mais legível e fácil de depurar e manter.</span><span class="sxs-lookup"><span data-stu-id="880d1-161">This, in turn, makes the code more readable and easier to debug and maintain.</span></span> <span data-ttu-id="880d1-162">O exemplo a seguir aborda as questões levantadas sobre o exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="880d1-162">The following example addresses the questions raised about the previous example.</span></span> <span data-ttu-id="880d1-163">Ele deixa claro que a comparação ordinal é usada e que as diferenças de maiúsculas e minúsculas são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="880d1-163">It makes it clear that ordinal comparison is used and that differences in case are ignored.</span></span> 

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

## <a name="the-details-of-string-comparison"></a><span data-ttu-id="880d1-164">Os detalhes da comparação de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="880d1-164">The details of string comparison</span></span>

<span data-ttu-id="880d1-165">A comparação de cadeia de caracteres é o centro de muitas operações relacionadas à cadeia de caracteres, especialmente a classificação e teste de igualdade.</span><span class="sxs-lookup"><span data-stu-id="880d1-165">String comparison is the heart of many string-related operations, particularly sorting and testing for equality.</span></span> <span data-ttu-id="880d1-166">As cadeias de caracteres são classificadas em uma determinada ordem: se “my” aparece antes de “string” em uma lista classificada de cadeias de caracteres, “my” deve comparar menos que ou igual a “string”.</span><span class="sxs-lookup"><span data-stu-id="880d1-166">Strings sort in a determined order: If "my" appears before "string" in a sorted list of strings, "my" must compare less than or equal to "string".</span></span> <span data-ttu-id="880d1-167">Além disso, a comparação define implicitamente a igualdade.</span><span class="sxs-lookup"><span data-stu-id="880d1-167">Additionally, comparison implicitly defines equality.</span></span> <span data-ttu-id="880d1-168">A operação de comparação retorna zero para cadeias de caracteres que considerar iguais.</span><span class="sxs-lookup"><span data-stu-id="880d1-168">The comparison operation returns zero for strings it deems equal.</span></span> <span data-ttu-id="880d1-169">Uma boa interpretação é que nenhuma cadeia de caracteres é menor que a outra.</span><span class="sxs-lookup"><span data-stu-id="880d1-169">A good interpretation is that neither string is less than the other.</span></span> <span data-ttu-id="880d1-170">Operações mais significativas envolvendo cadeias de caracteres incluem um ou ambos destes procedimentos: comparação com outra cadeia de caracteres e execução de uma operação de classificação bem definida.</span><span class="sxs-lookup"><span data-stu-id="880d1-170">Most meaningful operations involving strings include one or both of these procedures: comparing with another string, and executing a well-defined sort operation.</span></span>

<span data-ttu-id="880d1-171">No entanto, avaliar duas cadeias de caracteres quanto à igualdade ou ordem de classificação não gera um único resultado correto, o resultado depende dos critérios usados para comparar as cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="880d1-171">However, evaluating two strings for equality or sort order does not yield a single, correct result; the outcome depends on the criteria used to compare the strings.</span></span> <span data-ttu-id="880d1-172">Em particular, as comparações de cadeia de caracteres ordinais ou baseadas no uso de maiúsculas e minúsculas e convenções classificação da cultura atual ou da cultura invariável (uma cultura independente de localidade com base no idioma inglês) podem gerar resultados diferentes.</span><span class="sxs-lookup"><span data-stu-id="880d1-172">In particular, string comparisons that are ordinal or that are based on the casing and sorting conventions of the current culture or the invariant culture (a locale-agnostic culture based on the English language) may produce different results.</span></span>

### <a name="string-comparisons-that-use-the-current-culture"></a><span data-ttu-id="880d1-173">Comparações de cadeia de caracteres que usam a cultura atual</span><span class="sxs-lookup"><span data-stu-id="880d1-173">String comparisons that use the current culture</span></span>

<span data-ttu-id="880d1-174">Um critério envolve o uso das convenções da cultura atual ao comparar cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="880d1-174">One criterion involves using the conventions of the current culture when comparing strings.</span></span> <span data-ttu-id="880d1-175">As comparações que se baseiam na cultura atual usam a localidade ou a cultura atual do thread.</span><span class="sxs-lookup"><span data-stu-id="880d1-175">Comparisons that are based on the current culture use the thread's current culture or locale.</span></span> <span data-ttu-id="880d1-176">Você deve sempre usar comparações que se baseiam na cultura atual quando os dados forem linguisticamente relevantes e quando eles refletirem a interação do usuário que leva em conta a cultura.</span><span class="sxs-lookup"><span data-stu-id="880d1-176">You should always use comparisons that are based on the current culture when data is linguistically relevant, and when it reflects culture-sensitive user interaction.</span></span> 

<span data-ttu-id="880d1-177">No entanto, o comportamento da comparação e do uso de maiúsculas e minúsculas no .NET muda quando a cultura muda.</span><span class="sxs-lookup"><span data-stu-id="880d1-177">However, comparison and casing behavior in .NET changes when the culture changes.</span></span> <span data-ttu-id="880d1-178">Isso acontece quando um aplicativo é executado em um computador que tem uma cultura diferente do computador em que o aplicativo foi desenvolvido ou quando o thread em execução muda sua cultura.</span><span class="sxs-lookup"><span data-stu-id="880d1-178">This happens when an application executes on a computer that has a different culture than the computer on which the application was developed, or when the executing thread changes its culture.</span></span> <span data-ttu-id="880d1-179">Esse comportamento é intencional, mas permanece não óbvio para muitos desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="880d1-179">This behavior is intentional, but it remains non-obvious to many developers.</span></span> <span data-ttu-id="880d1-180">O exemplo a seguir ilustra as diferenças na ordem de classificação entre as culturas de inglês dos EUA ("en-US") e sueco ("sv-SE").</span><span class="sxs-lookup"><span data-stu-id="880d1-180">The following example illustrates differences in sort order between the U.S. English ("en-US") and Swedish ("sv-SE") cultures.</span></span> <span data-ttu-id="880d1-181">Observe que as palavras "ångström", "Windows" e "Visual Studio" aparecem em posições diferentes nas matrizes de cadeias de caracteres classificadas.</span><span class="sxs-lookup"><span data-stu-id="880d1-181">Note that the words "ångström", "Windows", and "Visual Studio" appear in different positions in the sorted string arrays.</span></span>

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

<span data-ttu-id="880d1-182">As comparações que não diferenciam maiúsculas de minúsculas que usam a cultura atual são iguais às comparações que levam em conta a cultura, exceto que elas ignoram as maiúsculas e minúsculas conforme determinado pela cultura atual do thread.</span><span class="sxs-lookup"><span data-stu-id="880d1-182">Case-insensitive comparisons that use the current culture are the same as culture-sensitive comparisons, except that they ignore case as dictated by the thread's current culture.</span></span> <span data-ttu-id="880d1-183">Esse comportamento pode se manifestar em ordens de classificação também.</span><span class="sxs-lookup"><span data-stu-id="880d1-183">This behavior may manifest itself in sort orders as well.</span></span> 

<span data-ttu-id="880d1-184">As comparações que usam a semântica de cultura atual são o padrão para os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="880d1-184">Comparisons that use current culture semantics are the default for the following methods:</span></span>

* <span data-ttu-id="880d1-185">Sobrecargas [String](xref:System.String) `Compare` que não incluem um parâmetro [StringComparison](xref:System.StringComparison).</span><span class="sxs-lookup"><span data-stu-id="880d1-185">[String](xref:System.String) `Compare` overloads that do not include a [StringComparison](xref:System.StringComparison) parameter.</span></span>

* <span data-ttu-id="880d1-186">Sobrecargas [String.CompareTo](xref:System.String.CompareTo(System.String)).</span><span class="sxs-lookup"><span data-stu-id="880d1-186">[String.CompareTo](xref:System.String.CompareTo(System.String)) overloads.</span></span>

* <span data-ttu-id="880d1-187">O método [String.StartsWith(String)](xref:System.String.StartsWith(System.String)) padrão.</span><span class="sxs-lookup"><span data-stu-id="880d1-187">The default [String.StartsWith(String)](xref:System.String.StartsWith(System.String)) method.</span></span> 

* <span data-ttu-id="880d1-188">O método [String.EndsWith(String)](xref:System.String.EndsWith(System.String)) padrão.</span><span class="sxs-lookup"><span data-stu-id="880d1-188">The default [String.EndsWith(String)](xref:System.String.EndsWith(System.String)) method.</span></span>

* <span data-ttu-id="880d1-189">Sobrecargas [String](xref:System.String) `IndexOf` que aceitam uma [String](xref:System.String) como um parâmetro de pesquisa e que não têm um parâmetro [StringComparison](xref:System.StringComparison).</span><span class="sxs-lookup"><span data-stu-id="880d1-189">[String](xref:System.String) `IndexOf` overloads that accept a [String](xref:System.String) as a search parameter and that do not have a [StringComparison](xref:System.StringComparison) parameter.</span></span>

* <span data-ttu-id="880d1-190">Sobrecargas [String](xref:System.String) `LastIndexOf` que aceitam uma [String](xref:System.String) como um parâmetro de pesquisa e que não têm um parâmetro [StringComparison](xref:System.StringComparison).</span><span class="sxs-lookup"><span data-stu-id="880d1-190">[String](xref:System.String) `LastIndexOf` overloads that accept a [String](xref:System.String) as a search parameter and that do not have a [StringComparison](xref:System.StringComparison) parameter.</span></span>

<span data-ttu-id="880d1-191">Em qualquer caso, é recomendável que você chame uma sobrecarga que tenha um parâmetro [StringComparison](xref:System.StringComparison) para deixar a intenção da chamada do método clara.</span><span class="sxs-lookup"><span data-stu-id="880d1-191">In any case, we recommend that you call an overload that has a [StringComparison](xref:System.StringComparison) parameter to make the intent of the method call clear.</span></span> 

<span data-ttu-id="880d1-192">Bugs sutis e não tão sutis podem surgir quando dados de cadeias de caracteres não linguísticas são interpretados linguisticamente ou quando os dados da cadeia de caracteres de uma cultura específica são interpretados usando as convenções de outra cultura.</span><span class="sxs-lookup"><span data-stu-id="880d1-192">Subtle and not so subtle bugs can emerge when non-linguistic string data is interpreted linguistically, or when string data from a particular culture is interpreted using the conventions of another culture.</span></span> <span data-ttu-id="880d1-193">O exemplo canônico é o problema do I turco.</span><span class="sxs-lookup"><span data-stu-id="880d1-193">The canonical example is the Turkish-I problem.</span></span>

<span data-ttu-id="880d1-194">Para quase todos os alfabetos latinos, incluindo o do inglês dos EUA, o caractere "i" (\u0069) é a versão em letra minúscula do caractere "I" (\u0049).</span><span class="sxs-lookup"><span data-stu-id="880d1-194">For nearly all Latin alphabets, including U.S. English, the character "i" (\u0069) is the lowercase version of the character "I" (\u0049).</span></span> <span data-ttu-id="880d1-195">Essa regra de maiúsculas e minúsculas rapidamente se torna o padrão para alguém programando em tal cultura.</span><span class="sxs-lookup"><span data-stu-id="880d1-195">This casing rule quickly becomes the default for someone programming in such a culture.</span></span> <span data-ttu-id="880d1-196">No entanto, o alfabeto turco ("tr-TR") inclui um caractere "I com um ponto", "İ" (\u0130), que é a versão maiúscula de "i".</span><span class="sxs-lookup"><span data-stu-id="880d1-196">However, the Turkish ("tr-TR") alphabet includes an "I with a dot" character "İ" (\u0130), which is the capital version of "i".</span></span> <span data-ttu-id="880d1-197">O turco também inclui um caractere minúsculo "i sem um ponto", "ı" (\u0131), que em maiúscula é “I”.</span><span class="sxs-lookup"><span data-stu-id="880d1-197">Turkish also includes a lowercase "i without a dot" character, "ı" (\u0131), which capitalizes to "I".</span></span> <span data-ttu-id="880d1-198">Esse comportamento também ocorre na cultura azerbaidjana ("az").</span><span class="sxs-lookup"><span data-stu-id="880d1-198">This behavior occurs in the Azerbaijani ("az") culture as well.</span></span>

<span data-ttu-id="880d1-199">Portanto, as suposições feitas sobre a colocação do "i" em maiúscula ou do "I" em minúscula não são válidas entre todas as culturas.</span><span class="sxs-lookup"><span data-stu-id="880d1-199">Therefore, assumptions made about capitalizing "i" or lowercasing "I" are not valid among all cultures.</span></span> <span data-ttu-id="880d1-200">Se você usar as sobrecargas padrão para rotinas de comparação de cadeias de caracteres, elas estarão sujeitas à variação entre culturas.</span><span class="sxs-lookup"><span data-stu-id="880d1-200">If you use the default overloads for string comparison routines, they will be subject to variance between cultures.</span></span> <span data-ttu-id="880d1-201">Se os dados a serem comparados são forem linguísticos, o uso das sobrecargas padrão pode gerar resultados indesejáveis, como a tentativa a seguir de realizar uma comparação que não diferencia maiúsculas de minúsculas das cadeias de caracteres “file” e “FILE” ilustra.</span><span class="sxs-lookup"><span data-stu-id="880d1-201">If the data to be compared is non-linguistic, using the default overloads can produce undesirable results, as the following attempt to perform a case-insensitive comparison of the strings "file" and "FILE" illustrates.</span></span>

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

<span data-ttu-id="880d1-202">Essa comparação pode causar problemas significativos se a cultura for usada inadvertidamente nas configurações sensíveis à segurança, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="880d1-202">This comparison could cause significant problems if the culture is inadvertently used in security-sensitive settings, as in the following example.</span></span> <span data-ttu-id="880d1-203">Uma chamada de método, como `IsFileURI("file:")` retorna `true` se a cultura atual for inglês dos EUA, mas `false` se a cultura atual for turco.</span><span class="sxs-lookup"><span data-stu-id="880d1-203">A method call such as `IsFileURI("file:")` returns `true` if the current culture is U.S. English, but `false` if the current culture is Turkish.</span></span> <span data-ttu-id="880d1-204">Assim, em sistemas turcos, alguém poderia driblar as medidas de segurança que bloqueiam o acesso a URIs que não diferenciam maiúsculas de minúsculas que começam com “FILE:”.</span><span class="sxs-lookup"><span data-stu-id="880d1-204">Thus, on Turkish systems, someone could circumvent security measures that block access to case-insensitive URIs that begin with "FILE:".</span></span>

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

<span data-ttu-id="880d1-205">Nesse caso, como "file:" deve ser interpretado como um identificador não linguístico que não leva em conta a cultura, o código deveria ser escrito como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="880d1-205">In this case, because "file:" is meant to be interpreted as a non-linguistic, culture-insensitive identifier, the code should instead be written as shown in the following example.</span></span>

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

## <a name="ordinal-string-operations"></a><span data-ttu-id="880d1-206">Operações Ordinais da Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="880d1-206">Ordinal String Operations</span></span>

<span data-ttu-id="880d1-207">Especificar o valor [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) ou [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) em uma chamada de método significa uma comparação não linguística em que as funcionalidades de idiomas naturais são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="880d1-207">Specifying the [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) or [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) value in a method call signifies a non-linguistic comparison in which the features of natural languages are ignored.</span></span> <span data-ttu-id="880d1-208">Os métodos que são invocados com esses valores de [StringComparison](xref:System.StringComparison) baseiam as decisões de operação da cadeia de caracteres em comparações de byte simples em vez de no uso de maiúsculas e minúsculas ou tabelas de equivalência que são parametrizadas pela cultura.</span><span class="sxs-lookup"><span data-stu-id="880d1-208">Methods that are invoked with these [StringComparison](xref:System.StringComparison) values base string operation decisions on simple byte comparisons instead of casing or equivalence tables that are parameterized by culture.</span></span> <span data-ttu-id="880d1-209">Na maioria dos casos, essa abordagem se adapta melhor à interpretação pretendida de cadeias de caracteres, enquanto torna o código mais rápido e confiável.</span><span class="sxs-lookup"><span data-stu-id="880d1-209">In most cases, this approach best fits the intended interpretation of strings while making code faster and more reliable.</span></span> 

<span data-ttu-id="880d1-210">Comparações ordinais são comparações de cadeia de caracteres nas quais cada byte de cada cadeia de caracteres é comparado sem a interpretação linguística, por exemplo, “windows” não corresponde a “Windows”.</span><span class="sxs-lookup"><span data-stu-id="880d1-210">Ordinal comparisons are string comparisons in which each byte of each string is compared without linguistic interpretation; for example, "windows" does not match "Windows".</span></span> <span data-ttu-id="880d1-211">Use essa comparação quando o contexto determinar que as cadeias de caracteres devem corresponder exatamente ou exigir uma política de correspondência conservadora.</span><span class="sxs-lookup"><span data-stu-id="880d1-211">Use this comparison when the context dictates that strings should be matched exactly or demands conservative matching policy.</span></span> <span data-ttu-id="880d1-212">Além disso, a comparação ordinal é a operação de comparação mais rápida porque ela não aplica nenhuma regra linguística ao determinar um resultado.</span><span class="sxs-lookup"><span data-stu-id="880d1-212">Additionally, ordinal comparison is the fastest comparison operation because it applies no linguistic rules when determining a result.</span></span>

<span data-ttu-id="880d1-213">As cadeias de caracteres no .NET podem conter caracteres nulos inseridos.</span><span class="sxs-lookup"><span data-stu-id="880d1-213">Strings in .NET can contain embedded null characters.</span></span> <span data-ttu-id="880d1-214">Uma das diferenças mais clara entre a comparação ordinal e a que leva em conta a cultura (incluindo comparações que usam a cultura invariável) diz respeito à manipulação de caracteres nulos inseridos em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="880d1-214">One of the clearest differences between ordinal and culture-sensitive comparison (including comparisons that use the invariant culture) concerns the handling of embedded null characters in a string.</span></span> <span data-ttu-id="880d1-215">Esses caracteres são ignorados quando você usa os métodos [String](xref:System.String) `Compare` e [String](xref:System.String) `Equals` para realizar comparações que levam em conta a cultura (incluindo comparações que usam a cultura invariável).</span><span class="sxs-lookup"><span data-stu-id="880d1-215">These characters are ignored when you use the [String](xref:System.String) `Compare` and [String](xref:System.String) `Equals` methods to perform culture-sensitive comparisons (including comparisons that use the invariant culture).</span></span> <span data-ttu-id="880d1-216">Como resultado, em comparações que levam em conta a cultura, cadeias de caracteres que contêm caracteres nulos inseridos podem ser consideradas iguais a cadeias de caracteres que não contêm.</span><span class="sxs-lookup"><span data-stu-id="880d1-216">As a result, in culture-sensitive comparisons, strings that contain embedded null characters can be considered equal to strings that do not.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="880d1-217">Embora os métodos de comparação de cadeia de caracteres ignorem caracteres nulos inseridos, os métodos de pesquisa de cadeia de caracteres como [String.Contains](xref:System.String.Contains(System.String)), [String.EndsWith](xref:System.String.EndsWith(System.String)), [String.IndexOf](xref:System.String.IndexOf(System.Char)), [String.LastIndexOf](xref:System.String.LastIndexOf(System.String)) e [String.StartsWith](xref:System.String.StartsWith(System.String)) não.</span><span class="sxs-lookup"><span data-stu-id="880d1-217">Although string comparison methods disregard embedded null characters, string search methods such as [String.Contains](xref:System.String.Contains(System.String)), [String.EndsWith](xref:System.String.EndsWith(System.String)), [String.IndexOf](xref:System.String.IndexOf(System.Char)), [String.LastIndexOf](xref:System.String.LastIndexOf(System.String)), and [String.StartsWith](xref:System.String.StartsWith(System.String)) do not.</span></span> 

<span data-ttu-id="880d1-218">O exemplo a seguir executa uma comparação que leva em conta a cultura da cadeia de caracteres "Aa" com uma cadeia de caracteres semelhante que contém vários caracteres nulos inseridos entre "A" e "a" e mostra como as duas cadeias de caracteres são consideradas iguais.</span><span class="sxs-lookup"><span data-stu-id="880d1-218">The following example performs a culture-sensitive comparison of the string "Aa" with a similar string that contains several embedded null characters between "A" and "a", and shows how the two strings are considered equal.</span></span> 

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

<span data-ttu-id="880d1-219">No entanto, as cadeias de caracteres não são consideradas iguais ao usar a comparação ordinal, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="880d1-219">However, the strings are not considered equal when you use ordinal comparison, as the following example shows.</span></span>

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

<span data-ttu-id="880d1-220">As comparações ordinais que não diferenciam maiúsculas de minúsculas são a próxima abordagem conservadora.</span><span class="sxs-lookup"><span data-stu-id="880d1-220">Case-insensitive ordinal comparisons are the next most conservative approach.</span></span> <span data-ttu-id="880d1-221">Essas comparações ignoram a maioria das maiúsculas e minúsculas, por exemplo, "windows" corresponde a "Windows".</span><span class="sxs-lookup"><span data-stu-id="880d1-221">These comparisons ignore most casing; for example, "windows" matches "Windows".</span></span> <span data-ttu-id="880d1-222">Ao lidar com caracteres ASCII, essa política é equivalente a [StringComparison.Ordinal](xref:System.StringComparison.Ordinal), exceto que ela ignora as maiúsculas e minúsculas de ASCII normais.</span><span class="sxs-lookup"><span data-stu-id="880d1-222">When dealing with ASCII characters, this policy is equivalent to [StringComparison.Ordinal](xref:System.StringComparison.Ordinal), except that it ignores the usual ASCII casing.</span></span> <span data-ttu-id="880d1-223">Portanto, qualquer caractere em [A, Z] (\u0041-\u005A) corresponde ao caractere correspondente em [a,z] (\u0061-\007A).</span><span class="sxs-lookup"><span data-stu-id="880d1-223">Therefore, any character in [A, Z] (\u0041-\u005A) matches the corresponding character in [a,z] (\u0061-\007A).</span></span> <span data-ttu-id="880d1-224">As maiúsculas e minúsculas fora do intervalo de ASCII usam as tabelas de cultura invariável.</span><span class="sxs-lookup"><span data-stu-id="880d1-224">Casing outside the ASCII range uses the invariant culture's tables.</span></span> <span data-ttu-id="880d1-225">Portanto, a comparação a seguir:</span><span class="sxs-lookup"><span data-stu-id="880d1-225">Therefore, the following comparison:</span></span>

```csharp
String.Compare(strA, strB, StringComparison.OrdinalIgnoreCase);
```

```vb
String.Compare(strA, strB, StringComparison.OrdinalIgnoreCase)
```

<span data-ttu-id="880d1-226">é equivalente a (mas mais rápida do que) esta comparação:</span><span class="sxs-lookup"><span data-stu-id="880d1-226">is equivalent to (but faster than) this comparison:</span></span> 

```csharp
String.Compare(strA.ToUpperInvariant(), strB.ToUpperInvariant(), 
               StringComparison.Ordinal);
```

```vb
String.Compare(strA.ToUpperInvariant(), strB.ToUpperInvariant(), 
               StringComparison.Ordinal)
```

<span data-ttu-id="880d1-227">Essas comparações ainda são muito rápidas.</span><span class="sxs-lookup"><span data-stu-id="880d1-227">These comparisons are still very fast.</span></span>

<span data-ttu-id="880d1-228">Ambas [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) e [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) usam os valores binários diretamente e são mais adequadas para correspondência.</span><span class="sxs-lookup"><span data-stu-id="880d1-228">Both [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) and [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) use the binary values directly, and are best suited for matching.</span></span> <span data-ttu-id="880d1-229">Quando você não tiver certeza sobre as configurações de comparação, use um destes dois valores.</span><span class="sxs-lookup"><span data-stu-id="880d1-229">When you are not sure about your comparison settings, use one of these two values.</span></span> <span data-ttu-id="880d1-230">No entanto, como elas executam uma comparação byte por byte, elas não classificam por uma ordem de classificação linguística (como um dicionário de inglês), mas por ordem de classificação binária.</span><span class="sxs-lookup"><span data-stu-id="880d1-230">However, because they perform a byte-by-byte comparison, they do not sort by a linguistic sort order (like an English dictionary) but by a binary sort order.</span></span> <span data-ttu-id="880d1-231">Os resultados podem parecer estranhos na maioria dos contextos se exibido aos usuários.</span><span class="sxs-lookup"><span data-stu-id="880d1-231">The results may look odd in most contexts if displayed to users.</span></span>

<span data-ttu-id="880d1-232">A semântica ordinal é o padrão para sobrecargas [String](xref:System.String) `Equals` que não incluem um argumento [StringComparison](xref:System.StringComparison) (incluindo o operador de igualdade).</span><span class="sxs-lookup"><span data-stu-id="880d1-232">Ordinal semantics are the default for [String](xref:System.String) `Equals` overloads that do not include a [StringComparison](xref:System.StringComparison) argument (including the equality operator).</span></span> <span data-ttu-id="880d1-233">Em qualquer caso, é recomendável que você chame uma sobrecarga que tenha um parâmetro [StringComparison](xref:System.StringComparison).</span><span class="sxs-lookup"><span data-stu-id="880d1-233">In any case, we recommend that you call an overload that has a [StringComparison](xref:System.StringComparison) parameter.</span></span>

### <a name="string-operations-that-use-the-invariant-culture"></a><span data-ttu-id="880d1-234">Operações da cadeia de caracteres que usam a cultura invariável</span><span class="sxs-lookup"><span data-stu-id="880d1-234">String operations that use the invariant culture</span></span>

<span data-ttu-id="880d1-235">As comparações com a cultura invariável usam a propriedade [CompareInfo](xref:System.Globalization.CompareInfo) retornada pela propriedade [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) estática.</span><span class="sxs-lookup"><span data-stu-id="880d1-235">Comparisons with the invariant culture use the [CompareInfo](xref:System.Globalization.CompareInfo) property returned by the static [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) property.</span></span> <span data-ttu-id="880d1-236">Esse comportamento é o mesmo em todos os sistemas, ele converte qualquer caractere fora de seu intervalo no que ele acredita que sejam caracteres invariáveis equivalentes.</span><span class="sxs-lookup"><span data-stu-id="880d1-236">This behavior is the same on all systems; it translates any characters outside its range into what it believes are equivalent invariant characters.</span></span> <span data-ttu-id="880d1-237">Essa política pode ser útil para manter um conjunto de comportamentos de cadeia de caracteres entre culturas, mas geralmente fornece resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="880d1-237">This policy can be useful for maintaining one set of string behavior across cultures, but it often provides unexpected results.</span></span>

<span data-ttu-id="880d1-238">As comparações que não diferenciam maiúsculas de minúsculas com a cultura invariável usam a propriedade [CompareInfo](xref:System.Globalization.CompareInfo) estática retornada pela propriedade [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) estática para informações de comparação também.</span><span class="sxs-lookup"><span data-stu-id="880d1-238">Case-insensitive comparisons with the invariant culture use the static [CompareInfo](xref:System.Globalization.CompareInfo) property returned by the static [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) property for comparison information as well.</span></span> <span data-ttu-id="880d1-239">As diferenças de maiúsculas e minúsculas entre esses caracteres convertidos são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="880d1-239">Any case differences among these translated characters are ignored.</span></span>

<span data-ttu-id="880d1-240">O objeto [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) objeto faz um método [String](xref:System.String) `Compare` interpretar determinados conjuntos de caracteres como equivalentes.</span><span class="sxs-lookup"><span data-stu-id="880d1-240">The [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) object makes a [String](xref:System.String) `Compare` method interpret certain sets of characters as equivalent.</span></span> <span data-ttu-id="880d1-241">Por exemplo, a equivalência a seguir é válida na cultura invariável:</span><span class="sxs-lookup"><span data-stu-id="880d1-241">For example, the following equivalence is valid under the invariant culture:</span></span>

<span data-ttu-id="880d1-242">InvariantCulture: a + ̊ = å</span><span class="sxs-lookup"><span data-stu-id="880d1-242">InvariantCulture: a + ̊ = å</span></span>

<span data-ttu-id="880d1-243">O caractere da letra A minúscula latina “a” (\u0061), quando ele está próximo ao caractere de anel superior combinável "+ " ̊" (\u030a), é interpretado como a letra A minúscula latina com o caractere de anel superior "å" (\u00e5).</span><span class="sxs-lookup"><span data-stu-id="880d1-243">The latin small lette A character "a" (\u0061), when it is next to the combining ring above character "+ " ̊" (\u030a), is interpreted as the latin small letter A with ring above character "å" (\u00e5).</span></span> <span data-ttu-id="880d1-244">Como mostra o exemplo a seguir, esse comportamento é diferente da comparação ordinal.</span><span class="sxs-lookup"><span data-stu-id="880d1-244">As the following example shows, this behavior differs from ordinal comparison.</span></span>

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

<span data-ttu-id="880d1-245">Ao interpretar nomes de arquivo, cookies ou qualquer outro elemento em que uma combinação como "å" pode aparecer, as comparações ordinais ainda oferecem o comportamento mais transparente e adequado.</span><span class="sxs-lookup"><span data-stu-id="880d1-245">When interpreting file names, cookies, or anything else where a combination such as "å" can appear, ordinal comparisons still offer the most transparent and fitting behavior.</span></span>

<span data-ttu-id="880d1-246">De forma geral, a cultura invariável tem muito poucas propriedades que a tornam útil para comparação.</span><span class="sxs-lookup"><span data-stu-id="880d1-246">On balance, the invariant culture has very few properties that make it useful for comparison.</span></span> <span data-ttu-id="880d1-247">Ela faz a comparação de maneira linguisticamente relevante, o que impede que ela garanta a equivalência simbólica total, mas não é a opção de exibição em nenhuma cultura.</span><span class="sxs-lookup"><span data-stu-id="880d1-247">It does comparison in a linguistically relevant manner, which prevents it from guaranteeing full symbolic equivalence, but it is not the choice for display in any culture.</span></span> <span data-ttu-id="880d1-248">Por exemplo, se um arquivo de dados grande que contém uma lista de identificadores classificados para exibição acompanha um aplicativo, a adição a essa lista exige uma inserção com a inserção de estilo invariável.</span><span class="sxs-lookup"><span data-stu-id="880d1-248">For example, if a large data file that contains a list of sorted identifiers for display accompanies an application, adding to this list would require an insertion with invariant-style sorting.</span></span>

## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a><span data-ttu-id="880d1-249">Escolha de um membro StringComparison para a chamada de método</span><span class="sxs-lookup"><span data-stu-id="880d1-249">Choosing a StringComparison member for your method call</span></span>

<span data-ttu-id="880d1-250">A tabela a seguir descreve o mapeamento do contexto semântico da cadeia de caracteres para um membro de enumeração [StringComparison](xref:System.StringComparison).</span><span class="sxs-lookup"><span data-stu-id="880d1-250">The following table outlines the mapping from semantic string context to a [StringComparison](xref:System.StringComparison) enumeration member.</span></span>

<span data-ttu-id="880d1-251">Dados</span><span class="sxs-lookup"><span data-stu-id="880d1-251">Data</span></span> | <span data-ttu-id="880d1-252">Comportamento</span><span class="sxs-lookup"><span data-stu-id="880d1-252">Behavior</span></span> | <span data-ttu-id="880d1-253">Valor de System.StringComparison correspondente</span><span class="sxs-lookup"><span data-stu-id="880d1-253">Corresponding System.StringComparison value</span></span>
---- | -------- | -------------------------------------------
<span data-ttu-id="880d1-254">Identificadores internos que diferenciam maiúsculas de minúsculas, identificadores que diferenciam maiúsculas de minúsculas em padrões, como XML e HTTP ou configurações relacionadas à segurança que diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="880d1-254">Case-sensitive internal identifiers, case-sensitive identifiers in standards such as XML and HTTP, or case-sensitive security-related settings.</span></span> | <span data-ttu-id="880d1-255">Um identificador não linguístico, em que bytes correspondem exatamente.</span><span class="sxs-lookup"><span data-stu-id="880d1-255">A non-linguistic identifier, where bytes match exactly.</span></span> | [<span data-ttu-id="880d1-256">StringComparison.Ordinal</span><span class="sxs-lookup"><span data-stu-id="880d1-256">StringComparison.Ordinal</span></span>](xref:System.StringComparison.Ordinal)
<span data-ttu-id="880d1-257">Identificadores internos que não diferenciam maiúsculas de minúsculas, identificadores que não diferenciam maiúsculas de minúsculas em padrões, como XML e HTTP, caminhos de arquivo, valores e chave de Registro, variáveis do ambiente, identificadores de recurso (por exemplo nomes de identificador) ou configurações relacionadas à segurança que não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="880d1-257">Case-insensitive internal identifiers, case-insensitive identifiers in standards such as XML and HTTP, file paths, registry keys and values, environment variables, resource identifiers (for example, handle names), or case-insensitive security-related settings.</span></span> | <span data-ttu-id="880d1-258">Um identificador não linguístico, em que as maiúsculas e minúsculas são irrelevantes.</span><span class="sxs-lookup"><span data-stu-id="880d1-258">A non-linguistic identifier, where case is irrelevant.</span></span> | [<span data-ttu-id="880d1-259">StringComparison.OrdinalIgnoreCase</span><span class="sxs-lookup"><span data-stu-id="880d1-259">StringComparison.OrdinalIgnoreCase</span></span>](xref:System.StringComparison.OrdinalIgnoreCase)
<span data-ttu-id="880d1-260">Dados exibidos para o usuário ou para a maioria das entradas do usuário.</span><span class="sxs-lookup"><span data-stu-id="880d1-260">Data displayed to the user or most user input.</span></span> | <span data-ttu-id="880d1-261">Dados que exigem os costumes linguísticos locais.</span><span class="sxs-lookup"><span data-stu-id="880d1-261">Data that requires local linguistic customs.</span></span> | <span data-ttu-id="880d1-262">[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) ou [CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase)</span><span class="sxs-lookup"><span data-stu-id="880d1-262">[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) or [CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase)</span></span>

## <a name="common-string-comparison-methods"></a><span data-ttu-id="880d1-263">Métodos comuns de comparação da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="880d1-263">Common string comparison methods</span></span>

<span data-ttu-id="880d1-264">As seções a seguir descrevem os métodos que são mais comumente usados para a comparação de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="880d1-264">The following sections describe the methods that are most commonly used for string comparison.</span></span>

### <a name="stringcompare"></a><span data-ttu-id="880d1-265">String.Compare</span><span class="sxs-lookup"><span data-stu-id="880d1-265">String.Compare</span></span>

<span data-ttu-id="880d1-266">Interpretação padrão: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span><span class="sxs-lookup"><span data-stu-id="880d1-266">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="880d1-267">Como a operação mais central da interpretação de cadeia de caracteres, todas as instâncias de chamadas desse método devem ser examinadas para determinar se as cadeias de caracteres devem ser interpretadas de acordo com a cultura atual ou dissociadas da cultura (simbolicamente).</span><span class="sxs-lookup"><span data-stu-id="880d1-267">As the operation most central to string interpretation, all instances of these method calls should be examined to determine whether strings should be interpreted according to the current culture, or dissociated from the culture (symbolically).</span></span> <span data-ttu-id="880d1-268">Normalmente, é o último e uma comparação de [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="880d1-268">Typically, it is the latter, and a [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) comparison should be used instead.</span></span>

<span data-ttu-id="880d1-269">A classe [System.Globalization.CompareInfo](xref:System.Globalization.CompareInfo), que é retornada pela propriedade [CultureInfo.CompareInfo](xref:System.Globalization.CultureInfo.CompareInfo), também inclui um método [Compare](xref:System.Globalization.CompareInfo.Compare(System.String,System.Int32,System.String,System.Int32,System.Globalization.CompareOptions)) que fornece um grande número de opções de correspondência (ordinal, ignorando os espaços em branco, ignorando o tipo kana e assim por diante) por meio da enumeração de sinalizador [CompareOptions](xref:System.Globalization.CompareOptions).</span><span class="sxs-lookup"><span data-stu-id="880d1-269">The [System.Globalization.CompareInfo](xref:System.Globalization.CompareInfo) class, which is returned by the [CultureInfo.CompareInfo](xref:System.Globalization.CultureInfo.CompareInfo) property, also includes a [Compare](xref:System.Globalization.CompareInfo.Compare(System.String,System.Int32,System.String,System.Int32,System.Globalization.CompareOptions)) method that provides a large number of matching options (ordinal, ignoring white space, ignoring kana type, and so on) by means of the [CompareOptions](xref:System.Globalization.CompareOptions) flag enumeration.</span></span> 

### <a name="stringcompareto"></a><span data-ttu-id="880d1-270">String.CompareTo</span><span class="sxs-lookup"><span data-stu-id="880d1-270">String.CompareTo</span></span>

<span data-ttu-id="880d1-271">Interpretação padrão: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span><span class="sxs-lookup"><span data-stu-id="880d1-271">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="880d1-272">Esse método no momento não oferece uma sobrecarga que especifica um tipo [StringComparison](xref:System.StringComparison).</span><span class="sxs-lookup"><span data-stu-id="880d1-272">This method does not currently offer an overload that specifies a [StringComparison](xref:System.StringComparison) type.</span></span> <span data-ttu-id="880d1-273">Normalmente é possível converter esse método para o formato [String.Compare(String, String, StringComparison)](xref:System.String.Compare(System.String,System.String,System.StringComparison)) recomendado.</span><span class="sxs-lookup"><span data-stu-id="880d1-273">It is usually possible to convert this method to the recommended [String.Compare(String, String, StringComparison)](xref:System.String.Compare(System.String,System.String,System.StringComparison)) form.</span></span>

<span data-ttu-id="880d1-274">Os tipos que implementam as interfaces [IComparable](xref:System.IComparable) e [IComparable&lt;T&gt;](xref:System.IComparable%601) implementam esse método.</span><span class="sxs-lookup"><span data-stu-id="880d1-274">Types that implement the [IComparable](xref:System.IComparable) and [IComparable&lt;T&gt;](xref:System.IComparable%601) interfaces implement this method.</span></span> <span data-ttu-id="880d1-275">Como ele não oferece a opção de um parâmetro [StringComparison](xref:System.StringComparison), os tipos de implementação geralmente permitem que o usuário especifique um [StringComparer](xref:System.StringComparer) em seu construtor.</span><span class="sxs-lookup"><span data-stu-id="880d1-275">Because it does not offer the option of a [StringComparison](xref:System.StringComparison) parameter, implementing types often let the user specify a [StringComparer](xref:System.StringComparer) in their constructor.</span></span> <span data-ttu-id="880d1-276">O exemplo a seguir define uma classe `FileName` cujo construtor de classe inclui um parâmetro [StringComparer](xref:System.StringComparer).</span><span class="sxs-lookup"><span data-stu-id="880d1-276">The following example defines a `FileName` class whose class constructor includes a [StringComparer](xref:System.StringComparer) parameter.</span></span> <span data-ttu-id="880d1-277">Esse objeto [StringComparer](xref:System.StringComparer) é então usado no método `FileName.CompareTo`.</span><span class="sxs-lookup"><span data-stu-id="880d1-277">This [StringComparer](xref:System.StringComparer) object is then used in the `FileName.CompareTo` method.</span></span>

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

### <a name="stringequals"></a><span data-ttu-id="880d1-278">String.Equals</span><span class="sxs-lookup"><span data-stu-id="880d1-278">String.Equals</span></span>

<span data-ttu-id="880d1-279">Interpretação padrão: [StringComparison.Ordinal](xref:System.StringComparison.Ordinal).</span><span class="sxs-lookup"><span data-stu-id="880d1-279">Default interpretation: [StringComparison.Ordinal](xref:System.StringComparison.Ordinal).</span></span>

<span data-ttu-id="880d1-280">A classe [String](xref:System.String) permite que você teste a igualdade chamando as sobrecargas do método `Equals` ou estáticas ou usando o operador de igualdade estático.</span><span class="sxs-lookup"><span data-stu-id="880d1-280">The [String](xref:System.String) class lets you test for equality by calling either the static or instance `Equals` method overloads, or by using the static equality operator.</span></span> <span data-ttu-id="880d1-281">O operador e as sobrecargas utilizam a comparação ordinal por padrão.</span><span class="sxs-lookup"><span data-stu-id="880d1-281">The overloads and operator use ordinal comparison by default.</span></span> <span data-ttu-id="880d1-282">No entanto, ainda é recomendável que você chame uma sobrecarga que especifique explicitamente o tipo [StringComparison](xref:System.StringComparison) mesmo se você desejar executar uma comparação ordinal. Isso facilita a pesquisa de código para uma determinada interpretação da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="880d1-282">However, we still recommend that you call an overload that explicitly specifies the [StringComparison](xref:System.StringComparison) type even if you want to perform an ordinal comparison; this makes it easier to search code for a certain string interpretation.</span></span> 

### <a name="stringtoupper-and-stringtolower"></a><span data-ttu-id="880d1-283">String.ToUpper e String.ToLower</span><span class="sxs-lookup"><span data-stu-id="880d1-283">String.ToUpper and String.ToLower</span></span>

<span data-ttu-id="880d1-284">Interpretação padrão: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span><span class="sxs-lookup"><span data-stu-id="880d1-284">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="880d1-285">Você deve ter cuidado ao usar esses métodos, pois forçar uma cadeia de caracteres para maiúsculas ou minúsculas normalmente é usado como uma normalização pequena para comparar cadeias de caracteres independentemente de maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="880d1-285">You should be careful when you use these methods, because forcing a string to a uppercase or lowercase is often used as a small normalization for comparing strings regardless of case.</span></span> <span data-ttu-id="880d1-286">Nesse caso, considere o uso de uma comparação que não diferencie maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="880d1-286">If so, consider using a case-insensitive comparison.</span></span> 

<span data-ttu-id="880d1-287">Os métodos [String.ToUpperInvariant](xref:System.String.ToUpperInvariant) e [String.ToLowerInvariant](xref:System.String.ToLowerInvariant) também estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="880d1-287">The [String.ToUpperInvariant](xref:System.String.ToUpperInvariant) and [String.ToLowerInvariant](xref:System.String.ToLowerInvariant) methods are also available.</span></span> <span data-ttu-id="880d1-288">[ToUpperInvariant](xref:System.String.ToUpperInvariant) é o modo padrão de normalizar as maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="880d1-288">[ToUpperInvariant](xref:System.String.ToUpperInvariant) is the standard way to normalize case.</span></span> <span data-ttu-id="880d1-289">Comparações feitas usando [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) são comportamentalmente a composição de duas chamadas: chamar [ToUpperInvariant](xref:System.String.ToUpperInvariant) nos dois argumentos da cadeia de caracteres e fazer uma comparação usando [StringComparison.Ordinal](xref:System.StringComparison.Ordinal).</span><span class="sxs-lookup"><span data-stu-id="880d1-289">Comparisons made using [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) are behaviorally the composition of two calls: calling [ToUpperInvariant](xref:System.String.ToUpperInvariant) on both string arguments, and doing a comparison using [StringComparison.Ordinal](xref:System.StringComparison.Ordinal).</span></span>

<span data-ttu-id="880d1-290">Também há sobrecargas disponíveis para converter para maiúsculas e minúsculas em uma cultura específica, passando um objeto [CultureInfo](xref:System.Globalization.CultureInfo) que representa aquela cultura para o método.</span><span class="sxs-lookup"><span data-stu-id="880d1-290">Overloads are also available for converting to uppercase and lowercase in a specific culture, by passing a [CultureInfo](xref:System.Globalization.CultureInfo) object that represents that culture to the method.</span></span>

### <a name="chartoupper-and-chartolower"></a><span data-ttu-id="880d1-291">Char.ToUpper e Char.ToLower</span><span class="sxs-lookup"><span data-stu-id="880d1-291">Char.ToUpper and Char.ToLower</span></span>

<span data-ttu-id="880d1-292">Interpretação padrão: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span><span class="sxs-lookup"><span data-stu-id="880d1-292">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="880d1-293">Esses métodos funcionam de forma semelhante aos métodos [String.ToUpper](xref:System.String.ToUpper) e [String.ToLower](xref:System.String.ToLower) descritos na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="880d1-293">These methods work similarly to the [String.ToUpper](xref:System.String.ToUpper) and [String.ToLower](xref:System.String.ToLower) methods described in the previous section.</span></span>

### <a name="stringstartswith-and-stringendswith"></a><span data-ttu-id="880d1-294">String.StartsWith e String.EndsWith</span><span class="sxs-lookup"><span data-stu-id="880d1-294">String.StartsWith and String.EndsWith</span></span>

<span data-ttu-id="880d1-295">Interpretação padrão: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span><span class="sxs-lookup"><span data-stu-id="880d1-295">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="880d1-296">Por padrão, esses dois métodos executam uma comparação que leva em conta a cultura.</span><span class="sxs-lookup"><span data-stu-id="880d1-296">By default, both of these methods perform a culture-sensitive comparison.</span></span>

### <a name="stringindexof-and-stringlastindexof"></a><span data-ttu-id="880d1-297">String.IndexOf e String.LastIndexOf</span><span class="sxs-lookup"><span data-stu-id="880d1-297">String.IndexOf and String.LastIndexOf</span></span>

<span data-ttu-id="880d1-298">Interpretação padrão: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span><span class="sxs-lookup"><span data-stu-id="880d1-298">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="880d1-299">Há uma falta de consistência em como as sobrecargas padrão desses métodos realizam comparações.</span><span class="sxs-lookup"><span data-stu-id="880d1-299">There is a lack of consistency in how the default overloads of these methods perform comparisons.</span></span> <span data-ttu-id="880d1-300">Todos os métodos [String](xref:System.String) `IndexOf` e [String](xref:System.String) `LastIndexOf` que incluem um parâmetro [Char](xref:System.Char) realizam uma comparação ordinal, mas os métodos [String](xref:System.String) `IndexOf` e [String`](xref:System.String) `LastIndexOf\` padrão que incluem um parâmetro [String](xref:System.String) realizam uma comparação que leva em conta a cultura.</span><span class="sxs-lookup"><span data-stu-id="880d1-300">All [String](xref:System.String) `IndexOf` and [String](xref:System.String) `LastIndexOf` methods that include a [Char](xref:System.Char) parameter perform an ordinal comparison, but the default [String](xref:System.String) `IndexOf` and [String`](xref:System.String) `LastIndexOf\` methods that include a [String](xref:System.String) parameter perform a culture-sensitive comparison.</span></span> 

<span data-ttu-id="880d1-301">Se você chamar o método ` `IndexOf` or `LastIndexOf\` e passar a ele uma cadeia de caracteres para localizar na instância atual, é recomendável que você chame uma sobrecarga que especifique explicitamente o tipo [StringComparison](xref:System.StringComparison).</span><span class="sxs-lookup"><span data-stu-id="880d1-301">If you call ` `IndexOf` or `LastIndexOf\` method and pass it a string to locate in the current instance, we recommend that you call an overload that explicitly specifies the [StringComparison](xref:System.StringComparison) type.</span></span> <span data-ttu-id="880d1-302">As sobrecargas que incluem um argumento [Char](xref:System.Char) não permitem que você especifique um tipo [StringComparison](xref:System.StringComparison).</span><span class="sxs-lookup"><span data-stu-id="880d1-302">The overloads that include a [Char](xref:System.Char) argument do not allow you to specify a [StringComparison](xref:System.StringComparison) type.</span></span>

## <a name="methods-that-perform-string-comparison-indirectly"></a><span data-ttu-id="880d1-303">Métodos que realizam comparação indireta de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="880d1-303">Methods that perform string comparison indirectly</span></span>

<span data-ttu-id="880d1-304">Alguns métodos que não de cadeias de caracteres que têm a comparação de cadeia de caracteres como uma operação central usam o tipo [StringComparer](xref:System.StringComparer).</span><span class="sxs-lookup"><span data-stu-id="880d1-304">Some non-string methods that have string comparison as a central operation use the [StringComparer](xref:System.StringComparer) type.</span></span> <span data-ttu-id="880d1-305">A classe [StringComparer](xref:System.StringComparer) inclui quatro propriedades estáticas que retornam instâncias [StringComparer](xref:System.StringComparer) cujos métodos `Compare` realizam os seguintes tipos de comparações de cadeias de caracteres:</span><span class="sxs-lookup"><span data-stu-id="880d1-305">The [StringComparer](xref:System.StringComparer) class includes four static properties that return [StringComparer](xref:System.StringComparer) instances whose `Compare` methods perform the following types of string comparisons:</span></span>

* <span data-ttu-id="880d1-306">Comparações de cadeias de caracteres que levam em conta a cultura usando a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="880d1-306">Culture-sensitive string comparisons using the current culture.</span></span> <span data-ttu-id="880d1-307">Esse objeto [StringComparer](xref:System.StringComparer) é retornado pela propriedade [StringComparer.CurrentCulture](xref:System.StringComparer.CurrentCulture).</span><span class="sxs-lookup"><span data-stu-id="880d1-307">This [StringComparer](xref:System.StringComparer) object is returned by the [StringComparer.CurrentCulture](xref:System.StringComparer.CurrentCulture) property.</span></span>

* <span data-ttu-id="880d1-308">Comparações que não diferenciam maiúsculas de minúsculas usando a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="880d1-308">Case-insensitive comparisons using the current culture.</span></span> <span data-ttu-id="880d1-309">Esse objeto [StringComparer](xref:System.StringComparer) é retornado pela propriedade [StringComparer.CurrentCultureIgnoreCase](xref:System.StringComparer.CurrentCultureIgnoreCase).</span><span class="sxs-lookup"><span data-stu-id="880d1-309">This [StringComparer](xref:System.StringComparer) object is returned by the [StringComparer.CurrentCultureIgnoreCase](xref:System.StringComparer.CurrentCultureIgnoreCase) property.</span></span>

* <span data-ttu-id="880d1-310">Comparação ordinal.</span><span class="sxs-lookup"><span data-stu-id="880d1-310">Ordinal comparison.</span></span> <span data-ttu-id="880d1-311">Esse objeto [StringComparer](xref:System.StringComparer) é retornado pela propriedade [StringComparer.Ordinal](xref:System.StringComparer.Ordinal).</span><span class="sxs-lookup"><span data-stu-id="880d1-311">This [StringComparer](xref:System.StringComparer) object is returned by the [StringComparer.Ordinal](xref:System.StringComparer.Ordinal) property.</span></span> 

* <span data-ttu-id="880d1-312">Comparação ordinal que não diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="880d1-312">Case-insensitive ordinal comparison.</span></span> <span data-ttu-id="880d1-313">Esse objeto [StringComparer](xref:System.StringComparer) é retornado pela propriedade [StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase).</span><span class="sxs-lookup"><span data-stu-id="880d1-313">This [StringComparer](xref:System.StringComparer) object is returned by the [StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase) property.</span></span>

### <a name="arraysort-and-arraybinarysearch"></a><span data-ttu-id="880d1-314">Array.Sort e Array.BinarySearch</span><span class="sxs-lookup"><span data-stu-id="880d1-314">Array.Sort and Array.BinarySearch</span></span>

<span data-ttu-id="880d1-315">Interpretação padrão: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span><span class="sxs-lookup"><span data-stu-id="880d1-315">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="880d1-316">Ao armazenar quaisquer dados em uma coleção ou ler dados persistentes de um arquivo ou banco de dados em uma coleção, alternar a cultura atual pode invalidar as invariáveis na coleção.</span><span class="sxs-lookup"><span data-stu-id="880d1-316">When you store any data in a collection, or read persisted data from a file or database into a collection, switching the current culture can invalidate the invariants in the collection.</span></span> <span data-ttu-id="880d1-317">O método [Array.BinarySearch](xref:System.Array.BinarySearch(System.Array,System.Object)) assume que os elementos na matriz a serem pesquisados já estão classificados.</span><span class="sxs-lookup"><span data-stu-id="880d1-317">The [Array.BinarySearch](xref:System.Array.BinarySearch(System.Array,System.Object)) method assumes that the elements in the array to be searched are already sorted.</span></span> <span data-ttu-id="880d1-318">Para classificar qualquer elemento de cadeia de caracteres na matriz, o método [Array.Sort](xref:System.Array.Sort(System.Array)) chama o método [String] `Compare` para ordenar os elementos individuais.</span><span class="sxs-lookup"><span data-stu-id="880d1-318">To sort any string element in the array, the [Array.Sort](xref:System.Array.Sort(System.Array)) method calls the [String] `Compare` method to order individual elements.</span></span> <span data-ttu-id="880d1-319">Usar um comparador que leva em conta a cultura pode ser perigoso se a cultura mudar entre o momento em que a matriz é ordenada e que seu conteúdo é pesquisado.</span><span class="sxs-lookup"><span data-stu-id="880d1-319">Using a culture-sensitive comparer can be dangerous if the culture changes between the time that the array is sorted and its contents are searched.</span></span> <span data-ttu-id="880d1-320">Por exemplo, no código a seguir, o armazenamento e a recuperação operam no comparador que é fornecido implicitamente pela propriedade `Thread.CurrentThread.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="880d1-320">For example, in the following code, storage and retrieval operate on the comparer that is provided implicitly by the `Thread.CurrentThread.CurrentCulture` property.</span></span> <span data-ttu-id="880d1-321">Se a cultura puder mudar entre as chamadas para `StoreNames` e `DoesNameExist`, e especialmente se os conteúdos da matriz forem mantidos em algum lugar entre as duas chamadas de método, a pesquisa binária poderá falhar.</span><span class="sxs-lookup"><span data-stu-id="880d1-321">If the culture can change between the calls to `StoreNames` and `DoesNameExist`, and especially if the array contents are persisted somewhere between the two method calls, the binary search may fail.</span></span> 

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

<span data-ttu-id="880d1-322">Uma variação recomendada é exibida no exemplo a seguir, que usa o mesmo método de comparação (que não leva em conta a cultura) ordinal para classificar e pesquisar a matriz.</span><span class="sxs-lookup"><span data-stu-id="880d1-322">A recommended variation appears in the following example, which uses the same ordinal (culture-insensitive) comparison method both to sort and to search the array.</span></span> <span data-ttu-id="880d1-323">O código de alteração é refletido nas linhas rotuladas como `Line A` e `Line B` nos dois exemplos.</span><span class="sxs-lookup"><span data-stu-id="880d1-323">The change code is reflected in the lines labeled `Line A` and `Line B` in the two examples.</span></span>

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

<span data-ttu-id="880d1-324">Se esses dados forem mantidos e movidos entre as culturas e a classificação for usada para apresentar esses dados para o usuário, você pode considerar usar `StringComparison.InvariantCulture`, que opera linguisticamente para a melhor saída do usuário, mas não é afetado pelas alterações na cultura.</span><span class="sxs-lookup"><span data-stu-id="880d1-324">If this data is persisted and moved across cultures, and sorting is used to present this data to the user, you might consider using `StringComparison.InvariantCulture`, which operates linguistically for better user output but is unaffected by changes in culture.</span></span> <span data-ttu-id="880d1-325">O exemplo a seguir modifica os dois exemplos anteriores para usar a cultura invariável para classificar e pesquisar a matriz.</span><span class="sxs-lookup"><span data-stu-id="880d1-325">The following example modifies the two previous examples to use the invariant culture for sorting and searching the array.</span></span>

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

### <a name="collections-example-hashtable-constructor"></a><span data-ttu-id="880d1-326">Exemplo de Coleções: Construtor da Tabela de Hash</span><span class="sxs-lookup"><span data-stu-id="880d1-326">Collections Example: Hashtable Constructor</span></span>

<span data-ttu-id="880d1-327">As cadeias de caracteres de hash fornecem um segundo exemplo de uma operação que é afetada pela maneira como as cadeias de caracteres são comparadas.</span><span class="sxs-lookup"><span data-stu-id="880d1-327">Hashing strings provides a second example of an operation that is affected by the way in which strings are compared.</span></span> 

<span data-ttu-id="880d1-328">O exemplo a seguir instancia um objeto [Hashtable](xref:System.Collections.Hashtable) passando para ele o objeto [StringComparer](xref:System.StringComparer) que é retornado pela propriedade [StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase).</span><span class="sxs-lookup"><span data-stu-id="880d1-328">The following example instantiates a [Hashtable](xref:System.Collections.Hashtable) object by passing it the [StringComparer](xref:System.StringComparer) object that is returned by the [StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase) property.</span></span> <span data-ttu-id="880d1-329">Como uma classe [StringComparer](xref:System.StringComparer) que é derivada de [StringComparer](xref:System.StringComparer) implementa a interface [IEqualityComparer](xref:System.Collections.IEqualityComparer), seu método [GetHashCode](xref:System.Collections.IEqualityComparer) é usado para calcular o código hash das cadeias de caracteres na tabela de hash.</span><span class="sxs-lookup"><span data-stu-id="880d1-329">Because a class [StringComparer](xref:System.StringComparer) that is derived from [StringComparer](xref:System.StringComparer) implements the [IEqualityComparer](xref:System.Collections.IEqualityComparer) interface, its [GetHashCode](xref:System.Collections.IEqualityComparer) method is used to compute the hash code of strings in the hash table.</span></span>

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

## <a name="displaying-and-persisting-formatted-data"></a><span data-ttu-id="880d1-330">Exibição e persistência de dados formatados</span><span class="sxs-lookup"><span data-stu-id="880d1-330">Displaying and persisting formatted data</span></span>

<span data-ttu-id="880d1-331">Quando você exibir dados que não são de cadeias de caracteres como números e datas e horas para os usuários, formate-os usando as configurações culturais do usuário.</span><span class="sxs-lookup"><span data-stu-id="880d1-331">When you display non-string data such as numbers and dates and times to users, format them by using the user's cultural settings.</span></span> <span data-ttu-id="880d1-332">Por padrão, o método [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) e os métodos `ToString` dos tipos numéricos e dos tipos de data e hora usam a cultura do thread atual para as operações de formatação.</span><span class="sxs-lookup"><span data-stu-id="880d1-332">By default, the [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) method and the `ToString` methods of the numeric types and the date and time types use the current thread culture for formatting operations.</span></span> <span data-ttu-id="880d1-333">Para especificar explicitamente que o método de formatação deve usar a cultura atual, você pode chamar uma sobrecarga de um método de formatação que tenha um parâmetro de provedor, como [String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) ou [DateTime.ToString(IFormatProvider)](xref:System.DateTime.ToString(System.IFormatProvider)) e passar para ela a propriedade [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture).</span><span class="sxs-lookup"><span data-stu-id="880d1-333">To explicitly specify that the formatting method should use the current culture, you can call an overload of a formatting method that has a provider parameter, such as [String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) or [DateTime.ToString(IFormatProvider)](xref:System.DateTime.ToString(System.IFormatProvider)), and pass it the [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture) property.</span></span> 

<span data-ttu-id="880d1-334">Você pode manter os dados que não são de cadeias de caracteres como dados binários ou como dados formatados.</span><span class="sxs-lookup"><span data-stu-id="880d1-334">You can persist non-string data either as binary data or as formatted data.</span></span> <span data-ttu-id="880d1-335">Se optar por salvá-los como dados formatados, você deve chamar uma sobrecarga de método de formatação que inclua um parâmetro *provider* e passar para ele a propriedade [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture).</span><span class="sxs-lookup"><span data-stu-id="880d1-335">If you choose to save it as formatted data, you should call a formatting method overload that includes a *provider* parameter and pass it the [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) property.</span></span> <span data-ttu-id="880d1-336">A cultura invariável fornece um formato consistente para os dados formatados que é independente da cultura e do computador.</span><span class="sxs-lookup"><span data-stu-id="880d1-336">The invariant culture provides a consistent format for formatted data that is independent of culture and machine.</span></span> <span data-ttu-id="880d1-337">Em contraste, dados persistentes que são formatados usando culturas diferentes da cultura invariável têm várias limitações:</span><span class="sxs-lookup"><span data-stu-id="880d1-337">In contrast, persisting data that is formatted by using cultures other than the invariant culture has a number of limitations:</span></span> 

* <span data-ttu-id="880d1-338">É provável que os dados não sejam utilizáveis se forem recuperados em um sistema que tem uma cultura diferente ou se o usuário do sistema atual alterar a cultura atual e tentar recuperar os dados.</span><span class="sxs-lookup"><span data-stu-id="880d1-338">The data is likely to be unusable if it is retrieved on a system that has a different culture, or if the user of the current system changes the current culture and tries to retrieve the data.</span></span> 

* <span data-ttu-id="880d1-339">As propriedades de uma cultura em um computador específico podem ser diferentes dos valores padrão.</span><span class="sxs-lookup"><span data-stu-id="880d1-339">The properties of a culture on a specific computer can differ from standard values.</span></span> <span data-ttu-id="880d1-340">A qualquer momento, um usuário pode personalizar as configurações de exibição que levam em conta a cultura.</span><span class="sxs-lookup"><span data-stu-id="880d1-340">At any time, a user can customize culture-sensitive display settings.</span></span> <span data-ttu-id="880d1-341">Devido a isso, os dados formatados que são salvos em um sistema podem não ser legíveis após o usuário personalizar as configurações culturais.</span><span class="sxs-lookup"><span data-stu-id="880d1-341">Because of this, formatted data that is saved on a system may not be readable after the user customizes cultural settings.</span></span> <span data-ttu-id="880d1-342">É provável que a portabilidade dos dados formatados entre computadores seja ainda mais limitada.</span><span class="sxs-lookup"><span data-stu-id="880d1-342">The portability of formatted data across computers is likely to be even more limited.</span></span> 

* <span data-ttu-id="880d1-343">Os padrões internacionais, regionais ou nacionais que controlam a formatação de números ou datas e horas são alterados ao longo do tempo e essas alterações são incorporadas nas atualizações do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="880d1-343">International, regional, or national standards that govern the formatting of numbers or dates and times change over time, and these changes are incorporated into operating system updates.</span></span> <span data-ttu-id="880d1-344">Quando as convenções de formatação mudam, os dados que foram formatados usando as convenções anteriores podem se tornar ilegíveis.</span><span class="sxs-lookup"><span data-stu-id="880d1-344">When formatting conventions change, data that was formatted by using the previous conventions may become unreadable.</span></span> 

<span data-ttu-id="880d1-345">O exemplo a seguir ilustra a portabilidade limitada resultante do uso da formatação que leva em conta a cultura para manter os dados.</span><span class="sxs-lookup"><span data-stu-id="880d1-345">The following example illustrates the limited portability that results from using culture-sensitive formatting to persist data.</span></span> <span data-ttu-id="880d1-346">O exemplo salva uma matriz de valores de data e hora em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="880d1-346">The example saves an array of date and time values to a file.</span></span> <span data-ttu-id="880d1-347">Eles são formatados usando as convenções da cultura do inglês (Estados Unidos).</span><span class="sxs-lookup"><span data-stu-id="880d1-347">These are formatted by using the conventions of the English (United States) culture.</span></span> <span data-ttu-id="880d1-348">Depois que o aplicativo altera a cultura do thread atual para francês (Suíça), ele tenta ler os valores salvos usando as convenções de formatação da cultura atual.</span><span class="sxs-lookup"><span data-stu-id="880d1-348">After the application changes the current thread culture to French (Switzerland), it tries to read the saved values by using the formatting conventions of the current culture.</span></span> <span data-ttu-id="880d1-349">A tentativa de ler dois dos itens de dados gera uma exceção [FormatException](xref:System.FormatException) e a matriz de datas agora contém dois elementos incorretos que são iguais a [MinValue](xref:System.DateTime.MinValue).</span><span class="sxs-lookup"><span data-stu-id="880d1-349">The attempt to read two of the data items throws a [FormatException](xref:System.FormatException) exception, and the array of dates now contains two incorrect elements that are equal to [MinValue](xref:System.DateTime.MinValue).</span></span> 

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

<span data-ttu-id="880d1-350">No entanto, se você substituir a propriedade [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture) por [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) nas chamadas para [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) e [DateTime.Parse(String, IFormatProvider)](xref:System.DateTime.Parse(System.String,System.IFormatProvider)), os dados de data e hora mantidos serão restaurados com êxito, como a saída a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="880d1-350">However, if you replace the [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture) property with [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) in the calls to [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) and [DateTime.Parse(String, IFormatProvider)](xref:System.DateTime.Parse(System.String,System.IFormatProvider)), the persisted date and time data is successfully restored, as the following output shows.</span></span>

```
// 06.05.1758 21:26
// 05.05.1818 07:19
// 22.04.1870 23:54
// 08.09.1890 06:47
// 18.02.1905 15:12
```

## <a name="see-also"></a><span data-ttu-id="880d1-351">Consulte também</span><span class="sxs-lookup"><span data-stu-id="880d1-351">See also</span></span>

[<span data-ttu-id="880d1-352">Manipulação de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="880d1-352">Manipulating strings</span></span>](manipulating-strings.md)

