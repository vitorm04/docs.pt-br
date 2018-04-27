---
title: Sobrecarga de membro
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 546db0540cf7852b40678476f732663369b15824
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="member-overloading"></a><span data-ttu-id="d1050-102">Sobrecarga de membro</span><span class="sxs-lookup"><span data-stu-id="d1050-102">Member Overloading</span></span>
<span data-ttu-id="d1050-103">Membro sobrecarga significa criar dois ou mais membros do mesmo tipo que diferem apenas o número ou tipo de parâmetros, mas que têm o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="d1050-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="d1050-104">Por exemplo, em seguida, o `WriteLine` método está sobrecarregado:</span><span class="sxs-lookup"><span data-stu-id="d1050-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 <span data-ttu-id="d1050-105">Como somente métodos, construtores e propriedades indexadas podem ter parâmetros, somente os membros podem ser sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="d1050-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>  
  
 <span data-ttu-id="d1050-106">Sobrecarga é uma das técnicas mais importantes para melhorar a legibilidade de bibliotecas reutilizáveis, produtividade e usabilidade.</span><span class="sxs-lookup"><span data-stu-id="d1050-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="d1050-107">Sobrecarga no número de parâmetros torna possível fornecer versões mais simples de construtores e métodos.</span><span class="sxs-lookup"><span data-stu-id="d1050-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="d1050-108">Sobrecarga no tipo de parâmetro torna possível usar o mesmo nome de membro para executar operações idênticas em um conjunto selecionado de tipos diferentes de membros.</span><span class="sxs-lookup"><span data-stu-id="d1050-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>  
  
 <span data-ttu-id="d1050-109">**FAZER ✓** tente usar nomes de parâmetro descritivo para indicar o padrão usado por sobrecargas mais curto.</span><span class="sxs-lookup"><span data-stu-id="d1050-109">**✓ DO** try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>  
  
 <span data-ttu-id="d1050-110">**X Evite** arbitrariamente diversos nomes de parâmetro em sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="d1050-110">**X AVOID** arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="d1050-111">Se um parâmetro em uma sobrecarga representa a mesma entrada como um parâmetro em outra sobrecarga, os parâmetros devem ter o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="d1050-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>  
  
 <span data-ttu-id="d1050-112">**X Evite** inconsistentes na ordem de parâmetros na sobrecarga membros.</span><span class="sxs-lookup"><span data-stu-id="d1050-112">**X AVOID** being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="d1050-113">Parâmetros com o mesmo nome devem aparecer na mesma posição em todas as sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="d1050-113">Parameters with the same name should appear in the same position in all overloads.</span></span>  
  
 <span data-ttu-id="d1050-114">**FAZER ✓** fazer somente a maior sobrecarga virtual (se extensibilidade é necessária).</span><span class="sxs-lookup"><span data-stu-id="d1050-114">**✓ DO** make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="d1050-115">Sobrecargas menores devem simplesmente chamar por meio de uma sobrecarga maior.</span><span class="sxs-lookup"><span data-stu-id="d1050-115">Shorter overloads should simply call through to a longer overload.</span></span>  
  
 <span data-ttu-id="d1050-116">**X não** usar `ref` ou `out` modificadores para sobrecarregar membros.</span><span class="sxs-lookup"><span data-stu-id="d1050-116">**X DO NOT** use `ref` or `out` modifiers to overload members.</span></span>  
  
 <span data-ttu-id="d1050-117">Alguns idiomas não é possível resolver chamadas para sobrecargas assim.</span><span class="sxs-lookup"><span data-stu-id="d1050-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="d1050-118">Além disso, essas sobrecargas geralmente tem semântica completamente diferente e provavelmente não devem ser sobrecargas mas dois métodos separados em vez disso.</span><span class="sxs-lookup"><span data-stu-id="d1050-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>  
  
 <span data-ttu-id="d1050-119">**X não** têm sobrecargas com parâmetros na mesma posição e tipos semelhantes, mas com semânticas diferentes.</span><span class="sxs-lookup"><span data-stu-id="d1050-119">**X DO NOT** have overloads with parameters at the same position and similar types yet with different semantics.</span></span>  
  
 <span data-ttu-id="d1050-120">**FAZER ✓** permitir `null` a serem passados para os argumentos opcionais.</span><span class="sxs-lookup"><span data-stu-id="d1050-120">**✓ DO**  allow `null` to be passed for optional arguments.</span></span>  
  
 <span data-ttu-id="d1050-121">**FAZER ✓** usar membro sobrecarga em vez de definir membros com argumentos padrão.</span><span class="sxs-lookup"><span data-stu-id="d1050-121">**✓ DO** use member overloading rather than defining members with default arguments.</span></span>  
  
 <span data-ttu-id="d1050-122">Argumentos padrão não são compatível com CLS.</span><span class="sxs-lookup"><span data-stu-id="d1050-122">Default arguments are not CLS compliant.</span></span>  
  
 <span data-ttu-id="d1050-123">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="d1050-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d1050-124">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="d1050-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1050-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1050-125">See Also</span></span>  
 [<span data-ttu-id="d1050-126">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="d1050-126">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="d1050-127">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="d1050-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
