---
title: Membros protegidos
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4574dffc3f9dd1b60d655bfde33a4ddc1a81d350
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44068970"
---
# <a name="protected-members"></a><span data-ttu-id="e114d-102">Membros protegidos</span><span class="sxs-lookup"><span data-stu-id="e114d-102">Protected Members</span></span>
<span data-ttu-id="e114d-103">Membros protegidos por si só não fornecem todos extensibilidade, mas eles podem tornar mais poderosa extensibilidade por meio de subclasse.</span><span class="sxs-lookup"><span data-stu-id="e114d-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="e114d-104">Eles podem ser usados para expor as opções avançadas de personalização sem complicar desnecessariamente a principal interface pública.</span><span class="sxs-lookup"><span data-stu-id="e114d-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>  
  
 <span data-ttu-id="e114d-105">Designers do Framework precisam ter cuidado com membros protegidos porque o nome "protegido" pode fornecer uma falsa sensação de segurança.</span><span class="sxs-lookup"><span data-stu-id="e114d-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="e114d-106">Qualquer pessoa é capaz de subclasse de uma classe não lacrada e membros protegido de acesso e, então todos os mesmos defensivas práticas de codificação usadas para os membros públicos se aplicam a membros protegidos.</span><span class="sxs-lookup"><span data-stu-id="e114d-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>  
  
 <span data-ttu-id="e114d-107">**✓ CONSIDER** usando membros para a personalização avançada protegidos.</span><span class="sxs-lookup"><span data-stu-id="e114d-107">**✓ CONSIDER** using protected members for advanced customization.</span></span>  
  
 <span data-ttu-id="e114d-108">**✓ DO** tratar membros protegidos em classes não lacradas como public para fins de análise de segurança, documentação e compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="e114d-108">**✓ DO** treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>  
  
 <span data-ttu-id="e114d-109">Qualquer pessoa pode herdar de uma classe e acessar os membros protegidos.</span><span class="sxs-lookup"><span data-stu-id="e114d-109">Anyone can inherit from a class and access the protected members.</span></span>  
  
 <span data-ttu-id="e114d-110">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="e114d-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e114d-111">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="e114d-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e114d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e114d-112">See also</span></span>

- [<span data-ttu-id="e114d-113">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="e114d-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="e114d-114">Designer voltado para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="e114d-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
