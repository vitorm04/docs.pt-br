---
title: Parâmetros de nomeação
description: Aprenda as diretrizes para a nomenclatura de parâmetros. Por exemplo, use nomes de parâmetros descritivos & o camel case, & considere a nomenclatura com base no significado, em vez do tipo.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 54f37c4d6a0f9a6931fa69d612bf0e45bf1f2ce7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583512"
---
# <a name="naming-parameters"></a><span data-ttu-id="1c91e-104">Parâmetros de nomeação</span><span class="sxs-lookup"><span data-stu-id="1c91e-104">Naming Parameters</span></span>
<span data-ttu-id="1c91e-105">Além do motivo óbvio da legibilidade, é importante seguir as diretrizes para nomes de parâmetro, pois os parâmetros são exibidos na documentação e no designer quando as ferramentas de Design Visual fornecem funcionalidade de navegação de classe e IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="1c91e-105">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>

 <span data-ttu-id="1c91e-106">✔️ usar camelCasing em nomes de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1c91e-106">✔️ DO use camelCasing in parameter names.</span></span>

 <span data-ttu-id="1c91e-107">✔️ usar nomes de parâmetro descritivos.</span><span class="sxs-lookup"><span data-stu-id="1c91e-107">✔️ DO use descriptive parameter names.</span></span>

 <span data-ttu-id="1c91e-108">✔️ CONSIDERAR o uso de nomes com base no significado de um parâmetro em vez do tipo do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1c91e-108">✔️ CONSIDER using names based on a parameter’s meaning rather than the parameter’s type.</span></span>

### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="1c91e-109">Parâmetros de sobrecarga de operador de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="1c91e-109">Naming Operator Overload Parameters</span></span>
 <span data-ttu-id="1c91e-110">✔️ usar `left` e `right` para nomes de parâmetros de sobrecarga de operador binário se não houver significado para os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1c91e-110">✔️ DO use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="1c91e-111">✔️ usar `value` para nomes de parâmetro de sobrecarga de operador unário se não houver significado para os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1c91e-111">✔️ DO use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="1c91e-112">✔️ CONSIDERAR nomes significativos para parâmetros de sobrecarga de operador se isso adicionar um valor significativo.</span><span class="sxs-lookup"><span data-stu-id="1c91e-112">✔️ CONSIDER meaningful names for operator overload parameters if doing so adds significant value.</span></span>

 <span data-ttu-id="1c91e-113">❌Não use abreviações ou índices numéricos para nomes de parâmetro de sobrecarga de operador.</span><span class="sxs-lookup"><span data-stu-id="1c91e-113">❌ DO NOT use abbreviations or numeric indices for operator overload parameter names.</span></span>

 <span data-ttu-id="1c91e-114">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="1c91e-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="1c91e-115">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="1c91e-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="1c91e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c91e-116">See also</span></span>

- [<span data-ttu-id="1c91e-117">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="1c91e-117">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="1c91e-118">Diretrizes de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="1c91e-118">Naming Guidelines</span></span>](naming-guidelines.md)
