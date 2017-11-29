---
title: Nomes de DLLs e Assemblies
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 071ca1547898b80440e86df0e4cb9c0667e462ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="4c3bc-102">Nomes de DLLs e Assemblies</span><span class="sxs-lookup"><span data-stu-id="4c3bc-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="4c3bc-103">Um assembly é a unidade de implantação e a identidade de programas de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4c3bc-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="4c3bc-104">Embora os assemblies podem abranger um ou mais arquivos, normalmente um assembly mapeia um para um com uma DLL.</span><span class="sxs-lookup"><span data-stu-id="4c3bc-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="4c3bc-105">Portanto, esta seção descreve somente DLL convenções de nomenclatura, que podem ser mapeadas para convenções de nomenclatura do assembly.</span><span class="sxs-lookup"><span data-stu-id="4c3bc-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>  
  
 <span data-ttu-id="4c3bc-106">**FAZER ✓** Escolha nomes do seu conjunto de DLLs que sugerem grandes blocos de funcionalidade, como System. Data.</span><span class="sxs-lookup"><span data-stu-id="4c3bc-106">**✓ DO** choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>  
  
 <span data-ttu-id="4c3bc-107">Nomes de assembly e a DLL não precisam corresponder aos nomes de namespace, mas é aconselhável ao nomear assemblies, siga o nome do namespace.</span><span class="sxs-lookup"><span data-stu-id="4c3bc-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="4c3bc-108">Uma boa regra prática é nomear a DLL com base no prefixo comum dos assemblies contidos no assembly.</span><span class="sxs-lookup"><span data-stu-id="4c3bc-108">A good rule of thumb is to name the DLL based on the common prefix of the assemblies contained in the assembly.</span></span> <span data-ttu-id="4c3bc-109">Por exemplo, um assembly com dois namespaces, `MyCompany.MyTechnology.FirstFeature` e `MyCompany.MyTechnology.SecondFeature`, poderia ser chamado `MyCompany.MyTechnology.dll`.</span><span class="sxs-lookup"><span data-stu-id="4c3bc-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>  
  
 <span data-ttu-id="4c3bc-110">**✓ CONSIDERE** nomenclatura DLLs de acordo com o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="4c3bc-110">**✓ CONSIDER** naming DLLs according to the following pattern:</span></span>  
  
 `<Company>.<Component>.dll`  
  
 <span data-ttu-id="4c3bc-111">onde `<Component>` contém uma ou mais cláusulas separados por pontos.</span><span class="sxs-lookup"><span data-stu-id="4c3bc-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="4c3bc-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4c3bc-112">For example:</span></span>  
  
 <span data-ttu-id="4c3bc-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="4c3bc-113">`Litware.Controls.dll`.</span></span>  
  
 <span data-ttu-id="4c3bc-114">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="4c3bc-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4c3bc-115">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="4c3bc-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c3bc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c3bc-116">See Also</span></span>  
 [<span data-ttu-id="4c3bc-117">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="4c3bc-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="4c3bc-118">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="4c3bc-118">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
