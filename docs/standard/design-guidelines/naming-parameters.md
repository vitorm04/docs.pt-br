---
title: "Parâmetros de nomeação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a10fa8835bfbcf826f8a3bb9318966e0dc603864
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="naming-parameters"></a><span data-ttu-id="f6824-102">Parâmetros de nomeação</span><span class="sxs-lookup"><span data-stu-id="f6824-102">Naming Parameters</span></span>
<span data-ttu-id="f6824-103">Além do motivo óbvio de legibilidade, é importante seguir as diretrizes para nomes de parâmetro porque os parâmetros são exibidos na documentação e no designer quando as ferramentas de design visual fornecem Intellisense e a funcionalidade de navegação de classe.</span><span class="sxs-lookup"><span data-stu-id="f6824-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>  
  
 <span data-ttu-id="f6824-104">**FAZER ✓** use camelCasing em nomes de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f6824-104">**✓ DO** use camelCasing in parameter names.</span></span>  
  
 <span data-ttu-id="f6824-105">**FAZER ✓** usam nomes de parâmetro descritivo.</span><span class="sxs-lookup"><span data-stu-id="f6824-105">**✓ DO** use descriptive parameter names.</span></span>  
  
 <span data-ttu-id="f6824-106">**✓ CONSIDERE** usando nomes com base no significado do parâmetro em vez do tipo do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f6824-106">**✓ CONSIDER** using names based on a parameter’s meaning rather than the parameter’s type.</span></span>  
  
### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="f6824-107">Parâmetros de sobrecarga de operador de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="f6824-107">Naming Operator Overload Parameters</span></span>  
 <span data-ttu-id="f6824-108">**FAZER ✓** usar `left` e `right` para nomes de parâmetro de sobrecarga de operador binário se não houver nenhum significado para os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f6824-108">**✓ DO** use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="f6824-109">**FAZER ✓** usar `value` para unário operador sobrecarregar os nomes de parâmetro se não houver nenhum significado para os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f6824-109">**✓ DO** use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="f6824-110">**✓ CONSIDERE** nomes significativos para o operador de sobrecarga parâmetros se isso adiciona valor significativo.</span><span class="sxs-lookup"><span data-stu-id="f6824-110">**✓ CONSIDER** meaningful names for operator overload parameters if doing so adds significant value.</span></span>  
  
 <span data-ttu-id="f6824-111">**X não** use abreviações ou índices numéricos para o operador sobrecarregar os nomes de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f6824-111">**X DO NOT** use abbreviations or numeric indices for operator overload parameter names.</span></span>  
  
 <span data-ttu-id="f6824-112">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="f6824-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f6824-113">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="f6824-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6824-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6824-114">See Also</span></span>  
 [<span data-ttu-id="f6824-115">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="f6824-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="f6824-116">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="f6824-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
