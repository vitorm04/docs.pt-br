---
title: Nomes de Namespaces
ms.date: 03/30/2017
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d68966f60c5039fd67195a03facc1586b9ed154
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44097003"
---
# <a name="names-of-namespaces"></a><span data-ttu-id="d7adb-102">Nomes de Namespaces</span><span class="sxs-lookup"><span data-stu-id="d7adb-102">Names of Namespaces</span></span>
<span data-ttu-id="d7adb-103">Como com outras diretrizes de nomenclatura, a meta ao nomear namespaces é criando clareza suficiente para o programador usando a estrutura de saber imediatamente qual o conteúdo do namespace é provavelmente será.</span><span class="sxs-lookup"><span data-stu-id="d7adb-103">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="d7adb-104">O modelo a seguir especifica a regra geral para a nomeação de namespaces:</span><span class="sxs-lookup"><span data-stu-id="d7adb-104">The following template specifies the general rule for naming namespaces:</span></span>  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 <span data-ttu-id="d7adb-105">A seguir estão exemplos:</span><span class="sxs-lookup"><span data-stu-id="d7adb-105">The following are examples:</span></span>  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 <span data-ttu-id="d7adb-106">**✓ DO** nomes de namespace com um nome de empresa para evitar namespaces de empresas diferentes tenham o mesmo nome do prefixo.</span><span class="sxs-lookup"><span data-stu-id="d7adb-106">**✓ DO** prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>  
  
 <span data-ttu-id="d7adb-107">**✓ DO** usar um nome de produto estável, independente de versão no segundo nível de um nome de namespace.</span><span class="sxs-lookup"><span data-stu-id="d7adb-107">**✓ DO** use a stable, version-independent product name at the second level of a namespace name.</span></span>  
  
 <span data-ttu-id="d7adb-108">**X DO NOT** usar hierarquias organizacionais como a base para nomes em hierarquias de namespace, como nomes de grupo em corporações tendem a ter vida curta.</span><span class="sxs-lookup"><span data-stu-id="d7adb-108">**X DO NOT** use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="d7adb-109">Organize a hierarquia de namespaces em torno de grupos de tecnologias relacionadas.</span><span class="sxs-lookup"><span data-stu-id="d7adb-109">Organize the hierarchy of namespaces around groups of related technologies.</span></span>  
  
 <span data-ttu-id="d7adb-110">**✓ DO** usar PascalCasing e componentes do namespace separado com pontos (por exemplo, `Microsoft.Office.PowerPoint`).</span><span class="sxs-lookup"><span data-stu-id="d7adb-110">**✓ DO** use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="d7adb-111">Se a sua marca emprega maiusculas e minúsculas não tradicional, você deve seguir as maiusculas e minúsculas definida pela sua marca, mesmo se ele tiver um desvio do uso de maiusculas e minúsculas do namespace normal.</span><span class="sxs-lookup"><span data-stu-id="d7adb-111">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>  
  
 <span data-ttu-id="d7adb-112">**✓ CONSIDER** usando nomes de namespace no plural quando apropriado.</span><span class="sxs-lookup"><span data-stu-id="d7adb-112">**✓ CONSIDER** using plural namespace names where appropriate.</span></span>  
  
 <span data-ttu-id="d7adb-113">Por exemplo, use `System.Collections` em vez de `System.Collection`.</span><span class="sxs-lookup"><span data-stu-id="d7adb-113">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="d7adb-114">Nomes de marca e acrônimos são exceções a essa regra, no entanto.</span><span class="sxs-lookup"><span data-stu-id="d7adb-114">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="d7adb-115">Por exemplo, use `System.IO` em vez de `System.IOs`.</span><span class="sxs-lookup"><span data-stu-id="d7adb-115">For example, use `System.IO` instead of `System.IOs`.</span></span>  
  
 <span data-ttu-id="d7adb-116">**X DO NOT** usar o mesmo nome de um namespace e um tipo no namespace.</span><span class="sxs-lookup"><span data-stu-id="d7adb-116">**X DO NOT** use the same name for a namespace and a type in that namespace.</span></span>  
  
 <span data-ttu-id="d7adb-117">Por exemplo, não use `Debug` como um namespace Nomeie e, em seguida, forneça também uma classe chamada `Debug` no mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="d7adb-117">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="d7adb-118">Os diversos compiladores exigem tais tipos totalmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="d7adb-118">Several compilers require such types to be fully qualified.</span></span>  
  
### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="d7adb-119">Namespaces e conflitos de nome de tipo</span><span class="sxs-lookup"><span data-stu-id="d7adb-119">Namespaces and Type Name Conflicts</span></span>  
 <span data-ttu-id="d7adb-120">**X DO NOT** apresentar nomes de tipo genérico como `Element`, `Node`, `Log`, e `Message`.</span><span class="sxs-lookup"><span data-stu-id="d7adb-120">**X DO NOT** introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>  
  
 <span data-ttu-id="d7adb-121">Há uma probabilidade muito alta que fazer isso levará para o nome de tipo está em conflito em comum cenários.</span><span class="sxs-lookup"><span data-stu-id="d7adb-121">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="d7adb-122">Você deve qualificar os nomes de tipo genérico (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span><span class="sxs-lookup"><span data-stu-id="d7adb-122">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>  
  
 <span data-ttu-id="d7adb-123">Há diretrizes específicas para evitar conflitos de nome de tipo para categorias diferentes de namespaces.</span><span class="sxs-lookup"><span data-stu-id="d7adb-123">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>  
  
-   <span data-ttu-id="d7adb-124">**Namespaces de modelos de aplicativo**</span><span class="sxs-lookup"><span data-stu-id="d7adb-124">**Application model namespaces**</span></span>  
  
     <span data-ttu-id="d7adb-125">Os namespaces que pertencem a um modelo de aplicativo único muito geralmente são usados juntos, mas quase nunca são usadas com namespaces de outros modelos de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7adb-125">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="d7adb-126">Por exemplo, o <xref:System.Windows.Forms?displayProperty=nameWithType> namespace muito raramente é usado junto com o <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="d7adb-126">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="d7adb-127">A seguir está uma lista de grupos de namespace do modelo de aplicativo bem conhecido:</span><span class="sxs-lookup"><span data-stu-id="d7adb-127">The following is a list of well-known application model namespace groups:</span></span>  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     <span data-ttu-id="d7adb-128">**X DO NOT** atribuir o mesmo nome para tipos em namespaces dentro de um modelo de aplicativo único.</span><span class="sxs-lookup"><span data-stu-id="d7adb-128">**X DO NOT** give the same name to types in namespaces within a single application model.</span></span>  
  
     <span data-ttu-id="d7adb-129">Por exemplo, não adicione um tipo chamado `Page` para o <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, porque o <xref:System.Web.UI?displayProperty=nameWithType> namespace já contém um tipo chamado `Page`.</span><span class="sxs-lookup"><span data-stu-id="d7adb-129">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>  
  
-   <span data-ttu-id="d7adb-130">**Namespaces de infraestrutura**</span><span class="sxs-lookup"><span data-stu-id="d7adb-130">**Infrastructure namespaces**</span></span>  
  
     <span data-ttu-id="d7adb-131">Esse grupo contém os namespaces que raramente são importados durante o desenvolvimento de aplicativos comuns.</span><span class="sxs-lookup"><span data-stu-id="d7adb-131">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="d7adb-132">Por exemplo, `.Design` namespaces são usados principalmente das ferramentas de desenvolvimento de programação.</span><span class="sxs-lookup"><span data-stu-id="d7adb-132">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="d7adb-133">Evitando conflitos com os tipos nesses namespaces não é crítica.</span><span class="sxs-lookup"><span data-stu-id="d7adb-133">Avoiding conflicts with types in these namespaces is not critical.</span></span>  
  
-   <span data-ttu-id="d7adb-134">**Namespaces básicos**</span><span class="sxs-lookup"><span data-stu-id="d7adb-134">**Core namespaces**</span></span>  
  
     <span data-ttu-id="d7adb-135">Namespaces básicos incluem todas `System` namespaces, exceto os namespaces dos modelos de aplicativo e os namespaces de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="d7adb-135">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="d7adb-136">Namespaces básicos incluem, entre outros, `System`, `System.IO`, `System.Xml`, e `System.Net`.</span><span class="sxs-lookup"><span data-stu-id="d7adb-136">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>  
  
     <span data-ttu-id="d7adb-137">**X DO NOT** fornecem tipos de nomes que entraria em conflito com qualquer tipo nos namespaces Core.</span><span class="sxs-lookup"><span data-stu-id="d7adb-137">**X DO NOT** give types names that would conflict with any type in the Core namespaces.</span></span>  
  
     <span data-ttu-id="d7adb-138">Por exemplo, nunca use `Stream` como um nome de tipo.</span><span class="sxs-lookup"><span data-stu-id="d7adb-138">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="d7adb-139">Ela entraria em conflito com <xref:System.IO.Stream?displayProperty=nameWithType>, um tipo muito usados.</span><span class="sxs-lookup"><span data-stu-id="d7adb-139">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>  
  
-   <span data-ttu-id="d7adb-140">**Grupos de namespace de tecnologia**</span><span class="sxs-lookup"><span data-stu-id="d7adb-140">**Technology namespace groups**</span></span>  
  
     <span data-ttu-id="d7adb-141">Essa categoria inclui todos os namespaces com os dois primeiros nós de namespace mesmo `(<Company>.<Technology>*`), como `Microsoft.Build.Utilities` e `Microsoft.Build.Tasks`.</span><span class="sxs-lookup"><span data-stu-id="d7adb-141">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="d7adb-142">É importante que os tipos que pertencem a uma única tecnologia não entrem em conflito umas com as outras.</span><span class="sxs-lookup"><span data-stu-id="d7adb-142">It is important that types belonging to a single technology do not conflict with each other.</span></span>  
  
     <span data-ttu-id="d7adb-143">**X DO NOT** atribuir nomes de tipo que entraria em conflito com outros tipos em uma única tecnologia.</span><span class="sxs-lookup"><span data-stu-id="d7adb-143">**X DO NOT** assign type names that would conflict with other types within a single technology.</span></span>  
  
     <span data-ttu-id="d7adb-144">**X DO NOT** apresentam conflitos de nome de tipo entre os tipos nos namespaces de tecnologia e um namespace do modelo de aplicativo (a menos que a tecnologia não se destina a ser usado com o modelo de aplicativo).</span><span class="sxs-lookup"><span data-stu-id="d7adb-144">**X DO NOT** introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>  
  
 <span data-ttu-id="d7adb-145">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="d7adb-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d7adb-146">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="d7adb-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7adb-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7adb-147">See also</span></span>

- [<span data-ttu-id="d7adb-148">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="d7adb-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="d7adb-149">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="d7adb-149">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
