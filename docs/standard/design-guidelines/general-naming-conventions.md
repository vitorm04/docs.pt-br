---
title: "Convenções de nomenclatura gerais"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dde3adbb7640978829dea4b977ed14eec38a9077
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="general-naming-conventions"></a><span data-ttu-id="c0964-102">Convenções de nomenclatura gerais</span><span class="sxs-lookup"><span data-stu-id="c0964-102">General Naming Conventions</span></span>
<span data-ttu-id="c0964-103">Esta seção descreve gerais convenções de nomenclatura relacionadas à escolha de palavra, diretrizes sobre o uso de abreviações e acrônimos e recomendações sobre como evitar o uso de nomes específicos do idioma.</span><span class="sxs-lookup"><span data-stu-id="c0964-103">This section describes general naming conventions that relate to word choice, guidelines on using abbreviations and acronyms, and recommendations on how to avoid using language-specific names.</span></span>  
  
## <a name="word-choice"></a><span data-ttu-id="c0964-104">Opções do Word</span><span class="sxs-lookup"><span data-stu-id="c0964-104">Word Choice</span></span>  
 <span data-ttu-id="c0964-105">**FAZER ✓** Escolha nomes de identificador facilmente legível.</span><span class="sxs-lookup"><span data-stu-id="c0964-105">**✓ DO** choose easily readable identifier names.</span></span>  
  
 <span data-ttu-id="c0964-106">Por exemplo, uma propriedade chamada `HorizontalAlignment` é mais legível para o inglês do que `AlignmentHorizontal`.</span><span class="sxs-lookup"><span data-stu-id="c0964-106">For example, a property named `HorizontalAlignment` is more English-readable than `AlignmentHorizontal`.</span></span>  
  
 <span data-ttu-id="c0964-107">**FAZER ✓** favorecer legibilidade por questão de brevidade.</span><span class="sxs-lookup"><span data-stu-id="c0964-107">**✓ DO** favor readability over brevity.</span></span>  
  
 <span data-ttu-id="c0964-108">O nome da propriedade `CanScrollHorizontally` é melhor do que `ScrollableX` (uma referência para o eixo x obscura).</span><span class="sxs-lookup"><span data-stu-id="c0964-108">The property name `CanScrollHorizontally` is better than `ScrollableX` (an obscure reference to the X-axis).</span></span>  
  
 <span data-ttu-id="c0964-109">**X não** usar outros caracteres não alfanuméricos, hífens ou sublinhados.</span><span class="sxs-lookup"><span data-stu-id="c0964-109">**X DO NOT** use underscores, hyphens, or any other nonalphanumeric characters.</span></span>  
  
 <span data-ttu-id="c0964-110">**X não** usar notação húngara.</span><span class="sxs-lookup"><span data-stu-id="c0964-110">**X DO NOT** use Hungarian notation.</span></span>  
  
 <span data-ttu-id="c0964-111">**X Evite** usando identificadores que entrem em conflito com palavras-chave de amplamente usados linguagens de programação.</span><span class="sxs-lookup"><span data-stu-id="c0964-111">**X AVOID** using identifiers that conflict with keywords of widely used programming languages.</span></span>  
  
 <span data-ttu-id="c0964-112">De acordo com a regra 4 do Common Language Specification (CLS), todos os idiomas compatíveis devem fornecer um mecanismo que permite o acesso a itens nomeados que usar uma palavra-chave de idioma como um identificador.</span><span class="sxs-lookup"><span data-stu-id="c0964-112">According to Rule 4 of the Common Language Specification (CLS), all compliant languages must provide a mechanism that allows access to named items that use a keyword of that language as an identifier.</span></span> <span data-ttu-id="c0964-113">C#, por exemplo, usa o @ logon como um mecanismo de escape nesse caso.</span><span class="sxs-lookup"><span data-stu-id="c0964-113">C#, for example, uses the @ sign as an escape mechanism in this case.</span></span> <span data-ttu-id="c0964-114">No entanto, ainda é uma boa ideia para evitar palavras-chave comuns porque ele é muito mais difícil de usar um método com a sequência de escape que sem ele.</span><span class="sxs-lookup"><span data-stu-id="c0964-114">However, it is still a good idea to avoid common keywords because it is much more difficult to use a method with the escape sequence than one without it.</span></span>  
  
