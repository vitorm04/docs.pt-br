---
title: Diretrizes de Design de membro
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8f4e33735a934b1ac41c34ccb9698c172ada28e1
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="member-design-guidelines"></a><span data-ttu-id="43cd6-102">Diretrizes de Design de membro</span><span class="sxs-lookup"><span data-stu-id="43cd6-102">Member Design Guidelines</span></span>
<span data-ttu-id="43cd6-103">Métodos, propriedades, eventos, construtores e campos são chamados, coletivamente como membros.</span><span class="sxs-lookup"><span data-stu-id="43cd6-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="43cd6-104">Os membros são, por fim, o meio pelo qual funcionalidade do framework é exposta aos usuários finais de uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="43cd6-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="43cd6-105">Membros podem ser virtual ou, concreto ou abstrato, estático ou instância e podem ter vários escopos diferentes de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="43cd6-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="43cd6-106">Todos os essa variedade fornece expressividade incrível mas ao mesmo tempo requer cuidado por parte do designer de estrutura.</span><span class="sxs-lookup"><span data-stu-id="43cd6-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="43cd6-107">Este capítulo oferece diretrizes básicas que devem ser seguidas durante a criação de membros de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="43cd6-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="43cd6-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="43cd6-108">In This Section</span></span>  
 [<span data-ttu-id="43cd6-109">Sobrecarga de membro</span><span class="sxs-lookup"><span data-stu-id="43cd6-109">Member Overloading</span></span>](../../../docs/standard/design-guidelines/member-overloading.md)  
 [<span data-ttu-id="43cd6-110">Design de propriedade</span><span class="sxs-lookup"><span data-stu-id="43cd6-110">Property Design</span></span>](../../../docs/standard/design-guidelines/property.md)  
 [<span data-ttu-id="43cd6-111">Design do construtor</span><span class="sxs-lookup"><span data-stu-id="43cd6-111">Constructor Design</span></span>](../../../docs/standard/design-guidelines/constructor.md)  
 [<span data-ttu-id="43cd6-112">Design de eventos</span><span class="sxs-lookup"><span data-stu-id="43cd6-112">Event Design</span></span>](../../../docs/standard/design-guidelines/event.md)  
 [<span data-ttu-id="43cd6-113">Design de campo</span><span class="sxs-lookup"><span data-stu-id="43cd6-113">Field Design</span></span>](../../../docs/standard/design-guidelines/field.md)  
 [<span data-ttu-id="43cd6-114">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="43cd6-114">Extension Methods</span></span>](../../../docs/standard/design-guidelines/extension-methods.md)  
 [<span data-ttu-id="43cd6-115">Sobrecargas de operador</span><span class="sxs-lookup"><span data-stu-id="43cd6-115">Operator Overloads</span></span>](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [<span data-ttu-id="43cd6-116">Design de parâmetro</span><span class="sxs-lookup"><span data-stu-id="43cd6-116">Parameter Design</span></span>](../../../docs/standard/design-guidelines/parameter-design.md)  
 <span data-ttu-id="43cd6-117">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="43cd6-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="43cd6-118">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="43cd6-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43cd6-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43cd6-119">See Also</span></span>  
 [<span data-ttu-id="43cd6-120">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="43cd6-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
