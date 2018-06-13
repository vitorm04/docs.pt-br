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
ms.openlocfilehash: 5d4d334d9809f374442e19807d3b249a17a1d9df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571070"
---
# <a name="protected-members"></a><span data-ttu-id="2a992-102">Membros protegidos</span><span class="sxs-lookup"><span data-stu-id="2a992-102">Protected Members</span></span>
<span data-ttu-id="2a992-103">Membros protegidos por si só não fornecem nenhuma extensibilidade, mas eles podem tornar a extensibilidade por meio de subclassificação mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="2a992-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="2a992-104">Eles podem ser usados para expor as opções avançadas de personalização sem desnecessariamente complicar a principal interface pública.</span><span class="sxs-lookup"><span data-stu-id="2a992-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>  
  
 <span data-ttu-id="2a992-105">Designers de Framework precisam ter cuidado com membros protegidos, porque o nome "protegido" pode dar uma falsa sensação de segurança.</span><span class="sxs-lookup"><span data-stu-id="2a992-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="2a992-106">Qualquer pessoa que é capaz de subclasse de uma classe não lacrada e membros de acesso protegido e então as mesmas as práticas de codificação usadas para membros públicos se aplica a membros protegidos.</span><span class="sxs-lookup"><span data-stu-id="2a992-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>  
  
 <span data-ttu-id="2a992-107">**✓ CONSIDERE** usando membros para a personalização avançada protegidos.</span><span class="sxs-lookup"><span data-stu-id="2a992-107">**✓ CONSIDER** using protected members for advanced customization.</span></span>  
  
 <span data-ttu-id="2a992-108">**FAZER ✓** tratar membros protegidos em classes não lacradas como public para fins de análise de segurança, documentação e compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="2a992-108">**✓ DO** treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>  
  
 <span data-ttu-id="2a992-109">Qualquer pessoa pode herdar de uma classe e acessar os membros protegidos.</span><span class="sxs-lookup"><span data-stu-id="2a992-109">Anyone can inherit from a class and access the protected members.</span></span>  
  
 <span data-ttu-id="2a992-110">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="2a992-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="2a992-111">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="2a992-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a992-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a992-112">See Also</span></span>  
 [<span data-ttu-id="2a992-113">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="2a992-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="2a992-114">Designer voltado para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="2a992-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