## <a name="using-abbreviations-and-acronyms"></a><span data-ttu-id="c0964-115">Usando siglas e abreviações</span><span class="sxs-lookup"><span data-stu-id="c0964-115">Using Abbreviations and Acronyms</span></span>  
 <span data-ttu-id="c0964-116">**X não** usar abreviações ou contrações como parte dos nomes de identificador.</span><span class="sxs-lookup"><span data-stu-id="c0964-116">**X DO NOT** use abbreviations or contractions as part of identifier names.</span></span>  
  
 <span data-ttu-id="c0964-117">Por exemplo, use `GetWindow` em vez de `GetWin`.</span><span class="sxs-lookup"><span data-stu-id="c0964-117">For example, use `GetWindow` rather than `GetWin`.</span></span>  
  
 <span data-ttu-id="c0964-118">**X não** usar os acrônimos que não são amplamente aceitas e até mesmo se elas forem, somente quando necessário.</span><span class="sxs-lookup"><span data-stu-id="c0964-118">**X DO NOT** use any acronyms that are not widely accepted, and even if they are, only when necessary.</span></span>  
  
## <a name="avoiding-language-specific-names"></a><span data-ttu-id="c0964-119">Evitando nomes específicos do idioma</span><span class="sxs-lookup"><span data-stu-id="c0964-119">Avoiding Language-Specific Names</span></span>  
 <span data-ttu-id="c0964-120">**FAZER ✓** usar nomes semanticamente interessantes em vez de palavras-chave para nomes de tipo.</span><span class="sxs-lookup"><span data-stu-id="c0964-120">**✓ DO** use semantically interesting names rather than language-specific keywords for type names.</span></span>  
  
 <span data-ttu-id="c0964-121">Por exemplo, `GetLength` é um nome de melhor `GetInt`.</span><span class="sxs-lookup"><span data-stu-id="c0964-121">For example, `GetLength` is a better name than `GetInt`.</span></span>  
  
 <span data-ttu-id="c0964-122">**FAZER ✓** usar um nome de tipo genérico do CLR, em vez de um nome de idioma específico, em casos raros, quando um identificador não tem nenhum significado semântico, além de seu tipo.</span><span class="sxs-lookup"><span data-stu-id="c0964-122">**✓ DO** use a generic CLR type name, rather than a language-specific name, in the rare cases when an identifier has no semantic meaning beyond its type.</span></span>  
  
 <span data-ttu-id="c0964-123">Por exemplo, um método de conversão em <xref:System.Int64> devem ser nomeados `ToInt64`, não `ToLong` (porque <xref:System.Int64> é um nome CLR para c#-alias específico `long`).</span><span class="sxs-lookup"><span data-stu-id="c0964-123">For example, a method converting to <xref:System.Int64> should be named `ToInt64`, not `ToLong` (because <xref:System.Int64> is a CLR name for the C#-specific alias `long`).</span></span> <span data-ttu-id="c0964-124">A tabela a seguir apresenta vários tipos de dados base usando os nomes de tipo CLR (bem como os nomes de tipo correspondente do c#, Visual Basic e C++).</span><span class="sxs-lookup"><span data-stu-id="c0964-124">The following table presents several base data types using the CLR type names (as well as the corresponding type names for C#, Visual Basic, and C++).</span></span>  
  
|<span data-ttu-id="c0964-125">C#</span><span class="sxs-lookup"><span data-stu-id="c0964-125">C#</span></span>|<span data-ttu-id="c0964-126">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c0964-126">Visual Basic</span></span>|<span data-ttu-id="c0964-127">C++</span><span class="sxs-lookup"><span data-stu-id="c0964-127">C++</span></span>|<span data-ttu-id="c0964-128">CLR</span><span class="sxs-lookup"><span data-stu-id="c0964-128">CLR</span></span>|  
|---------|------------------|-----------|---------|  
|<span data-ttu-id="c0964-129">**sbyte**</span><span class="sxs-lookup"><span data-stu-id="c0964-129">**sbyte**</span></span>|<span data-ttu-id="c0964-130">**SByte**</span><span class="sxs-lookup"><span data-stu-id="c0964-130">**SByte**</span></span>|<span data-ttu-id="c0964-131">**char**</span><span class="sxs-lookup"><span data-stu-id="c0964-131">**char**</span></span>|<span data-ttu-id="c0964-132">**SByte**</span><span class="sxs-lookup"><span data-stu-id="c0964-132">**SByte**</span></span>|  
|<span data-ttu-id="c0964-133">**byte**</span><span class="sxs-lookup"><span data-stu-id="c0964-133">**byte**</span></span>|<span data-ttu-id="c0964-134">**Byte**</span><span class="sxs-lookup"><span data-stu-id="c0964-134">**Byte**</span></span>|<span data-ttu-id="c0964-135">**unsigned char**</span><span class="sxs-lookup"><span data-stu-id="c0964-135">**unsigned char**</span></span>|<span data-ttu-id="c0964-136">**Byte**</span><span class="sxs-lookup"><span data-stu-id="c0964-136">**Byte**</span></span>|  
|<span data-ttu-id="c0964-137">**short**</span><span class="sxs-lookup"><span data-stu-id="c0964-137">**short**</span></span>|<span data-ttu-id="c0964-138">**Short**</span><span class="sxs-lookup"><span data-stu-id="c0964-138">**Short**</span></span>|<span data-ttu-id="c0964-139">**short**</span><span class="sxs-lookup"><span data-stu-id="c0964-139">**short**</span></span>|<span data-ttu-id="c0964-140">**Int16**</span><span class="sxs-lookup"><span data-stu-id="c0964-140">**Int16**</span></span>|  
|<span data-ttu-id="c0964-141">**ushort**</span><span class="sxs-lookup"><span data-stu-id="c0964-141">**ushort**</span></span>|<span data-ttu-id="c0964-142">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="c0964-142">**UInt16**</span></span>|<span data-ttu-id="c0964-143">**unsigned short**</span><span class="sxs-lookup"><span data-stu-id="c0964-143">**unsigned short**</span></span>|<span data-ttu-id="c0964-144">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="c0964-144">**UInt16**</span></span>|  
|<span data-ttu-id="c0964-145">**int**</span><span class="sxs-lookup"><span data-stu-id="c0964-145">**int**</span></span>|<span data-ttu-id="c0964-146">**Integer**</span><span class="sxs-lookup"><span data-stu-id="c0964-146">**Integer**</span></span>|<span data-ttu-id="c0964-147">**int**</span><span class="sxs-lookup"><span data-stu-id="c0964-147">**int**</span></span>|<span data-ttu-id="c0964-148">**Int32**</span><span class="sxs-lookup"><span data-stu-id="c0964-148">**Int32**</span></span>|  
|<span data-ttu-id="c0964-149">**uint**</span><span class="sxs-lookup"><span data-stu-id="c0964-149">**uint**</span></span>|<span data-ttu-id="c0964-150">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="c0964-150">**UInt32**</span></span>|<span data-ttu-id="c0964-151">**unsigned int**</span><span class="sxs-lookup"><span data-stu-id="c0964-151">**unsigned int**</span></span>|<span data-ttu-id="c0964-152">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="c0964-152">**UInt32**</span></span>|  
|<span data-ttu-id="c0964-153">**long**</span><span class="sxs-lookup"><span data-stu-id="c0964-153">**long**</span></span>|<span data-ttu-id="c0964-154">**Long**</span><span class="sxs-lookup"><span data-stu-id="c0964-154">**Long**</span></span>|<span data-ttu-id="c0964-155">**__int64**</span><span class="sxs-lookup"><span data-stu-id="c0964-155">**__int64**</span></span>|<span data-ttu-id="c0964-156">**Int64**</span><span class="sxs-lookup"><span data-stu-id="c0964-156">**Int64**</span></span>|  
|<span data-ttu-id="c0964-157">**ulong**</span><span class="sxs-lookup"><span data-stu-id="c0964-157">**ulong**</span></span>|<span data-ttu-id="c0964-158">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="c0964-158">**UInt64**</span></span>|<span data-ttu-id="c0964-159">**unsigned __int64**</span><span class="sxs-lookup"><span data-stu-id="c0964-159">**unsigned __int64**</span></span>|<span data-ttu-id="c0964-160">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="c0964-160">**UInt64**</span></span>|  
|<span data-ttu-id="c0964-161">**float**</span><span class="sxs-lookup"><span data-stu-id="c0964-161">**float**</span></span>|<span data-ttu-id="c0964-162">**Simples**</span><span class="sxs-lookup"><span data-stu-id="c0964-162">**Single**</span></span>|<span data-ttu-id="c0964-163">**float**</span><span class="sxs-lookup"><span data-stu-id="c0964-163">**float**</span></span>|<span data-ttu-id="c0964-164">**Simples**</span><span class="sxs-lookup"><span data-stu-id="c0964-164">**Single**</span></span>|  
|<span data-ttu-id="c0964-165">**double**</span><span class="sxs-lookup"><span data-stu-id="c0964-165">**double**</span></span>|<span data-ttu-id="c0964-166">**Duplo**</span><span class="sxs-lookup"><span data-stu-id="c0964-166">**Double**</span></span>|<span data-ttu-id="c0964-167">**double**</span><span class="sxs-lookup"><span data-stu-id="c0964-167">**double**</span></span>|<span data-ttu-id="c0964-168">**Duplo**</span><span class="sxs-lookup"><span data-stu-id="c0964-168">**Double**</span></span>|  
|<span data-ttu-id="c0964-169">**bool**</span><span class="sxs-lookup"><span data-stu-id="c0964-169">**bool**</span></span>|<span data-ttu-id="c0964-170">**Booliano**</span><span class="sxs-lookup"><span data-stu-id="c0964-170">**Boolean**</span></span>|<span data-ttu-id="c0964-171">**bool**</span><span class="sxs-lookup"><span data-stu-id="c0964-171">**bool**</span></span>|<span data-ttu-id="c0964-172">**Booliano**</span><span class="sxs-lookup"><span data-stu-id="c0964-172">**Boolean**</span></span>|  
|<span data-ttu-id="c0964-173">**char**</span><span class="sxs-lookup"><span data-stu-id="c0964-173">**char**</span></span>|<span data-ttu-id="c0964-174">**Char**</span><span class="sxs-lookup"><span data-stu-id="c0964-174">**Char**</span></span>|<span data-ttu-id="c0964-175">**wchar_t**</span><span class="sxs-lookup"><span data-stu-id="c0964-175">**wchar_t**</span></span>|<span data-ttu-id="c0964-176">**Char**</span><span class="sxs-lookup"><span data-stu-id="c0964-176">**Char**</span></span>|  
|<span data-ttu-id="c0964-177">**string**</span><span class="sxs-lookup"><span data-stu-id="c0964-177">**string**</span></span>|<span data-ttu-id="c0964-178">**Cadeia de caracteres**</span><span class="sxs-lookup"><span data-stu-id="c0964-178">**String**</span></span>|<span data-ttu-id="c0964-179">**Cadeia de caracteres**</span><span class="sxs-lookup"><span data-stu-id="c0964-179">**String**</span></span>|<span data-ttu-id="c0964-180">**Cadeia de caracteres**</span><span class="sxs-lookup"><span data-stu-id="c0964-180">**String**</span></span>|  
|<span data-ttu-id="c0964-181">**object**</span><span class="sxs-lookup"><span data-stu-id="c0964-181">**object**</span></span>|<span data-ttu-id="c0964-182">**Object**</span><span class="sxs-lookup"><span data-stu-id="c0964-182">**Object**</span></span>|<span data-ttu-id="c0964-183">**Object**</span><span class="sxs-lookup"><span data-stu-id="c0964-183">**Object**</span></span>|<span data-ttu-id="c0964-184">**Object**</span><span class="sxs-lookup"><span data-stu-id="c0964-184">**Object**</span></span>|  
  
 <span data-ttu-id="c0964-185">**FAZER ✓** usar um nome comum, como `value` ou `item`, em vez de repetir o nome do tipo, em casos raros, quando um identificador não tem nenhum significado semântico e o tipo do parâmetro não é importante.</span><span class="sxs-lookup"><span data-stu-id="c0964-185">**✓ DO**  use a common name, such as `value` or `item`, rather than repeating the type name, in the rare cases when an identifier has no semantic meaning and the type of the parameter is not important.</span></span>  
  
## <a name="naming-new-versions-of-existing-apis"></a><span data-ttu-id="c0964-186">Nomenclatura novas versões de APIs existentes</span><span class="sxs-lookup"><span data-stu-id="c0964-186">Naming New Versions of Existing APIs</span></span>  
 <span data-ttu-id="c0964-187">**FAZER ✓** usar um nome semelhante à API antigo durante a criação de novas versões de uma API existente.</span><span class="sxs-lookup"><span data-stu-id="c0964-187">**✓ DO** use a name similar to the old API when creating new versions of an existing API.</span></span>  
  
 <span data-ttu-id="c0964-188">Isso ajuda a realçar a relação entre as APIs.</span><span class="sxs-lookup"><span data-stu-id="c0964-188">This helps to highlight the relationship between the APIs.</span></span>  
  
 <span data-ttu-id="c0964-189">**FAZER ✓** preferir adicionando um sufixo, em vez de um prefixo para indicar uma nova versão de uma API existente.</span><span class="sxs-lookup"><span data-stu-id="c0964-189">**✓ DO** prefer adding a suffix rather than a prefix to indicate a new version of an existing API.</span></span>  
  
 <span data-ttu-id="c0964-190">Isso ajudará a descoberta ao procurar a documentação, ou usando o Intellisense.</span><span class="sxs-lookup"><span data-stu-id="c0964-190">This will assist discovery when browsing documentation, or using Intellisense.</span></span> <span data-ttu-id="c0964-191">A versão antiga da API será organizada perto de novas APIs, como a maioria dos navegadores e Intellisense mostram identificadores em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="c0964-191">The old version of the API will be organized close to the new APIs, because most browsers and Intellisense show identifiers in alphabetical order.</span></span>  
  
 <span data-ttu-id="c0964-192">**✓ CONSIDERE** usando um identificador de novo, mas significativo, em vez de adicionar um prefixo ou um sufixo.</span><span class="sxs-lookup"><span data-stu-id="c0964-192">**✓ CONSIDER** using a brand new, but meaningful identifier, instead of adding a suffix or a prefix.</span></span>  
  
 <span data-ttu-id="c0964-193">**FAZER ✓** use um sufixo numérico para indicar uma nova versão de uma API existente, especialmente se o nome existente da API é o único nome que faça sentido (ou seja, se ele é um padrão da indústria) e se adicionando significativo qualquer sufixo (ou a alteração do nome) não é um aplicativo opção de ropriate.</span><span class="sxs-lookup"><span data-stu-id="c0964-193">**✓ DO** use a numeric suffix to indicate a new version of an existing API, particularly if the existing name of the API is the only name that makes sense (i.e., if it is an industry standard) and if adding any meaningful suffix (or changing the name) is not an appropriate option.</span></span>  
  
 <span data-ttu-id="c0964-194">**X não** usar "Ex" (ou similar) sufixo para um identificador para distingui-lo de uma versão anterior da mesma API.</span><span class="sxs-lookup"><span data-stu-id="c0964-194">**X DO NOT** use the "Ex" (or a similar) suffix for an identifier to distinguish it from an earlier version of the same API.</span></span>  
  
 <span data-ttu-id="c0964-195">**FAZER ✓** usam o sufixo "64" quando apresentando as versões de APIs que operam em um inteiro de 64 bits (um inteiro longo) em vez de um inteiro de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="c0964-195">**✓ DO** use the "64" suffix when introducing versions of APIs that operate on a 64-bit integer (a long integer) instead of a 32-bit integer.</span></span> <span data-ttu-id="c0964-196">Você só precisa usar essa abordagem à API de 32 bits existente existe; não faça isso para APIs totalmente novo com apenas uma versão de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="c0964-196">You only need to take this approach when the existing 32-bit API exists; don’t do it for brand new APIs with only a 64-bit version.</span></span>  
  
 <span data-ttu-id="c0964-197">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="c0964-197">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c0964-198">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="c0964-198">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0964-199">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0964-199">See Also</span></span>  
 [<span data-ttu-id="c0964-200">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="c0964-200">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="c0964-201">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="c0964-201">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
