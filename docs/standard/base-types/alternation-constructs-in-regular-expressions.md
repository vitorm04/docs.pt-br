---
title: "Construtores de alternância em expressões regulares"
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
- either/or matching
- alternative matching patterns
- regular expressions, alternation constructs
- alternation constructs
- optional matching patterns
- constructs, alternation
- .NET Framework regular expressions, alternation constructs
ms.assetid: 071e22e9-fbb0-4ecf-add1-8d2424f9f2d1
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6ad632130b6f111ff863648b8b1a3b2835c27660
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="b6a65-102">Construtores de alternância em expressões regulares</span><span class="sxs-lookup"><span data-stu-id="b6a65-102">Alternation Constructs in Regular Expressions</span></span>
<span data-ttu-id="b6a65-103"><a name="top"></a>Construtores de alternância modificam uma expressão regular para habilitar o / ou ou correspondência condicional.</span><span class="sxs-lookup"><span data-stu-id="b6a65-103"><a name="top"></a> Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="b6a65-104">O .NET dá suporte a três constructos de alternância:</span><span class="sxs-lookup"><span data-stu-id="b6a65-104">.NET supports three alternation constructs:</span></span>  
  
-   [<span data-ttu-id="b6a65-105">Correspondência de padrões com &#124;</span><span class="sxs-lookup"><span data-stu-id="b6a65-105">Pattern matching with &#124;</span></span>](#Either_Or)  
  
-   [<span data-ttu-id="b6a65-106">Correspondendo condicional (? ( Sim de expressão) &#124; não)</span><span class="sxs-lookup"><span data-stu-id="b6a65-106">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)  
  
-   [<span data-ttu-id="b6a65-107">Correspondência condicional baseado em um grupo capturado válido</span><span class="sxs-lookup"><span data-stu-id="b6a65-107">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a><span data-ttu-id="b6a65-108">Correspondência de padrão com &#124;</span><span class="sxs-lookup"><span data-stu-id="b6a65-108">Pattern Matching with &#124;</span></span>  
 <span data-ttu-id="b6a65-109">Você pode usar a barra vertical (`|`) caracteres para corresponder a qualquer um de uma série de padrões, onde o `|` caractere que separa cada padrão.</span><span class="sxs-lookup"><span data-stu-id="b6a65-109">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>  
  
 <span data-ttu-id="b6a65-110">Como a classe de caractere positivo, o `|` caractere pode ser usado para corresponder a qualquer um de um número de caracteres único.</span><span class="sxs-lookup"><span data-stu-id="b6a65-110">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="b6a65-111">O exemplo a seguir usa uma classe de caractere positivo e um / ou correspondência de padrão com o `|` caractere para localizar as ocorrências das palavras "cinza" ou "cinza" em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b6a65-111">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="b6a65-112">Nesse caso, o `|` caractere produz uma expressão regular é mais detalhada.</span><span class="sxs-lookup"><span data-stu-id="b6a65-112">In this case, the `|` character produces a regular expression that is more verbose.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 <span data-ttu-id="b6a65-113">A expressão regular que usa o `|` caractere, `\bgr(a|e)y\b`, é interpretado conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6a65-113">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="b6a65-114">Padrão</span><span class="sxs-lookup"><span data-stu-id="b6a65-114">Pattern</span></span>|<span data-ttu-id="b6a65-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6a65-115">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="b6a65-116">Iniciar em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="b6a65-116">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="b6a65-117">Corresponder aos caracteres "gr".</span><span class="sxs-lookup"><span data-stu-id="b6a65-117">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="b6a65-118">Corresponder a um "a" ou "e".</span><span class="sxs-lookup"><span data-stu-id="b6a65-118">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="b6a65-119">Corresponder a um “y” em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="b6a65-119">Match a "y" on a word boundary.</span></span>|  
  
 <span data-ttu-id="b6a65-120">O `|` caractere também pode ser usado para realizar uma / ou corresponder a vários caracteres ou subexpressões, que podem incluir qualquer combinação de literais de caracteres e elementos de linguagem de expressão regular.</span><span class="sxs-lookup"><span data-stu-id="b6a65-120">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="b6a65-121">(A classe de caracteres não fornece essa funcionalidade.) O exemplo a seguir usa o `|` caractere para extrair a qualquer dos EUA Número de seguro social (SSN), que é um número de 9 dígitos com o formato *ddd*-*dd*-*dddd*, ou dos EUA Número de identificação de empregador (EIN), que é um número de 9 dígitos com o formato *dd*-*ddddddd*.</span><span class="sxs-lookup"><span data-stu-id="b6a65-121">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 <span data-ttu-id="b6a65-122">A expressão regular `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` é interpretada conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6a65-122">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="b6a65-123">Padrão</span><span class="sxs-lookup"><span data-stu-id="b6a65-123">Pattern</span></span>|<span data-ttu-id="b6a65-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6a65-124">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="b6a65-125">Iniciar em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="b6a65-125">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="b6a65-126">Corresponde a uma das seguintes opções: dois dígitos decimais seguidos por um hífen seguido por sete dígitos decimais ou três dígitos decimais, um hífen, dois dígitos decimais, outro hífen e quatro dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="b6a65-126">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="b6a65-127">Termina a correspondência em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="b6a65-127">End the match at a word boundary.</span></span>|  
  
 [<span data-ttu-id="b6a65-128">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="b6a65-128">Back to top</span></span>](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="b6a65-129">Correspondência condicional com uma expressão</span><span class="sxs-lookup"><span data-stu-id="b6a65-129">Conditional Matching with an Expression</span></span>  
 <span data-ttu-id="b6a65-130">Este elemento de linguagem tenta corresponder a um dos dois padrões dependendo de se ele pode corresponder a um padrão inicial.</span><span class="sxs-lookup"><span data-stu-id="b6a65-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="b6a65-131">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="b6a65-131">Its syntax is:</span></span>  
  
 <span data-ttu-id="b6a65-132">`(?(`*expressão* `)` *Sim* `|` *sem*`)`</span><span class="sxs-lookup"><span data-stu-id="b6a65-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="b6a65-133">onde *expressão* é o padrão inicial para fazer a correspondência, *Sim* é o padrão para correspondência se *expressão* é correspondido e *sem* é opcional padrão para correspondência se *expressão* não corresponde.</span><span class="sxs-lookup"><span data-stu-id="b6a65-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="b6a65-134">O mecanismo de expressões regulares trata a *expressão* como uma asserção de largura zero, isto é, o mecanismo de expressões regulares não avança no fluxo de entrada após avaliar a *expressão*.</span><span class="sxs-lookup"><span data-stu-id="b6a65-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="b6a65-135">Portanto, esse constructo é equivalente ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="b6a65-135">Therefore, this construct is equivalent to the following:</span></span>  
  
 <span data-ttu-id="b6a65-136">`(?(?=`*expressão* `)` *Sim* `|` *sem*`)`</span><span class="sxs-lookup"><span data-stu-id="b6a65-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="b6a65-137">onde `(?=` *expressão* `)` é uma construção de declaração de largura zero.</span><span class="sxs-lookup"><span data-stu-id="b6a65-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="b6a65-138">(Para obter mais informações, consulte [construções de agrupamento](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Porque o mecanismo de expressão regular interpreta *expressão* como uma âncora (uma declaração de largura zero), *expressão* deve ser uma declaração de largura zero (para obter mais informações, consulte [ Ancora](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) ou uma subexpressão que também está contida no *Sim*.</span><span class="sxs-lookup"><span data-stu-id="b6a65-138">(For more information, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="b6a65-139">Caso contrário, o padrão *sim* não pode ser correspondido.</span><span class="sxs-lookup"><span data-stu-id="b6a65-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6a65-140">Se *expressão*é um grupo de captura nomeado ou numerado, a construção de alternância é interpretada como um teste de captura; para obter mais informações, consulte a próxima seção, [condicional correspondência com base em um grupo de captura válido](#Conditional_Group).</span><span class="sxs-lookup"><span data-stu-id="b6a65-140">If *expression*is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="b6a65-141">Em outras palavras, o mecanismo de expressões regulares não tenta corresponder a subcadeia de caracteres capturada, mas em vez disso, testa a presença ou ausência do grupo.</span><span class="sxs-lookup"><span data-stu-id="b6a65-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
 <span data-ttu-id="b6a65-142">O exemplo a seguir é uma variação do exemplo que aparece no [tanto / ou correspondência de padrões com &#124;](#Either_Or) seção.</span><span class="sxs-lookup"><span data-stu-id="b6a65-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="b6a65-143">Ele usa a correspondência condicional para determinar se os três primeiros caracteres após um limite de palavra são dois dígitos seguidos por um hífen.</span><span class="sxs-lookup"><span data-stu-id="b6a65-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="b6a65-144">Se forem, ele tenta corresponder a um EIN (Número de Identificação de Empregador) dos EUA.</span><span class="sxs-lookup"><span data-stu-id="b6a65-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="b6a65-145">Se não, ele tenta corresponder a um SSN (cadastro de pessoas físicas).</span><span class="sxs-lookup"><span data-stu-id="b6a65-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 <span data-ttu-id="b6a65-146">O padrão da expressão regular `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` é interpretado conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6a65-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="b6a65-147">Padrão</span><span class="sxs-lookup"><span data-stu-id="b6a65-147">Pattern</span></span>|<span data-ttu-id="b6a65-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6a65-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="b6a65-149">Iniciar em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="b6a65-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="b6a65-150">Determinar se os próximos três caracteres são compostos por dois dígitos seguidos por um hífen.</span><span class="sxs-lookup"><span data-stu-id="b6a65-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="b6a65-151">Se o padrão anterior corresponder, corresponder a dois dígitos seguidos por um hífen seguido por sete dígitos.</span><span class="sxs-lookup"><span data-stu-id="b6a65-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="b6a65-152">Se o padrão anterior não corresponder, corresponder a três dígitos decimais, um hífen, dois dígitos decimais, outro hífen e quatro dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="b6a65-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="b6a65-153">Corresponder a um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="b6a65-153">Match a word boundary.</span></span>|  
  
 [<span data-ttu-id="b6a65-154">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="b6a65-154">Back to top</span></span>](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="b6a65-155">Correspondência condicional com base em um grupo capturado válido</span><span class="sxs-lookup"><span data-stu-id="b6a65-155">Conditional Matching Based on a Valid Captured Group</span></span>  
 <span data-ttu-id="b6a65-156">Este elemento de linguagem tenta corresponder a um dos dois padrões dependendo de se ele correspondeu a um grupo de captura especificado.</span><span class="sxs-lookup"><span data-stu-id="b6a65-156">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="b6a65-157">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="b6a65-157">Its syntax is:</span></span>  
  
 <span data-ttu-id="b6a65-158">`(?(`*nome* `)` *Sim* `|` *sem*`)`</span><span class="sxs-lookup"><span data-stu-id="b6a65-158">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="b6a65-159">ou</span><span class="sxs-lookup"><span data-stu-id="b6a65-159">or</span></span>  
  
 <span data-ttu-id="b6a65-160">`(?(`*número* `)` *Sim* `|` *sem*`)`</span><span class="sxs-lookup"><span data-stu-id="b6a65-160">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="b6a65-161">onde *nome* é o nome e *número* é o número de um grupo de captura, *Sim* é a expressão para correspondência se *nome* ou *número* tiver uma correspondência, e *sem* é a expressão opcional para correspondência se não existir.</span><span class="sxs-lookup"><span data-stu-id="b6a65-161">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>  
  
 <span data-ttu-id="b6a65-162">Se *name* não corresponder ao nome de um grupo de captura que é usado no padrão de expressão regular, o constructo de alternância será interpretado como teste de expressão, conforme explicado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="b6a65-162">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="b6a65-163">Normalmente, isso significa que *expressão* é avaliada como `false`.</span><span class="sxs-lookup"><span data-stu-id="b6a65-163">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="b6a65-164">Se *número* não corresponde a um grupo de captura numerado que é usado no padrão de expressão regular, a expressão regular mecanismo lança um <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="b6a65-164">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="b6a65-165">O exemplo a seguir é uma variação do exemplo que aparece no [tanto / ou correspondência de padrões com &#124;](#Either_Or) seção.</span><span class="sxs-lookup"><span data-stu-id="b6a65-165">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="b6a65-166">Ele usa um grupo de captura chamado `n2` que consiste em dois dígitos seguidos por um hífen.</span><span class="sxs-lookup"><span data-stu-id="b6a65-166">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="b6a65-167">O constructo de alternância testa se este grupo de captura foi correspondido na cadeia de caracteres de entrada.</span><span class="sxs-lookup"><span data-stu-id="b6a65-167">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="b6a65-168">Em caso afirmativo, o constructo de alternância tenta corresponder aos sete últimos dígitos de um EIN (Número de Identificação de Empregador) dos EUA.</span><span class="sxs-lookup"><span data-stu-id="b6a65-168">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="b6a65-169">Se não tiver, ele tenta corresponder a um SSN (cadastro de pessoas físicas).</span><span class="sxs-lookup"><span data-stu-id="b6a65-169">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 <span data-ttu-id="b6a65-170">O padrão da expressão regular `\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` é interpretado conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6a65-170">The regular expression pattern `\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="b6a65-171">Padrão</span><span class="sxs-lookup"><span data-stu-id="b6a65-171">Pattern</span></span>|<span data-ttu-id="b6a65-172">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6a65-172">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="b6a65-173">Iniciar em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="b6a65-173">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)*`|<span data-ttu-id="b6a65-174">Corresponder a zero ou uma ocorrência de dois dígitos seguidos por um hífen.</span><span class="sxs-lookup"><span data-stu-id="b6a65-174">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="b6a65-175">Atribua um nome ao grupo de captura `n2`.</span><span class="sxs-lookup"><span data-stu-id="b6a65-175">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="b6a65-176">Testar se `n2` foi correspondido na cadeia de caracteres de entrada.</span><span class="sxs-lookup"><span data-stu-id="b6a65-176">Test whether `n2` was matched in the input string.</span></span>|  
|`)\d{7}`|<span data-ttu-id="b6a65-177">Se `n2` tiver sido correspondido, corresponder a sete dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="b6a65-177">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="b6a65-178">Se `n2` não tiver sido correspondido, corresponder a três dígitos decimais, um hífen, dois dígitos decimais, outro hífen e quatro dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="b6a65-178">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="b6a65-179">Corresponder a um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="b6a65-179">Match a word boundary.</span></span>|  
  
 <span data-ttu-id="b6a65-180">Uma variação desse exemplo que usa um grupo numerado em vez de um grupo nomeado é mostrada no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6a65-180">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="b6a65-181">O padrão da expressão regular é `\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="b6a65-181">Its regular expression pattern is `\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b6a65-182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6a65-182">See Also</span></span>  
 [<span data-ttu-id="b6a65-183">Linguagem de expressão regular – referência rápida</span><span class="sxs-lookup"><span data-stu-id="b6a65-183">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
