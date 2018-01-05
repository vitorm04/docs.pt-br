---
title: Design de classe abstrata
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 739f86acd534549bc997dc7a939cf43a0c6fc3cb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="abstract-class-design"></a><span data-ttu-id="5d008-102">Design de classe abstrata</span><span class="sxs-lookup"><span data-stu-id="5d008-102">Abstract Class Design</span></span>
<span data-ttu-id="5d008-103">**X não** definir construtores internos públicos ou privados em tipos abstratos.</span><span class="sxs-lookup"><span data-stu-id="5d008-103">**X DO NOT** define public or protected internal constructors in abstract types.</span></span>  
  
 <span data-ttu-id="5d008-104">Construtores devem ser públicos somente se os usuários precisarão criar instâncias do tipo.</span><span class="sxs-lookup"><span data-stu-id="5d008-104">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="5d008-105">Porque você não pode criar instâncias de um tipo abstrato, um tipo abstrato com um construtor público incorretamente é projetado e falsos para os usuários.</span><span class="sxs-lookup"><span data-stu-id="5d008-105">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>  
  
 <span data-ttu-id="5d008-106">**FAZER ✓** definir um construtor interno ou uma protegidos em classes abstratas.</span><span class="sxs-lookup"><span data-stu-id="5d008-106">**✓ DO** define a protected or an internal constructor in abstract classes.</span></span>  
  
 <span data-ttu-id="5d008-107">Um construtor protegido é mais comum e simplesmente permite que a classe base fazer seu próprios inicialização quando os subtipos são criados.</span><span class="sxs-lookup"><span data-stu-id="5d008-107">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>  
  
 <span data-ttu-id="5d008-108">Um construtor interno pode ser usado para limitar as implementações concretas de classe abstrata para o assembly que define a classe.</span><span class="sxs-lookup"><span data-stu-id="5d008-108">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>  
  
 <span data-ttu-id="5d008-109">**FAZER ✓** fornecer pelo menos um tipo concreto que herda de cada classe abstrata que você enviar.</span><span class="sxs-lookup"><span data-stu-id="5d008-109">**✓ DO** provide at least one concrete type that inherits from each abstract class that you ship.</span></span>  
  
 <span data-ttu-id="5d008-110">Fazer isso ajuda a validar o design da classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="5d008-110">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="5d008-111">Por exemplo, <xref:System.IO.FileStream?displayProperty=nameWithType> é uma implementação de <xref:System.IO.Stream?displayProperty=nameWithType> classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="5d008-111">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>  
  
 <span data-ttu-id="5d008-112">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="5d008-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="5d008-113">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="5d008-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d008-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d008-114">See Also</span></span>  
 [<span data-ttu-id="5d008-115">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="5d008-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="5d008-116">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="5d008-116">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
