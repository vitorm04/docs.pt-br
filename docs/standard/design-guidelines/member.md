---
title: Diretrizes de design de membro
description: Aprenda as diretrizes de design de membro no .NET. Os membros incluem métodos, propriedades, eventos, construtores e campos.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
ms.openlocfilehash: a1f0c1d74e8bffa7cfef975c7dafb9fd01479470
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594485"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="4f4de-104">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="4f4de-104">Member Design Guidelines</span></span>
<span data-ttu-id="4f4de-105">Métodos, propriedades, eventos, construtores e campos são chamados coletivamente de membros.</span><span class="sxs-lookup"><span data-stu-id="4f4de-105">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="4f4de-106">Os membros são, em última instância, o meio pelo qual a funcionalidade de estrutura é exposta aos usuários finais de uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="4f4de-106">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="4f4de-107">Os membros podem ser virtuais ou não virtuais, concretos ou abstratos, estáticos ou de instância, e podem ter vários escopos diferentes de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="4f4de-107">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="4f4de-108">Toda essa variedade fornece uma expressividade incrível, mas, ao mesmo tempo, requer cuidado com a parte do designer de Framework.</span><span class="sxs-lookup"><span data-stu-id="4f4de-108">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="4f4de-109">Este capítulo oferece diretrizes básicas que devem ser seguidas durante a criação de membros de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="4f4de-109">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4f4de-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="4f4de-110">In This Section</span></span>  
 [<span data-ttu-id="4f4de-111">Sobrecarga de membros</span><span class="sxs-lookup"><span data-stu-id="4f4de-111">Member Overloading</span></span>](member-overloading.md)  
 [<span data-ttu-id="4f4de-112">Design de propriedade</span><span class="sxs-lookup"><span data-stu-id="4f4de-112">Property Design</span></span>](property.md)  
 [<span data-ttu-id="4f4de-113">Design do Construtor</span><span class="sxs-lookup"><span data-stu-id="4f4de-113">Constructor Design</span></span>](constructor.md)  
 [<span data-ttu-id="4f4de-114">Design de eventos</span><span class="sxs-lookup"><span data-stu-id="4f4de-114">Event Design</span></span>](event.md)  
 [<span data-ttu-id="4f4de-115">Design de campo</span><span class="sxs-lookup"><span data-stu-id="4f4de-115">Field Design</span></span>](field.md)  
 [<span data-ttu-id="4f4de-116">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="4f4de-116">Extension Methods</span></span>](extension-methods.md)  
 [<span data-ttu-id="4f4de-117">Sobrecargas de operador</span><span class="sxs-lookup"><span data-stu-id="4f4de-117">Operator Overloads</span></span>](operator-overloads.md)  
 [<span data-ttu-id="4f4de-118">Design de parâmetro</span><span class="sxs-lookup"><span data-stu-id="4f4de-118">Parameter Design</span></span>](parameter-design.md)  
 <span data-ttu-id="4f4de-119">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="4f4de-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4f4de-120">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="4f4de-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f4de-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="4f4de-121">See also</span></span>

- [<span data-ttu-id="4f4de-122">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="4f4de-122">Framework Design Guidelines</span></span>](index.md)
