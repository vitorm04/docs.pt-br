---
title: Nomes de Namespaces
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4fc0cb9183fde33887a3e84bb30cc3f79892586e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-namespaces"></a><span data-ttu-id="5e834-102">Nomes de Namespaces</span><span class="sxs-lookup"><span data-stu-id="5e834-102">Names of Namespaces</span></span>
<span data-ttu-id="5e834-103">Como com outras diretrizes de nomenclatura, a meta ao nomear namespaces está criando clareza suficiente para o programador usando a estrutura imediatamente saber o que é provavelmente o conteúdo do namespace.</span><span class="sxs-lookup"><span data-stu-id="5e834-103">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="5e834-104">O modelo a seguir especifica a regra geral para nomear namespaces:</span><span class="sxs-lookup"><span data-stu-id="5e834-104">The following template specifies the general rule for naming namespaces:</span></span>  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 <span data-ttu-id="5e834-105">A seguir estão exemplos:</span><span class="sxs-lookup"><span data-stu-id="5e834-105">The following are examples:</span></span>  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 <span data-ttu-id="5e834-106">**FAZER ✓** nomes de namespace com um nome de empresa para evitar namespaces de empresas diferentes tenham o mesmo nome do prefixo.</span><span class="sxs-lookup"><span data-stu-id="5e834-106">**✓ DO** prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>  
  
 <span data-ttu-id="5e834-107">**FAZER ✓** usar um nome de produto estável, independente de versão no segundo nível de um nome de namespace.</span><span class="sxs-lookup"><span data-stu-id="5e834-107">**✓ DO** use a stable, version-independent product name at the second level of a namespace name.</span></span>  
  
 <span data-ttu-id="5e834-108">**X não** usar hierarquias organizacionais como a base para nomes em hierarquias de namespace, como nomes de grupo em corporações tendem a ter vida curta.</span><span class="sxs-lookup"><span data-stu-id="5e834-108">**X DO NOT** use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="5e834-109">Organize a hierarquia de namespaces em torno de grupos de tecnologias relacionadas.</span><span class="sxs-lookup"><span data-stu-id="5e834-109">Organize the hierarchy of namespaces around groups of related technologies.</span></span>  
  
 <span data-ttu-id="5e834-110">**FAZER ✓** usar PascalCasing e componentes do namespace separado com pontos (por exemplo, `Microsoft.Office.PowerPoint`).</span><span class="sxs-lookup"><span data-stu-id="5e834-110">**✓ DO** use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="5e834-111">Se a marca emprega maiusculas e minúsculas não tradicional, você deve seguir o uso de maiusculas e minúsculas definido por sua marca, mesmo se ele tiver um desvio de maiusculas e minúsculas do namespace normal.</span><span class="sxs-lookup"><span data-stu-id="5e834-111">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>  
  
 <span data-ttu-id="5e834-112">**✓ CONSIDERE** usando nomes de namespace no plural quando apropriado.</span><span class="sxs-lookup"><span data-stu-id="5e834-112">**✓ CONSIDER** using plural namespace names where appropriate.</span></span>  
  
 <span data-ttu-id="5e834-113">Por exemplo, use `System.Collections` em vez de `System.Collection`.</span><span class="sxs-lookup"><span data-stu-id="5e834-113">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="5e834-114">Nomes de marca e acrônimos são exceções a essa regra, no entanto.</span><span class="sxs-lookup"><span data-stu-id="5e834-114">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="5e834-115">Por exemplo, use `System.IO` em vez de `System.IOs`.</span><span class="sxs-lookup"><span data-stu-id="5e834-115">For example, use `System.IO` instead of `System.IOs`.</span></span>  
  
 <span data-ttu-id="5e834-116">**X não** usar o mesmo nome de um namespace e um tipo no namespace.</span><span class="sxs-lookup"><span data-stu-id="5e834-116">**X DO NOT** use the same name for a namespace and a type in that namespace.</span></span>  
  
 <span data-ttu-id="5e834-117">Por exemplo, não use `Debug` como um namespace do nome e, em seguida, também fornecem uma classe denominada `Debug` no mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="5e834-117">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="5e834-118">Alguns compiladores exigem tipos totalmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="5e834-118">Several compilers require such types to be fully qualified.</span></span>  
  
### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="5e834-119">Namespaces e conflitos de nome de tipo</span><span class="sxs-lookup"><span data-stu-id="5e834-119">Namespaces and Type Name Conflicts</span></span>  
 <span data-ttu-id="5e834-120">**X não** apresentar nomes de tipo genérico como `Element`, `Node`, `Log`, e `Message`.</span><span class="sxs-lookup"><span data-stu-id="5e834-120">**X DO NOT** introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>  
  
 <span data-ttu-id="5e834-121">Há uma probabilidade muito alta que fazer isso levará para o nome de tipo está em conflito em comum cenários.</span><span class="sxs-lookup"><span data-stu-id="5e834-121">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="5e834-122">Você deve qualificar os nomes de tipo genérico (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span><span class="sxs-lookup"><span data-stu-id="5e834-122">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>  
  
 <span data-ttu-id="5e834-123">Há instruções específicas para evitar conflitos de nome de tipo para categorias diferentes de namespaces.</span><span class="sxs-lookup"><span data-stu-id="5e834-123">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>  
  
-   <span data-ttu-id="5e834-124">**Namespaces do modelo de aplicativo**</span><span class="sxs-lookup"><span data-stu-id="5e834-124">**Application model namespaces**</span></span>  
  
     <span data-ttu-id="5e834-125">Namespaces que pertencem a um modelo de aplicativo único com muita frequência, são usados juntos, mas quase nunca são usadas com namespaces de outros modelos de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5e834-125">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="5e834-126">Por exemplo, o <xref:System.Windows.Forms?displayProperty=nameWithType> namespace muito raramente é usado junto com o <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="5e834-126">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="5e834-127">A seguir está uma lista de grupos de namespace do modelo de aplicativo conhecidas:</span><span class="sxs-lookup"><span data-stu-id="5e834-127">The following is a list of well-known application model namespace groups:</span></span>  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     <span data-ttu-id="5e834-128">**X não** atribuir o mesmo nome para tipos em namespaces dentro de um modelo de aplicativo único.</span><span class="sxs-lookup"><span data-stu-id="5e834-128">**X DO NOT** give the same name to types in namespaces within a single application model.</span></span>  
  
     <span data-ttu-id="5e834-129">Por exemplo, não adicione um tipo chamado `Page` para o <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, porque o <xref:System.Web.UI?displayProperty=nameWithType> namespace já contém um tipo chamado `Page`.</span><span class="sxs-lookup"><span data-stu-id="5e834-129">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>  
  
-   <span data-ttu-id="5e834-130">**Namespaces de infraestrutura**</span><span class="sxs-lookup"><span data-stu-id="5e834-130">**Infrastructure namespaces**</span></span>  
  
     <span data-ttu-id="5e834-131">Esse grupo contém namespaces que raramente são importados durante o desenvolvimento de aplicativos comuns.</span><span class="sxs-lookup"><span data-stu-id="5e834-131">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="5e834-132">Por exemplo, `.Design` namespaces são usados principalmente quando as ferramentas de desenvolvimento de programação.</span><span class="sxs-lookup"><span data-stu-id="5e834-132">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="5e834-133">Evitando conflitos com os tipos nesses namespaces, não é crítico.</span><span class="sxs-lookup"><span data-stu-id="5e834-133">Avoiding conflicts with types in these namespaces is not critical.</span></span>  
  
-   <span data-ttu-id="5e834-134">**Namespaces de núcleo**</span><span class="sxs-lookup"><span data-stu-id="5e834-134">**Core namespaces**</span></span>  
  
     <span data-ttu-id="5e834-135">Namespaces básicos incluem todos os `System` namespaces, excluindo espaços para nome dos modelos de aplicativo e os namespaces de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="5e834-135">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="5e834-136">Namespaces básicos incluem, entre outros, `System`, `System.IO`, `System.Xml`, e `System.Net`.</span><span class="sxs-lookup"><span data-stu-id="5e834-136">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>  
  
     <span data-ttu-id="5e834-137">**X não** fornecem tipos de nomes que entraria em conflito com qualquer tipo nos namespaces Core.</span><span class="sxs-lookup"><span data-stu-id="5e834-137">**X DO NOT** give types names that would conflict with any type in the Core namespaces.</span></span>  
  
     <span data-ttu-id="5e834-138">Por exemplo, nunca use `Stream` como um nome de tipo.</span><span class="sxs-lookup"><span data-stu-id="5e834-138">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="5e834-139">Ela entraria em conflito com <xref:System.IO.Stream?displayProperty=nameWithType>, um tipo muito usados.</span><span class="sxs-lookup"><span data-stu-id="5e834-139">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>  
  
-   <span data-ttu-id="5e834-140">**Grupos de espaço para nome de tecnologia**</span><span class="sxs-lookup"><span data-stu-id="5e834-140">**Technology namespace groups**</span></span>  
  
     <span data-ttu-id="5e834-141">Essa categoria inclui todos os namespaces com os dois primeiros nós de namespace mesmo `(<Company>.<Technology>*`), como `Microsoft.Build.Utilities` e `Microsoft.Build.Tasks`.</span><span class="sxs-lookup"><span data-stu-id="5e834-141">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="5e834-142">É importante que tipos que pertencem a uma única tecnologia não entrem em conflito entre si.</span><span class="sxs-lookup"><span data-stu-id="5e834-142">It is important that types belonging to a single technology do not conflict with each other.</span></span>  
  
     <span data-ttu-id="5e834-143">**X não** atribuir nomes de tipo que entraria em conflito com outros tipos em uma única tecnologia.</span><span class="sxs-lookup"><span data-stu-id="5e834-143">**X DO NOT** assign type names that would conflict with other types within a single technology.</span></span>  
  
     <span data-ttu-id="5e834-144">**X não** apresentam conflitos de nome de tipo entre os tipos nos namespaces de tecnologia e um namespace do modelo de aplicativo (a menos que a tecnologia não se destina a ser usado com o modelo de aplicativo).</span><span class="sxs-lookup"><span data-stu-id="5e834-144">**X DO NOT** introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>  
  
 <span data-ttu-id="5e834-145">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="5e834-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="5e834-146">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="5e834-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e834-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e834-147">See Also</span></span>  
 [<span data-ttu-id="5e834-148">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="5e834-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="5e834-149">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="5e834-149">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
