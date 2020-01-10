---
title: Parâmetros de nomeação
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 0bb67056bb39b6a5f372191a1d0b0bb0dc1fe4d1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709173"
---
# <a name="naming-parameters"></a><span data-ttu-id="528b3-102">Parâmetros de nomeação</span><span class="sxs-lookup"><span data-stu-id="528b3-102">Naming Parameters</span></span>
<span data-ttu-id="528b3-103">Além do motivo óbvio da legibilidade, é importante seguir as diretrizes para nomes de parâmetro, pois os parâmetros são exibidos na documentação e no designer quando as ferramentas de Design Visual fornecem funcionalidade de navegação de classe e IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="528b3-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>  
  
 <span data-ttu-id="528b3-104">**✓ DO** use camelCasing em nomes de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="528b3-104">**✓ DO** use camelCasing in parameter names.</span></span>  
  
 <span data-ttu-id="528b3-105">**✓ DO** usam nomes de parâmetro descritivo.</span><span class="sxs-lookup"><span data-stu-id="528b3-105">**✓ DO** use descriptive parameter names.</span></span>  
  
 <span data-ttu-id="528b3-106">**✓ CONSIDER** usando nomes com base no significado do parâmetro em vez do tipo do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="528b3-106">**✓ CONSIDER** using names based on a parameter’s meaning rather than the parameter’s type.</span></span>  
  
### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="528b3-107">Parâmetros de sobrecarga de operador de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="528b3-107">Naming Operator Overload Parameters</span></span>  
 <span data-ttu-id="528b3-108">**✓ DO** usar `left` e `right` para nomes de parâmetro de sobrecarga de operador binário se não houver nenhum significado para os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="528b3-108">**✓ DO** use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="528b3-109">**✓ DO** usar `value` para unário operador sobrecarregar os nomes de parâmetro se não houver nenhum significado para os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="528b3-109">**✓ DO** use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="528b3-110">**✓ CONSIDER** nomes significativos para o operador de sobrecarga parâmetros se isso adiciona valor significativo.</span><span class="sxs-lookup"><span data-stu-id="528b3-110">**✓ CONSIDER** meaningful names for operator overload parameters if doing so adds significant value.</span></span>  
  
 <span data-ttu-id="528b3-111">**X DO NOT** use abreviações ou índices numéricos para o operador sobrecarregar os nomes de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="528b3-111">**X DO NOT** use abbreviations or numeric indices for operator overload parameter names.</span></span>  
  
 <span data-ttu-id="528b3-112">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="528b3-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="528b3-113">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="528b3-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="528b3-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="528b3-114">See also</span></span>

- [<span data-ttu-id="528b3-115">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="528b3-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="528b3-116">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="528b3-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
