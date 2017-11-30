---
title: "Exemplo de expressão regular: Verificação de HREFs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2bc9db7317c7a73f70a2cb83322b8b3a4c3771b9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="regular-expression-example-scanning-for-hrefs"></a><span data-ttu-id="5279f-102">Exemplo de expressão regular: Verificação de HREFs</span><span class="sxs-lookup"><span data-stu-id="5279f-102">Regular Expression Example: Scanning for HREFs</span></span>
<span data-ttu-id="5279f-103">O exemplo a seguir procura uma cadeia de caracteres de entrada e exibe todos os valores href="…" e suas localizações na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5279f-103">The following example searches an input string and displays all the href="…" values and their locations in the string.</span></span>  
  
## <a name="the-regex-object"></a><span data-ttu-id="5279f-104">O objeto Regex</span><span class="sxs-lookup"><span data-stu-id="5279f-104">The Regex Object</span></span>  
 <span data-ttu-id="5279f-105">Porque o `DumpHRefs` método pode ser chamado várias vezes do código do usuário, ele usa o `static` (`Shared` no Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="5279f-105">Because the `DumpHRefs` method can be called multiple times from user code, it uses the `static` (`Shared` in Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5279f-106">Isso permite que o mecanismo de expressão regular para armazenar em cache a expressão regular e evita a sobrecarga da instanciação de um novo <xref:System.Text.RegularExpressions.Regex> objeto cada vez que o método é chamado.</span><span class="sxs-lookup"><span data-stu-id="5279f-106">This enables the regular expression engine to cache the regular expression and avoids the overhead of instantiating a new <xref:System.Text.RegularExpressions.Regex> object each time the method is called.</span></span> <span data-ttu-id="5279f-107">Um <xref:System.Text.RegularExpressions.Match> objeto é usado para iterar por todas as correspondências na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5279f-107">A <xref:System.Text.RegularExpressions.Match> object is then used to iterate through all matches in the string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 <span data-ttu-id="5279f-108">O exemplo a seguir mostra uma chamada para o método `DumpHRefs`.</span><span class="sxs-lookup"><span data-stu-id="5279f-108">The following example then illustrates a call to the `DumpHRefs` method.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 <span data-ttu-id="5279f-109">O padrão da expressão regular `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` é interpretado conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="5279f-109">The regular expression pattern `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="5279f-110">Padrão</span><span class="sxs-lookup"><span data-stu-id="5279f-110">Pattern</span></span>|<span data-ttu-id="5279f-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="5279f-111">Description</span></span>|  
|-------------|-----------------|  
|`href`|<span data-ttu-id="5279f-112">Corresponder à cadeia de caracteres literal “href”.</span><span class="sxs-lookup"><span data-stu-id="5279f-112">Match the literal string "href".</span></span> <span data-ttu-id="5279f-113">A correspondência não diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="5279f-113">The match is case-insensitive.</span></span>|  
|`\s*`|<span data-ttu-id="5279f-114">Corresponder a zero ou mais caracteres de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="5279f-114">Match zero or more white-space characters.</span></span>|  
|`=`|<span data-ttu-id="5279f-115">Coincide com o sinal de igual.</span><span class="sxs-lookup"><span data-stu-id="5279f-115">Match the equals sign.</span></span>|  
|`\s*`|<span data-ttu-id="5279f-116">Corresponder a zero ou mais caracteres de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="5279f-116">Match zero or more white-space characters.</span></span>|  
|`(?:["'](?<1>[^"']*)"&#124;(?<1>\S+))`|<span data-ttu-id="5279f-117">Corresponde a um dos seguintes sem atribuir o resultado a um grupo capturado:</span><span class="sxs-lookup"><span data-stu-id="5279f-117">Match one of the following without assigning the result to a captured group:</span></span><br /><br /> <span data-ttu-id="5279f-118">-Um sinal de aspas ou apóstrofo, seguido por zero ou mais ocorrências de qualquer caractere que não seja um sinal de aspas ou apóstrofo, seguido por um sinal de aspas ou apóstrofo.</span><span class="sxs-lookup"><span data-stu-id="5279f-118">-   A quotation mark or apostrophe, followed by zero or more occurrences of any character other than a quotation mark or apostrophe, followed by a quotation mark or apostrophe.</span></span> <span data-ttu-id="5279f-119">O grupo chamado `1` está incluído nesse padrão.</span><span class="sxs-lookup"><span data-stu-id="5279f-119">The group named `1` is included in this pattern.</span></span><br /><span data-ttu-id="5279f-120">-Um ou mais caracteres de espaço não em branco.</span><span class="sxs-lookup"><span data-stu-id="5279f-120">-   One or more non-white-space characters.</span></span> <span data-ttu-id="5279f-121">O grupo chamado `1` está incluído nesse padrão.</span><span class="sxs-lookup"><span data-stu-id="5279f-121">The group named `1` is included in this pattern.</span></span>|  
|`(?<1>[^"']*)`|<span data-ttu-id="5279f-122">Atribuir zero ou mais ocorrências de qualquer caractere diferente de aspas simples ou apóstrofe ao grupo de captura chamado `1`.</span><span class="sxs-lookup"><span data-stu-id="5279f-122">Assign zero or more occurrences of any character other than a quotation mark or apostrophe to the capturing group named `1`.</span></span>|  
|`"(?<1>\S+)`|<span data-ttu-id="5279f-123">Atribuir um ou mais caracteres diferentes de espaço em branco ao grupo de captura chamado `1`.</span><span class="sxs-lookup"><span data-stu-id="5279f-123">Assign one or more non-white-space characters to the capturing group named `1`.</span></span>|  
  
## <a name="match-result-class"></a><span data-ttu-id="5279f-124">Classe de resultado de correspondência</span><span class="sxs-lookup"><span data-stu-id="5279f-124">Match Result Class</span></span>  
 <span data-ttu-id="5279f-125">Os resultados de uma pesquisa são armazenados no <xref:System.Text.RegularExpressions.Match> classe, que fornece acesso a todas as subcadeias de caracteres extraídas pela pesquisa.</span><span class="sxs-lookup"><span data-stu-id="5279f-125">The results of a search are stored in the <xref:System.Text.RegularExpressions.Match> class, which provides access to all the substrings extracted by the search.</span></span> <span data-ttu-id="5279f-126">Ela também lembra a cadeia de caracteres que está sendo pesquisada e a expressão regular que está sendo usada, para que ele pode chamar o <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> método para executar outra pesquisa iniciando onde a última terminou.</span><span class="sxs-lookup"><span data-stu-id="5279f-126">It also remembers the string being searched and the regular expression being used, so it can call the <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> method to perform another search starting where the last one ended.</span></span>  
  
## <a name="explicitly-named-captures"></a><span data-ttu-id="5279f-127">Capturas nomeadas explicitamente</span><span class="sxs-lookup"><span data-stu-id="5279f-127">Explicitly Named Captures</span></span>  
 <span data-ttu-id="5279f-128">Em expressões regulares tradicionais, os parênteses de captura são numerados sequencialmente de forma automática.</span><span class="sxs-lookup"><span data-stu-id="5279f-128">In traditional regular expressions, capturing parentheses are automatically numbered sequentially.</span></span> <span data-ttu-id="5279f-129">Isso causa dois problemas.</span><span class="sxs-lookup"><span data-stu-id="5279f-129">This leads to two problems.</span></span> <span data-ttu-id="5279f-130">Primeiro, se uma expressão regular for modificada pela inserção ou remoção de um conjunto de parênteses, todo o código que se refere às captura numeradas deverá ser reescrito para refletir a nova numeração.</span><span class="sxs-lookup"><span data-stu-id="5279f-130">First, if a regular expression is modified by inserting or removing a set of parentheses, all code that refers to the numbered captures must be rewritten to reflect the new numbering.</span></span> <span data-ttu-id="5279f-131">Em segundo lugar, como diferentes conjuntos de parênteses geralmente são usados para fornecer duas expressões alternativas para uma correspondência aceitável, pode ser difícil determinar qual das duas expressões realmente retornou um resultado.</span><span class="sxs-lookup"><span data-stu-id="5279f-131">Second, because different sets of parentheses often are used to provide two alternative expressions for an acceptable match, it might be difficult to determine which of the two expressions actually returned a result.</span></span>  
  
 <span data-ttu-id="5279f-132">Para resolver esses problemas, o <xref:System.Text.RegularExpressions.Regex> classe oferece suporte à sintaxe `(?<name>…)` para capturar uma correspondência em um slot especificado (o slot pode ser nomeado usando uma cadeia de caracteres ou um inteiro; inteiros podem ser recuperados mais rapidamente).</span><span class="sxs-lookup"><span data-stu-id="5279f-132">To address these problems, the <xref:System.Text.RegularExpressions.Regex> class supports the syntax `(?<name>…)` for capturing a match into a specified slot (the slot can be named using a string or an integer; integers can be recalled more quickly).</span></span> <span data-ttu-id="5279f-133">Assim, todas as correspondências alternativas para a mesma cadeia de caracteres podem ser direcionadas para o mesmo local.</span><span class="sxs-lookup"><span data-stu-id="5279f-133">Thus, alternative matches for the same string all can be directed to the same place.</span></span> <span data-ttu-id="5279f-134">Em caso de conflito, a última correspondência solta em um slot é a correspondência com êxito.</span><span class="sxs-lookup"><span data-stu-id="5279f-134">In case of a conflict, the last match dropped into a slot is the successful match.</span></span> <span data-ttu-id="5279f-135">(No entanto, está disponível uma lista completa de diversas correspondências para um único slot.</span><span class="sxs-lookup"><span data-stu-id="5279f-135">(However, a complete list of multiple matches for a single slot is available.</span></span> <span data-ttu-id="5279f-136">Consulte o <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> coleção para obter detalhes.)</span><span class="sxs-lookup"><span data-stu-id="5279f-136">See the <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> collection for details.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5279f-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5279f-137">See Also</span></span>  
 [<span data-ttu-id="5279f-138">Expressões regulares do .NET</span><span class="sxs-lookup"><span data-stu-id="5279f-138">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
