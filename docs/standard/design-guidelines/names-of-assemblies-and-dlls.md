---
title: Nomes de Assemblies e DLLs
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
author: KrzysztofCwalina
ms.openlocfilehash: 1aeef9e1be6e5fe747f440a8cb7f21095cb22f49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945490"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="1922b-102">Nomes de Assemblies e DLLs</span><span class="sxs-lookup"><span data-stu-id="1922b-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="1922b-103">Um assembly é a unidade de implantação e identidade para programas de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1922b-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="1922b-104">Embora os assemblies podem abranger um ou mais arquivos, normalmente um assembly mapeia um para um com uma DLL.</span><span class="sxs-lookup"><span data-stu-id="1922b-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="1922b-105">Portanto, esta seção descreve somente DLL convenções de nomenclatura, que, em seguida, podem ser mapeadas para as convenções de nomenclatura do assembly.</span><span class="sxs-lookup"><span data-stu-id="1922b-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>  
  
 <span data-ttu-id="1922b-106">**✓ DO** Escolha nomes do seu conjunto de DLLs que sugerem grandes blocos de funcionalidade, como System. Data.</span><span class="sxs-lookup"><span data-stu-id="1922b-106">**✓ DO** choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>  
  
 <span data-ttu-id="1922b-107">Nomes de assembly e a DLL não precisam corresponder aos nomes de namespace, mas é razoável seguir o nome do namespace ao nomear os assemblies.</span><span class="sxs-lookup"><span data-stu-id="1922b-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="1922b-108">Uma boa regra prática é nomear a DLL com base no prefixo comum dos namespaces contidos no assembly.</span><span class="sxs-lookup"><span data-stu-id="1922b-108">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="1922b-109">Por exemplo, um assembly com dois namespaces, `MyCompany.MyTechnology.FirstFeature` e `MyCompany.MyTechnology.SecondFeature`, poderia ser chamado `MyCompany.MyTechnology.dll`.</span><span class="sxs-lookup"><span data-stu-id="1922b-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>  
  
 <span data-ttu-id="1922b-110">**✓ CONSIDER** nomenclatura DLLs de acordo com o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="1922b-110">**✓ CONSIDER** naming DLLs according to the following pattern:</span></span>  
  
 `<Company>.<Component>.dll`  
  
 <span data-ttu-id="1922b-111">onde `<Component>` contém uma ou mais cláusulas separados por pontos.</span><span class="sxs-lookup"><span data-stu-id="1922b-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="1922b-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1922b-112">For example:</span></span>  
  
 <span data-ttu-id="1922b-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="1922b-113">`Litware.Controls.dll`.</span></span>  
  
 <span data-ttu-id="1922b-114">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="1922b-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1922b-115">*Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="1922b-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1922b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1922b-116">See also</span></span>

- [<span data-ttu-id="1922b-117">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="1922b-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="1922b-118">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="1922b-118">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
