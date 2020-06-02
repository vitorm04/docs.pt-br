---
title: Sobrecarga de membro
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: 6a2cd6d4dd293a7f4a408e1ee97a125c9454be41
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288999"
---
# <a name="member-overloading"></a><span data-ttu-id="cbd98-102">Sobrecarga de membro</span><span class="sxs-lookup"><span data-stu-id="cbd98-102">Member Overloading</span></span>
<span data-ttu-id="cbd98-103">Sobrecarga de membros significa criar dois ou mais membros no mesmo tipo que diferem apenas no número ou tipo de parâmetros, mas têm o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="cbd98-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="cbd98-104">Por exemplo, no seguinte, o `WriteLine` método está sobrecarregado:</span><span class="sxs-lookup"><span data-stu-id="cbd98-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>

```csharp
public static class Console {
    public void WriteLine();
    public void WriteLine(string value);
    public void WriteLine(bool value);
    ...
}
```

 <span data-ttu-id="cbd98-105">Como somente métodos, construtores e propriedades indexadas podem ter parâmetros, somente esses membros podem ser sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="cbd98-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>

 <span data-ttu-id="cbd98-106">A sobrecarga é uma das técnicas mais importantes para melhorar a usabilidade, a produtividade e a legibilidade de bibliotecas reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="cbd98-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="cbd98-107">O sobrecarregamento no número de parâmetros torna possível fornecer versões mais simples de construtores e métodos.</span><span class="sxs-lookup"><span data-stu-id="cbd98-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="cbd98-108">Sobrecarregar no tipo de parâmetro torna possível usar o mesmo nome de membro para membros que executam operações idênticas em um conjunto selecionado de tipos diferentes.</span><span class="sxs-lookup"><span data-stu-id="cbd98-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>

 <span data-ttu-id="cbd98-109">✔️ Tente usar nomes de parâmetro descritivos para indicar o padrão usado por sobrecargas menores.</span><span class="sxs-lookup"><span data-stu-id="cbd98-109">✔️ DO try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>

 <span data-ttu-id="cbd98-110">❌Evite nomes de parâmetros com variação arbitrária em sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="cbd98-110">❌ AVOID arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="cbd98-111">Se um parâmetro em uma sobrecarga representa a mesma entrada que um parâmetro em outra sobrecarga, os parâmetros deverão ter o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="cbd98-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>

 <span data-ttu-id="cbd98-112">❌Evite ser inconsistente na ordenação de parâmetros em Membros sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="cbd98-112">❌ AVOID being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="cbd98-113">Os parâmetros com o mesmo nome devem aparecer na mesma posição em todas as sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="cbd98-113">Parameters with the same name should appear in the same position in all overloads.</span></span>

 <span data-ttu-id="cbd98-114">✔️ fazer apenas a sobrecarga virtual mais longa (se a extensibilidade for necessária).</span><span class="sxs-lookup"><span data-stu-id="cbd98-114">✔️ DO make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="cbd98-115">Sobrecargas menores devem simplesmente chamar para uma sobrecarga mais longa.</span><span class="sxs-lookup"><span data-stu-id="cbd98-115">Shorter overloads should simply call through to a longer overload.</span></span>

 <span data-ttu-id="cbd98-116">❌Não use `ref` `out` modificadores ou para sobrecarregar Membros.</span><span class="sxs-lookup"><span data-stu-id="cbd98-116">❌ DO NOT use `ref` or `out` modifiers to overload members.</span></span>

 <span data-ttu-id="cbd98-117">Alguns idiomas não podem resolver chamadas para sobrecargas como esta.</span><span class="sxs-lookup"><span data-stu-id="cbd98-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="cbd98-118">Além disso, essas sobrecargas geralmente têm semânticas completamente diferentes e, provavelmente, não devem ser sobrecarregadas, mas dois métodos separados.</span><span class="sxs-lookup"><span data-stu-id="cbd98-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>

 <span data-ttu-id="cbd98-119">❌Não têm sobrecargas com parâmetros na mesma posição e tipos semelhantes, ainda com semânticas diferentes.</span><span class="sxs-lookup"><span data-stu-id="cbd98-119">❌ DO NOT have overloads with parameters at the same position and similar types yet with different semantics.</span></span>

 <span data-ttu-id="cbd98-120">✔️ permitir que `null` sejam passados para argumentos opcionais.</span><span class="sxs-lookup"><span data-stu-id="cbd98-120">✔️ DO  allow `null` to be passed for optional arguments.</span></span>

 <span data-ttu-id="cbd98-121">✔️ usar a sobrecarga de membros em vez de definir membros com argumentos padrão.</span><span class="sxs-lookup"><span data-stu-id="cbd98-121">✔️ DO use member overloading rather than defining members with default arguments.</span></span>

 <span data-ttu-id="cbd98-122">Os argumentos padrão não são compatíveis com CLS.</span><span class="sxs-lookup"><span data-stu-id="cbd98-122">Default arguments are not CLS compliant.</span></span>

 <span data-ttu-id="cbd98-123">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="cbd98-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="cbd98-124">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="cbd98-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="cbd98-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="cbd98-125">See also</span></span>

- [<span data-ttu-id="cbd98-126">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="cbd98-126">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="cbd98-127">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="cbd98-127">Framework Design Guidelines</span></span>](index.md)
