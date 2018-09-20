---
title: Nomes dos Assemblies e DLLs
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97bd152cff53fb1c2edb107b6d6b34bd91ca1c49
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45972053"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="ec4fb-102">Nomes dos Assemblies e DLLs</span><span class="sxs-lookup"><span data-stu-id="ec4fb-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="ec4fb-103">Um assembly é a unidade de implantação e identidade para programas de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ec4fb-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="ec4fb-104">Embora os assemblies podem abranger um ou mais arquivos, normalmente um assembly mapeia um para um com uma DLL.</span><span class="sxs-lookup"><span data-stu-id="ec4fb-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="ec4fb-105">Portanto, esta seção descreve somente DLL convenções de nomenclatura, que, em seguida, podem ser mapeadas para as convenções de nomenclatura do assembly.</span><span class="sxs-lookup"><span data-stu-id="ec4fb-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>  
  
 <span data-ttu-id="ec4fb-106">**✓ DO** Escolha nomes do seu conjunto de DLLs que sugerem grandes blocos de funcionalidade, como System. Data.</span><span class="sxs-lookup"><span data-stu-id="ec4fb-106">**✓ DO** choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>  
  
 <span data-ttu-id="ec4fb-107">Nomes de assembly e a DLL não precisam corresponder aos nomes de namespace, mas é razoável seguir o nome do namespace ao nomear os assemblies.</span><span class="sxs-lookup"><span data-stu-id="ec4fb-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="ec4fb-108">Uma boa regra prática é nomear a DLL com base no prefixo comum dos namespaces contidos no assembly.</span><span class="sxs-lookup"><span data-stu-id="ec4fb-108">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="ec4fb-109">Por exemplo, um assembly com dois namespaces, `MyCompany.MyTechnology.FirstFeature` e `MyCompany.MyTechnology.SecondFeature`, poderia ser chamado `MyCompany.MyTechnology.dll`.</span><span class="sxs-lookup"><span data-stu-id="ec4fb-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>  
  
 <span data-ttu-id="ec4fb-110">**✓ CONSIDER** nomenclatura DLLs de acordo com o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="ec4fb-110">**✓ CONSIDER** naming DLLs according to the following pattern:</span></span>  
  
 `<Company>.<Component>.dll`  
  
 <span data-ttu-id="ec4fb-111">onde `<Component>` contém uma ou mais cláusulas separados por pontos.</span><span class="sxs-lookup"><span data-stu-id="ec4fb-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="ec4fb-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ec4fb-112">For example:</span></span>  
  
 <span data-ttu-id="ec4fb-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="ec4fb-113">`Litware.Controls.dll`.</span></span>  
  
 <span data-ttu-id="ec4fb-114">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="ec4fb-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ec4fb-115">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="ec4fb-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec4fb-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec4fb-116">See also</span></span>

- [<span data-ttu-id="ec4fb-117">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="ec4fb-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="ec4fb-118">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="ec4fb-118">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
