---
title: Nomes de namespaces
description: Use estas diretrizes para nomear namespaces como parte das diretrizes para criar bibliotecas que estendem e interajam com bibliotecas .NET.
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: e435e0281165b4a9f12bbccbeb10401b57375dcb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290195"
---
# <a name="names-of-namespaces"></a><span data-ttu-id="d2481-103">Nomes de namespaces</span><span class="sxs-lookup"><span data-stu-id="d2481-103">Names of Namespaces</span></span>
<span data-ttu-id="d2481-104">Assim como acontece com outras diretrizes de nomenclatura, a meta ao nomear namespaces é criar uma clareza suficiente para o programador usando a estrutura para saber imediatamente qual é a probabilidade do conteúdo do namespace.</span><span class="sxs-lookup"><span data-stu-id="d2481-104">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="d2481-105">O modelo a seguir especifica a regra geral para nomes de namespaces:</span><span class="sxs-lookup"><span data-stu-id="d2481-105">The following template specifies the general rule for naming namespaces:</span></span>

 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`

 <span data-ttu-id="d2481-106">Os exemplos são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="d2481-106">The following are examples:</span></span>

 <span data-ttu-id="d2481-107">`Fabrikam.Math` `Litware.Security`</span><span class="sxs-lookup"><span data-stu-id="d2481-107">`Fabrikam.Math` `Litware.Security`</span></span>

 <span data-ttu-id="d2481-108">✔️ os nomes de namespace de prefixo com um nome de empresa para impedir que os namespaces de diferentes empresas tenham o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="d2481-108">✔️ DO prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>

 <span data-ttu-id="d2481-109">✔️ usar um nome de produto estável e independente de versão no segundo nível de um nome de namespace.</span><span class="sxs-lookup"><span data-stu-id="d2481-109">✔️ DO use a stable, version-independent product name at the second level of a namespace name.</span></span>

 <span data-ttu-id="d2481-110">❌Não use hierarquias organizacionais como base para nomes em hierarquias de namespace, pois os nomes de grupo nas empresas tendem a ser de curta duração.</span><span class="sxs-lookup"><span data-stu-id="d2481-110">❌ DO NOT use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="d2481-111">Organize a hierarquia de namespaces em relação a grupos de tecnologias relacionadas.</span><span class="sxs-lookup"><span data-stu-id="d2481-111">Organize the hierarchy of namespaces around groups of related technologies.</span></span>

 <span data-ttu-id="d2481-112">✔️ usar PascalCasing e separar componentes de namespace com pontos (por exemplo, `Microsoft.Office.PowerPoint` ).</span><span class="sxs-lookup"><span data-stu-id="d2481-112">✔️ DO use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="d2481-113">Se sua marca emprega um uso não tradicional, você deve seguir a capitalização definida por sua marca, mesmo que ela se desvie da capitalização normal do namespace.</span><span class="sxs-lookup"><span data-stu-id="d2481-113">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>

 <span data-ttu-id="d2481-114">✔️ Considere o uso de nomes de namespace do plural quando apropriado.</span><span class="sxs-lookup"><span data-stu-id="d2481-114">✔️ CONSIDER using plural namespace names where appropriate.</span></span>

 <span data-ttu-id="d2481-115">Por exemplo, use `System.Collections` ao invés de `System.Collection`.</span><span class="sxs-lookup"><span data-stu-id="d2481-115">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="d2481-116">No entanto, os nomes e acrônimos de marca são exceções a essa regra.</span><span class="sxs-lookup"><span data-stu-id="d2481-116">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="d2481-117">Por exemplo, use `System.IO` ao invés de `System.IOs`.</span><span class="sxs-lookup"><span data-stu-id="d2481-117">For example, use `System.IO` instead of `System.IOs`.</span></span>

 <span data-ttu-id="d2481-118">❌Não use o mesmo nome para um namespace e um tipo nesse namespace.</span><span class="sxs-lookup"><span data-stu-id="d2481-118">❌ DO NOT use the same name for a namespace and a type in that namespace.</span></span>

 <span data-ttu-id="d2481-119">Por exemplo, não use `Debug` como um nome de namespace e, em seguida, forneça uma classe chamada `Debug` no mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="d2481-119">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="d2481-120">Vários compiladores exigem que esses tipos sejam totalmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="d2481-120">Several compilers require such types to be fully qualified.</span></span>

### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="d2481-121">Namespaces e conflitos de nome de tipo</span><span class="sxs-lookup"><span data-stu-id="d2481-121">Namespaces and Type Name Conflicts</span></span>
 <span data-ttu-id="d2481-122">❌Não introduza nomes de tipos genéricos, como,, `Element` `Node` `Log` e `Message` .</span><span class="sxs-lookup"><span data-stu-id="d2481-122">❌ DO NOT introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>

 <span data-ttu-id="d2481-123">Há uma probabilidade muito alta de fazer isso resultará em conflitos de nome de tipo em cenários comuns.</span><span class="sxs-lookup"><span data-stu-id="d2481-123">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="d2481-124">Você deve qualificar os nomes de tipo genérico ( `FormElement` , `XmlNode` , `EventLog` , `SoapMessage` ).</span><span class="sxs-lookup"><span data-stu-id="d2481-124">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>

 <span data-ttu-id="d2481-125">Há diretrizes específicas para evitar conflitos de nome de tipo para diferentes categorias de namespaces.</span><span class="sxs-lookup"><span data-stu-id="d2481-125">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>

- <span data-ttu-id="d2481-126">**Namespaces de modelo de aplicativo**</span><span class="sxs-lookup"><span data-stu-id="d2481-126">**Application model namespaces**</span></span>

     <span data-ttu-id="d2481-127">Os namespaces que pertencem a um único modelo de aplicativo geralmente são usados juntos, mas quase nunca são usados com namespaces de outros modelos de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d2481-127">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="d2481-128">Por exemplo, o <xref:System.Windows.Forms?displayProperty=nameWithType> namespace é muito raramente usado junto com o <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="d2481-128">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="d2481-129">Veja a seguir uma lista de grupos de namespace de modelo de aplicativo conhecidos:</span><span class="sxs-lookup"><span data-stu-id="d2481-129">The following is a list of well-known application model namespace groups:</span></span>

     <span data-ttu-id="d2481-130">`System.Windows*` `System.Web.UI*`</span><span class="sxs-lookup"><span data-stu-id="d2481-130">`System.Windows*` `System.Web.UI*`</span></span>

     <span data-ttu-id="d2481-131">❌Não atribua o mesmo nome a tipos em namespaces em um único modelo de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d2481-131">❌ DO NOT give the same name to types in namespaces within a single application model.</span></span>

     <span data-ttu-id="d2481-132">Por exemplo, não adicione um tipo chamado `Page` ao <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, pois o <xref:System.Web.UI?displayProperty=nameWithType> namespace já contém um tipo chamado `Page` .</span><span class="sxs-lookup"><span data-stu-id="d2481-132">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>

- <span data-ttu-id="d2481-133">**Namespaces de infraestrutura**</span><span class="sxs-lookup"><span data-stu-id="d2481-133">**Infrastructure namespaces**</span></span>

     <span data-ttu-id="d2481-134">Esse grupo contém namespaces que raramente são importados durante o desenvolvimento de aplicativos comuns.</span><span class="sxs-lookup"><span data-stu-id="d2481-134">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="d2481-135">Por exemplo, os `.Design` namespaces são usados principalmente ao desenvolver ferramentas de programação.</span><span class="sxs-lookup"><span data-stu-id="d2481-135">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="d2481-136">Evitar conflitos com tipos nesses namespaces não é crítico.</span><span class="sxs-lookup"><span data-stu-id="d2481-136">Avoiding conflicts with types in these namespaces is not critical.</span></span>

- <span data-ttu-id="d2481-137">**Principais namespaces**</span><span class="sxs-lookup"><span data-stu-id="d2481-137">**Core namespaces**</span></span>

     <span data-ttu-id="d2481-138">Os namespaces de núcleo incluem todos os `System` namespaces, excluindo namespaces dos modelos de aplicativo e os namespaces de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="d2481-138">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="d2481-139">Os namespaces de núcleo incluem, entre outros,,,, `System` `System.IO` `System.Xml` e `System.Net` .</span><span class="sxs-lookup"><span data-stu-id="d2481-139">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>

     <span data-ttu-id="d2481-140">❌Não forneça nomes de tipos que possam entrar em conflito com qualquer tipo nos namespaces de núcleo.</span><span class="sxs-lookup"><span data-stu-id="d2481-140">❌ DO NOT give types names that would conflict with any type in the Core namespaces.</span></span>

     <span data-ttu-id="d2481-141">Por exemplo, nunca use `Stream` como um nome de tipo.</span><span class="sxs-lookup"><span data-stu-id="d2481-141">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="d2481-142">Ele estaria em conflito com <xref:System.IO.Stream?displayProperty=nameWithType> um tipo muito usado.</span><span class="sxs-lookup"><span data-stu-id="d2481-142">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>

- <span data-ttu-id="d2481-143">**Grupos de namespace de tecnologia**</span><span class="sxs-lookup"><span data-stu-id="d2481-143">**Technology namespace groups**</span></span>

     <span data-ttu-id="d2481-144">Essa categoria inclui todos os namespaces com os mesmos primeiros dois nós de namespace `(<Company>.<Technology>*` ), como `Microsoft.Build.Utilities` e `Microsoft.Build.Tasks` .</span><span class="sxs-lookup"><span data-stu-id="d2481-144">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="d2481-145">É importante que os tipos que pertencem a uma única tecnologia não entrem em conflito entre si.</span><span class="sxs-lookup"><span data-stu-id="d2481-145">It is important that types belonging to a single technology do not conflict with each other.</span></span>

     <span data-ttu-id="d2481-146">❌Não atribua nomes de tipos que possam entrar em conflito com outros tipos em uma única tecnologia.</span><span class="sxs-lookup"><span data-stu-id="d2481-146">❌ DO NOT assign type names that would conflict with other types within a single technology.</span></span>

     <span data-ttu-id="d2481-147">❌Não introduza o nome do tipo em conflito entre os tipos nos namespaces de tecnologia e um namespace de modelo de aplicativo (a menos que a tecnologia não se destinar a ser usada com o modelo de aplicativo).</span><span class="sxs-lookup"><span data-stu-id="d2481-147">❌ DO NOT introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>

 <span data-ttu-id="d2481-148">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="d2481-148">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="d2481-149">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="d2481-149">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="d2481-150">Veja também</span><span class="sxs-lookup"><span data-stu-id="d2481-150">See also</span></span>

- [<span data-ttu-id="d2481-151">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="d2481-151">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="d2481-152">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="d2481-152">Naming Guidelines</span></span>](naming-guidelines.md)
