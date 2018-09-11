---
title: Sobrecarga de membro
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2127497d294cbfd4e1bb24d033f432378627ff13
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353168"
---
# <a name="member-overloading"></a><span data-ttu-id="25294-102">Sobrecarga de membro</span><span class="sxs-lookup"><span data-stu-id="25294-102">Member Overloading</span></span>
<span data-ttu-id="25294-103">Sobrecarga de membro significa criar dois ou mais membros no mesmo tipo que diferem somente no número ou tipo de parâmetros, mas que têm o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="25294-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="25294-104">Por exemplo, em seguida, o `WriteLine` método está sobrecarregado:</span><span class="sxs-lookup"><span data-stu-id="25294-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 <span data-ttu-id="25294-105">Como apenas métodos, construtores e propriedades indexadas podem ter parâmetros, somente os membros podem ser sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="25294-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>  
  
 <span data-ttu-id="25294-106">Sobrecarga é uma das técnicas mais importantes para melhorar a usabilidade, a produtividade e facilitar a leitura de bibliotecas reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="25294-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="25294-107">Sobrecarregando o número de parâmetros torna possível fornecer versões mais simples dos construtores e métodos.</span><span class="sxs-lookup"><span data-stu-id="25294-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="25294-108">Sobrecarga no tipo de parâmetro torna possível usar o mesmo nome de membro para executar operações idêntico em um conjunto selecionado de diferentes tipos de membros.</span><span class="sxs-lookup"><span data-stu-id="25294-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>  
  
 <span data-ttu-id="25294-109">**✓ DO** tente usar nomes de parâmetro descritivo para indicar o padrão usado por sobrecargas mais curto.</span><span class="sxs-lookup"><span data-stu-id="25294-109">**✓ DO** try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>  
  
 <span data-ttu-id="25294-110">**X AVOID** arbitrariamente diversos nomes de parâmetro em sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="25294-110">**X AVOID** arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="25294-111">Se um parâmetro em uma sobrecarga representa a mesma entrada como um parâmetro em outra sobrecarga, os parâmetros devem ter o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="25294-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>  
  
 <span data-ttu-id="25294-112">**X AVOID** inconsistentes na ordem de parâmetros na sobrecarga membros.</span><span class="sxs-lookup"><span data-stu-id="25294-112">**X AVOID** being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="25294-113">Parâmetros com o mesmo nome deverá aparecer na mesma posição em todas as sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="25294-113">Parameters with the same name should appear in the same position in all overloads.</span></span>  
  
 <span data-ttu-id="25294-114">**✓ DO** fazer somente a maior sobrecarga virtual (se extensibilidade é necessária).</span><span class="sxs-lookup"><span data-stu-id="25294-114">**✓ DO** make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="25294-115">Sobrecargas mais curtas devem simplesmente chamar por meio de uma sobrecarga maior.</span><span class="sxs-lookup"><span data-stu-id="25294-115">Shorter overloads should simply call through to a longer overload.</span></span>  
  
 <span data-ttu-id="25294-116">**X DO NOT** usar `ref` ou `out` modificadores para sobrecarregar membros.</span><span class="sxs-lookup"><span data-stu-id="25294-116">**X DO NOT** use `ref` or `out` modifiers to overload members.</span></span>  
  
 <span data-ttu-id="25294-117">Alguns idiomas não podem resolver chamadas para sobrecargas assim.</span><span class="sxs-lookup"><span data-stu-id="25294-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="25294-118">Além disso, essas sobrecargas geralmente têm semânticas completamente diferentes e provavelmente não devem ser sobrecargas, mas dois métodos separados em vez disso.</span><span class="sxs-lookup"><span data-stu-id="25294-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>  
  
 <span data-ttu-id="25294-119">**X DO NOT** têm sobrecargas com parâmetros na mesma posição e tipos semelhantes, mas com semânticas diferentes.</span><span class="sxs-lookup"><span data-stu-id="25294-119">**X DO NOT** have overloads with parameters at the same position and similar types yet with different semantics.</span></span>  
  
 <span data-ttu-id="25294-120">**✓ DO** permitir `null` a serem passados para os argumentos opcionais.</span><span class="sxs-lookup"><span data-stu-id="25294-120">**✓ DO**  allow `null` to be passed for optional arguments.</span></span>  
  
 <span data-ttu-id="25294-121">**✓ DO** usar membro sobrecarga em vez de definir membros com argumentos padrão.</span><span class="sxs-lookup"><span data-stu-id="25294-121">**✓ DO** use member overloading rather than defining members with default arguments.</span></span>  
  
 <span data-ttu-id="25294-122">Argumentos padrão não estão em conformidade com CLS.</span><span class="sxs-lookup"><span data-stu-id="25294-122">Default arguments are not CLS compliant.</span></span>  
  
 <span data-ttu-id="25294-123">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="25294-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="25294-124">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="25294-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25294-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25294-125">See also</span></span>

- [<span data-ttu-id="25294-126">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="25294-126">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
- [<span data-ttu-id="25294-127">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="25294-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
