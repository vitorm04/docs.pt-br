---
title: "Construtores de referência inversa em expressões regulares"
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
- backreferences
- constructs, backreference
- .NET Framework regular expressions, backreference constructs
- regular expressions, backreference constructs
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a884e70f542c2ed7ff63e39cb7eadedf0ef7b4d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="backreference-constructs-in-regular-expressions"></a><span data-ttu-id="b8774-102">Construtores de referência inversa em expressões regulares</span><span class="sxs-lookup"><span data-stu-id="b8774-102">Backreference Constructs in Regular Expressions</span></span>
<span data-ttu-id="b8774-103">As referências inversas fornecem uma maneira conveniente de identificar um caractere ou subcadeia de caracteres repetida em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b8774-103">Backreferences provide a convenient way to identify a repeated character or substring within a string.</span></span> <span data-ttu-id="b8774-104">Por exemplo, se a cadeia de caracteres de entrada contiver várias ocorrências de uma subcadeia de caracteres arbitrária, você poderá corresponder a primeira ocorrência a um grupo de captura e, em seguida, usar uma referência inversa para corresponder às ocorrências subsequentes da subcadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b8774-104">For example, if the input string contains multiple occurrences of an arbitrary substring, you can match the first occurrence with a capturing group, and then use a backreference to match subsequent occurrences of the substring.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8774-105">Uma sintaxe separada é usada para se referir a grupos de captura nomeados e numerados em cadeias de caracteres de substituição.</span><span class="sxs-lookup"><span data-stu-id="b8774-105">A separate syntax is used to refer to named and numbered capturing groups in replacement strings.</span></span> <span data-ttu-id="b8774-106">Para obter mais informações, consulte [substituições](substitutions-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b8774-106">For more information, see [Substitutions](substitutions-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="b8774-107">O .NET define elementos de linguagem separados para se referir a grupos de captura nomeados e numerados.</span><span class="sxs-lookup"><span data-stu-id="b8774-107">.NET defines separate language elements to refer to numbered and named capturing groups.</span></span> <span data-ttu-id="b8774-108">Para obter mais informações sobre grupos de captura, consulte [construções de agrupamento](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b8774-108">For more information about capturing groups, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span></span>  
  
## <a name="numbered-backreferences"></a><span data-ttu-id="b8774-109">Referências inversas numeradas</span><span class="sxs-lookup"><span data-stu-id="b8774-109">Numbered Backreferences</span></span>  
 <span data-ttu-id="b8774-110">Uma referência inversa numerada usa a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="b8774-110">A numbered backreference uses the following syntax:</span></span>  
  
 <span data-ttu-id="b8774-111">`\`*número*</span><span class="sxs-lookup"><span data-stu-id="b8774-111">`\` *number*</span></span>  
  
 <span data-ttu-id="b8774-112">em que *number* é a posição ordinal do grupo de captura na expressão regular.</span><span class="sxs-lookup"><span data-stu-id="b8774-112">where *number* is the ordinal position of the capturing group in the regular expression.</span></span> <span data-ttu-id="b8774-113">Por exemplo, `\4` corresponde ao conteúdo do quarto grupo de captura.</span><span class="sxs-lookup"><span data-stu-id="b8774-113">For example, `\4` matches the contents of the fourth capturing group.</span></span> <span data-ttu-id="b8774-114">Se *número* não é definido no padrão de expressão regular, um erro de análise ocorre e o mecanismo de expressão regular gera um <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="b8774-114">If *number* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="b8774-115">Por exemplo, a expressão regular `\b(\w+)\s\1` é válida porque `(\w+)` é o primeiro e único grupo de captura na expressão.</span><span class="sxs-lookup"><span data-stu-id="b8774-115">For example, the regular expression `\b(\w+)\s\1` is valid, because `(\w+)` is the first and only capturing group in the expression.</span></span> <span data-ttu-id="b8774-116">Por outro lado, `\b(\w+)\s\2` é inválida e gera uma exceção de argumento porque não há nenhum grupo de captura com o número `\2`.</span><span class="sxs-lookup"><span data-stu-id="b8774-116">On the other hand, `\b(\w+)\s\2` is invalid and throws an argument exception, because there is no capturing group numbered `\2`.</span></span>  
  
 <span data-ttu-id="b8774-117">Observe a ambiguidade entre códigos de escape octal (como `\16`) e `\` *número* referências inversas que usam a mesma notação.</span><span class="sxs-lookup"><span data-stu-id="b8774-117">Note the ambiguity between octal escape codes (such as `\16`) and `\`*number* backreferences that use the same notation.</span></span> <span data-ttu-id="b8774-118">Essa ambiguidade é resolvida da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b8774-118">This ambiguity is resolved as follows:</span></span>  
  
-   <span data-ttu-id="b8774-119">As expressões `\1` a `\9` sempre são interpretadas como referências inversas e não como códigos octais.</span><span class="sxs-lookup"><span data-stu-id="b8774-119">The expressions `\1` through `\9` are always interpreted as backreferences, and not as octal codes.</span></span>  
  
-   <span data-ttu-id="b8774-120">Se o primeiro dígito de uma expressão de diversos for 8 ou 9 (como `\80` ou `\91`), a expressão será interpretada como uma literal.</span><span class="sxs-lookup"><span data-stu-id="b8774-120">If the first digit of a multidigit expression is 8 or 9 (such as `\80` or `\91`), the expression as interpreted as a literal.</span></span>  
  
-   <span data-ttu-id="b8774-121">Expressões de `\10` e maiores serão consideradas referências inversas se houver uma referência inversa correspondente àquele número, caso contrário, elas serão interpretadas como códigos octais.</span><span class="sxs-lookup"><span data-stu-id="b8774-121">Expressions from `\10` and greater are considered backreferences if there is a backreference corresponding to that number; otherwise, they are interpreted as octal codes.</span></span>  
  
-   <span data-ttu-id="b8774-122">Se uma expressão regular contém uma referência anterior para um número de grupo indefinido, ocorre um erro de análise e o mecanismo de expressão regular gera um <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="b8774-122">If a regular expression contains a backreference to an undefined group number, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="b8774-123">Se a ambiguidade for um problema, você pode usar o `\k<` *nome* `>` notação, que é ambíguo e não pode ser confundido com códigos de caracteres octal.</span><span class="sxs-lookup"><span data-stu-id="b8774-123">If the ambiguity is a problem, you can use the `\k<`*name*`>` notation, which is unambiguous and cannot be confused with octal character codes.</span></span> <span data-ttu-id="b8774-124">Da mesma forma, os códigos hexadecimais como `\xdd` são não ambíguos e não podem ser confundidos com referências inversas.</span><span class="sxs-lookup"><span data-stu-id="b8774-124">Similarly, hexadecimal codes such as `\xdd` are unambiguous and cannot be confused with backreferences.</span></span>  
  
 <span data-ttu-id="b8774-125">O exemplo a seguir localiza caracteres de palavra duplicados em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b8774-125">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="b8774-126">Ele define uma expressão regular, `(\w)\1`, que consiste nos elementos a seguir.</span><span class="sxs-lookup"><span data-stu-id="b8774-126">It defines a regular expression, `(\w)\1`, which consists of the following elements.</span></span>  
  
|<span data-ttu-id="b8774-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="b8774-127">Element</span></span>|<span data-ttu-id="b8774-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8774-128">Description</span></span>|  
|-------------|-----------------|  
|`(\w)`|<span data-ttu-id="b8774-129">Corresponde a um caractere de palavra e o atribui ao primeiro grupo de captura.</span><span class="sxs-lookup"><span data-stu-id="b8774-129">Match a word character and assign it to the first capturing group.</span></span>|  
|`\1`|<span data-ttu-id="b8774-130">Corresponde ao próximo caractere que é o mesmo que o valor do primeiro grupo de captura.</span><span class="sxs-lookup"><span data-stu-id="b8774-130">Match the next character that is the same as the value of the first capturing group.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
 [!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]  
  
## <a name="named-backreferences"></a><span data-ttu-id="b8774-131">Referências inversas nomeadas</span><span class="sxs-lookup"><span data-stu-id="b8774-131">Named Backreferences</span></span>  
 <span data-ttu-id="b8774-132">Uma referência inversa nomeada é definida usando a sintaxe a seguir:</span><span class="sxs-lookup"><span data-stu-id="b8774-132">A named backreference is defined by using the following syntax:</span></span>  
  
 <span data-ttu-id="b8774-133">`\k<`*nome*`>`</span><span class="sxs-lookup"><span data-stu-id="b8774-133">`\k<` *name* `>`</span></span>  
  
 <span data-ttu-id="b8774-134">ou:</span><span class="sxs-lookup"><span data-stu-id="b8774-134">or:</span></span>  
  
 <span data-ttu-id="b8774-135">`\k'`*nome*`'`</span><span class="sxs-lookup"><span data-stu-id="b8774-135">`\k'` *name* `'`</span></span>  
  
 <span data-ttu-id="b8774-136">em que *name* é o nome de um grupo de captura definido no padrão da expressão regular.</span><span class="sxs-lookup"><span data-stu-id="b8774-136">where *name* is the name of a capturing group defined in the regular expression pattern.</span></span> <span data-ttu-id="b8774-137">Se *nome* não é definido no padrão de expressão regular, um erro de análise ocorre e o mecanismo de expressão regular gera um <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="b8774-137">If *name* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="b8774-138">O exemplo a seguir localiza caracteres de palavra duplicados em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b8774-138">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="b8774-139">Ele define uma expressão regular, `(?<char>\w)\k<char>`, que consiste nos elementos a seguir.</span><span class="sxs-lookup"><span data-stu-id="b8774-139">It defines a regular expression, `(?<char>\w)\k<char>`, which consists of the following elements.</span></span>  
  
|<span data-ttu-id="b8774-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="b8774-140">Element</span></span>|<span data-ttu-id="b8774-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8774-141">Description</span></span>|  
|-------------|-----------------|  
|`(?<char>\w)`|<span data-ttu-id="b8774-142">Corresponder um caractere de palavra e atribuí-la a um grupo de captura nomeado `char`.</span><span class="sxs-lookup"><span data-stu-id="b8774-142">Match a word character and assign it to a capturing group named `char`.</span></span>|  
|`\k<char>`|<span data-ttu-id="b8774-143">Corresponde o próximo caractere é o mesmo que o valor da `char` grupo de captura.</span><span class="sxs-lookup"><span data-stu-id="b8774-143">Match the next character that is the same as the value of the `char` capturing group.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
 [!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]  
  
 <span data-ttu-id="b8774-144">Observe que *name* também pode ser a representação da cadeia de caracteres de um número.</span><span class="sxs-lookup"><span data-stu-id="b8774-144">Note that *name* can also be the string representation of a number.</span></span> <span data-ttu-id="b8774-145">Por exemplo, o exemplo a seguir usa a expressão regular `(?<2>\w)\k<2>` para localizar caracteres de palavra duplicados em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b8774-145">For example, the following example uses the regular expression `(?<2>\w)\k<2>` to find doubled word characters in a string.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
 [!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]  
  
## <a name="what-backreferences-match"></a><span data-ttu-id="b8774-146">A que as referências inversas correspondem</span><span class="sxs-lookup"><span data-stu-id="b8774-146">What Backreferences Match</span></span>  
 <span data-ttu-id="b8774-147">Uma referência inversa refere-se à definição mais recente de um grupo (a definição mais imediatamente à esquerda, ao fazer a correspondência da esquerda para a direita).</span><span class="sxs-lookup"><span data-stu-id="b8774-147">A backreference refers to the most recent definition of a group (the definition most immediately to the left, when matching left to right).</span></span> <span data-ttu-id="b8774-148">Quando um grupo faz várias capturas, uma referência inversa refere-se à captura mais recente.</span><span class="sxs-lookup"><span data-stu-id="b8774-148">When a group makes multiple captures, a backreference refers to the most recent capture.</span></span>  
  
 <span data-ttu-id="b8774-149">O exemplo a seguir inclui um padrão de expressão regular, `(?<1>a)(?<1>\1b)*`, que redefine o grupo nomeado \1.</span><span class="sxs-lookup"><span data-stu-id="b8774-149">The following example includes a regular expression pattern, `(?<1>a)(?<1>\1b)*`, which redefines the \1 named group.</span></span> <span data-ttu-id="b8774-150">A tabela a seguir descreve cada padrão na expressão regular.</span><span class="sxs-lookup"><span data-stu-id="b8774-150">The following table describes each pattern in the regular expression.</span></span>  
  
|<span data-ttu-id="b8774-151">Padrão</span><span class="sxs-lookup"><span data-stu-id="b8774-151">Pattern</span></span>|<span data-ttu-id="b8774-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8774-152">Description</span></span>|  
|-------------|-----------------|  
|`(?<1>a)`|<span data-ttu-id="b8774-153">Associar o caractere "a" e atribuir o resultado para o grupo de captura nomeado `1`.</span><span class="sxs-lookup"><span data-stu-id="b8774-153">Match the character "a" and assign the result to the capturing group named `1`.</span></span>|  
|`(?<1>\1b)*`|<span data-ttu-id="b8774-154">Ocorrência de correspondência 0 ou 1 do grupo denominado `1` juntamente com um "b" e atribui o resultado para o grupo de captura nomeado `1`.</span><span class="sxs-lookup"><span data-stu-id="b8774-154">Match 0 or 1 occurrence of the group named `1` along with a "b", and assign the result to the capturing group named `1`.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
 [!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]  
  
 <span data-ttu-id="b8774-155">Comparando a expressão regular com a cadeia de caracteres de entrada ("aababb"), o mecanismo de expressões regulares realiza as seguintes operações:</span><span class="sxs-lookup"><span data-stu-id="b8774-155">In comparing the regular expression with the input string ("aababb"), the regular expression engine performs the following operations:</span></span>  
  
1.  <span data-ttu-id="b8774-156">Ele começa no início da cadeia de caracteres e corresponde com êxito o “a” com a expressão `(?<1>a)`.</span><span class="sxs-lookup"><span data-stu-id="b8774-156">It starts at the beginning of the string, and successfully matches "a" with the expression `(?<1>a)`.</span></span> <span data-ttu-id="b8774-157">O valor de `1` grupo agora é "a".</span><span class="sxs-lookup"><span data-stu-id="b8774-157">The value of the `1` group is now "a".</span></span>  
  
2.  <span data-ttu-id="b8774-158">Ele avança para o segundo caractere e corresponde com êxito a cadeia de caracteres "ab" com a expressão `\1b`, ou "ab".</span><span class="sxs-lookup"><span data-stu-id="b8774-158">It advances to the second character, and successfully matches the string "ab" with the expression `\1b`, or "ab".</span></span> <span data-ttu-id="b8774-159">Em seguida, atribui o resultado, "ab", a `\1`.</span><span class="sxs-lookup"><span data-stu-id="b8774-159">It then assigns the result, "ab" to `\1`.</span></span>  
  
3.  <span data-ttu-id="b8774-160">Ele avança para o quarto caractere.</span><span class="sxs-lookup"><span data-stu-id="b8774-160">It advances to the fourth character.</span></span> <span data-ttu-id="b8774-161">A expressão `(?<1>\1b)` deve ser correspondida zero ou mais vezes, de forma que corresponda com êxito a cadeia de caracteres “abb” à expressão `\1b`.</span><span class="sxs-lookup"><span data-stu-id="b8774-161">The expression `(?<1>\1b)` is to be matched zero or more times, so it successfully matches the string "abb" with the expression `\1b`.</span></span> <span data-ttu-id="b8774-162">Ela atribui o resultado, “abb”, a `\1`.</span><span class="sxs-lookup"><span data-stu-id="b8774-162">It assigns the result, "abb", back to `\1`.</span></span>  
  
 <span data-ttu-id="b8774-163">Neste exemplo, `*` é um quantificador looping – ele é avaliado repetidamente até que o mecanismo de expressões regulares não corresponda ao padrão definido.</span><span class="sxs-lookup"><span data-stu-id="b8774-163">In this example, `*` is a looping quantifier -- it is evaluated repeatedly until the regular expression engine cannot match the pattern it defines.</span></span> <span data-ttu-id="b8774-164">Os quantificadores de looping não limpam definições de grupo.</span><span class="sxs-lookup"><span data-stu-id="b8774-164">Looping quantifiers do not clear group definitions.</span></span>  
  
 <span data-ttu-id="b8774-165">Se um grupo não capturou nenhuma subcadeia de caracteres, uma referência inversa a esse grupo é indefinida e nunca corresponde.</span><span class="sxs-lookup"><span data-stu-id="b8774-165">If a group has not captured any substrings, a backreference to that group is undefined and never matches.</span></span> <span data-ttu-id="b8774-166">Isso é ilustrado pelo padrão de expressão regular `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, que é definida da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b8774-166">This is illustrated by the regular expression pattern `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, which is defined as follows:</span></span>  
  
|<span data-ttu-id="b8774-167">Padrão</span><span class="sxs-lookup"><span data-stu-id="b8774-167">Pattern</span></span>|<span data-ttu-id="b8774-168">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8774-168">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="b8774-169">Começa a correspondência em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="b8774-169">Begin the match on a word boundary.</span></span>|  
|`(\p{Lu}{2})`|<span data-ttu-id="b8774-170">Corresponde a duas letras maiúsculas.</span><span class="sxs-lookup"><span data-stu-id="b8774-170">Match two uppercase letters.</span></span> <span data-ttu-id="b8774-171">Este é o primeiro grupo de captura.</span><span class="sxs-lookup"><span data-stu-id="b8774-171">This is the first capturing group.</span></span>|  
|`(\d{2})?`|<span data-ttu-id="b8774-172">Corresponde a zero ou uma ocorrência de dois dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="b8774-172">Match zero or one occurrence of two decimal digits.</span></span> <span data-ttu-id="b8774-173">Este é o segundo grupo de captura.</span><span class="sxs-lookup"><span data-stu-id="b8774-173">This is the second capturing group.</span></span>|  
|`(\p{Lu}{2})`|<span data-ttu-id="b8774-174">Corresponde a duas letras maiúsculas.</span><span class="sxs-lookup"><span data-stu-id="b8774-174">Match two uppercase letters.</span></span> <span data-ttu-id="b8774-175">Este é o terceiro grupo de captura.</span><span class="sxs-lookup"><span data-stu-id="b8774-175">This is the third capturing group.</span></span>|  
|`\b`|<span data-ttu-id="b8774-176">Termina a correspondência em um limite de palavra.</span><span class="sxs-lookup"><span data-stu-id="b8774-176">End the match on a word boundary.</span></span>|  
  
 <span data-ttu-id="b8774-177">Uma cadeia de caracteres de entrada pode corresponder a essa expressão regular, mesmo se os dois dígitos decimais que são definidos pelo segundo grupo de captura não estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="b8774-177">An input string can match this regular expression even if the two decimal digits that are defined by the second capturing group are not present.</span></span> <span data-ttu-id="b8774-178">O exemplo a seguir mostra que, embora a correspondência seja bem-sucedida, um grupo de captura vazio foi encontrado entre dois grupos de captura com êxito.</span><span class="sxs-lookup"><span data-stu-id="b8774-178">The following example shows that even though the match is successful, an empty capturing group is found between two successful capturing groups.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
 [!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b8774-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8774-179">See Also</span></span>  
 [<span data-ttu-id="b8774-180">Linguagem de expressão regular – referência rápida</span><span class="sxs-lookup"><span data-stu-id="b8774-180">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
