---
title: Parâmetros de nomeação
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
author: KrzysztofCwalina
ms.openlocfilehash: 0e5b33839372e303b96bd6b84949f9a82da2f689
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026296"
---
# <a name="naming-parameters"></a><span data-ttu-id="c519f-102">Parâmetros de nomeação</span><span class="sxs-lookup"><span data-stu-id="c519f-102">Naming Parameters</span></span>
<span data-ttu-id="c519f-103">Além do motivo óbvio de legibilidade, é importante seguir as diretrizes para nomes de parâmetro porque os parâmetros são exibidos na documentação e no designer quando ferramentas de design visual fornecem Intellisense e a funcionalidade de navegação de classe.</span><span class="sxs-lookup"><span data-stu-id="c519f-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>  
  
 <span data-ttu-id="c519f-104">**✓ DO** use camelCasing em nomes de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c519f-104">**✓ DO** use camelCasing in parameter names.</span></span>  
  
 <span data-ttu-id="c519f-105">**✓ DO** usam nomes de parâmetro descritivo.</span><span class="sxs-lookup"><span data-stu-id="c519f-105">**✓ DO** use descriptive parameter names.</span></span>  
  
 <span data-ttu-id="c519f-106">**✓ CONSIDER** usando nomes com base no significado do parâmetro em vez do tipo do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c519f-106">**✓ CONSIDER** using names based on a parameter’s meaning rather than the parameter’s type.</span></span>  
  
### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="c519f-107">Parâmetros de sobrecarga de operador de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="c519f-107">Naming Operator Overload Parameters</span></span>  
 <span data-ttu-id="c519f-108">**✓ DO** usar `left` e `right` para nomes de parâmetro de sobrecarga de operador binário se não houver nenhum significado para os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c519f-108">**✓ DO** use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="c519f-109">**✓ DO** usar `value` para unário operador sobrecarregar os nomes de parâmetro se não houver nenhum significado para os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c519f-109">**✓ DO** use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="c519f-110">**✓ CONSIDER** nomes significativos para o operador de sobrecarga parâmetros se isso adiciona valor significativo.</span><span class="sxs-lookup"><span data-stu-id="c519f-110">**✓ CONSIDER** meaningful names for operator overload parameters if doing so adds significant value.</span></span>  
  
 <span data-ttu-id="c519f-111">**X DO NOT** use abreviações ou índices numéricos para o operador sobrecarregar os nomes de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c519f-111">**X DO NOT** use abbreviations or numeric indices for operator overload parameter names.</span></span>  
  
 <span data-ttu-id="c519f-112">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="c519f-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c519f-113">*Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="c519f-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c519f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c519f-114">See also</span></span>

- [<span data-ttu-id="c519f-115">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="c519f-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="c519f-116">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="c519f-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
