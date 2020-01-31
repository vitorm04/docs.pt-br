---
title: Membros protegidos
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: 44d342662e1aaeb51f14470f354f2dadd9a6f18d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743649"
---
# <a name="protected-members"></a><span data-ttu-id="dfd92-102">Membros protegidos</span><span class="sxs-lookup"><span data-stu-id="dfd92-102">Protected Members</span></span>
<span data-ttu-id="dfd92-103">Os membros protegidos por si só não fornecem nenhuma extensibilidade, mas podem tornar a extensibilidade por meio de subclasses mais poderosas.</span><span class="sxs-lookup"><span data-stu-id="dfd92-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="dfd92-104">Eles podem ser usados para expor opções de personalização avançadas sem desnecessariamente complicar a interface pública principal.</span><span class="sxs-lookup"><span data-stu-id="dfd92-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>

 <span data-ttu-id="dfd92-105">Os designers de estrutura precisam ter cuidado com membros protegidos porque o nome "protegido" pode dar um falso aspecto de segurança.</span><span class="sxs-lookup"><span data-stu-id="dfd92-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="dfd92-106">Qualquer pessoa pode fazer uma subclasse de uma classe sem lacre e acessar membros protegidos e, portanto, todas as mesmas práticas de codificação defensivas usadas para membros públicos se aplicam a membros protegidos.</span><span class="sxs-lookup"><span data-stu-id="dfd92-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>

 <span data-ttu-id="dfd92-107">✔️ Considere o uso de membros protegidos para personalização avançada.</span><span class="sxs-lookup"><span data-stu-id="dfd92-107">✔️ CONSIDER using protected members for advanced customization.</span></span>

 <span data-ttu-id="dfd92-108">✔️ tratar membros protegidos em classes sem lacre como públicas para fins de segurança, documentação e análise de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="dfd92-108">✔️ DO treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>

 <span data-ttu-id="dfd92-109">Qualquer pessoa pode herdar de uma classe e acessar os membros protegidos.</span><span class="sxs-lookup"><span data-stu-id="dfd92-109">Anyone can inherit from a class and access the protected members.</span></span>

 <span data-ttu-id="dfd92-110">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="dfd92-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="dfd92-111">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="dfd92-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="dfd92-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="dfd92-112">See also</span></span>

- [<span data-ttu-id="dfd92-113">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="dfd92-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="dfd92-114">Designer voltado para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="dfd92-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
