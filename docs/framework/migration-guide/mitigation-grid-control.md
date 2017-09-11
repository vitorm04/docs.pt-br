---
title: "Mitigação: alocação de espaço do controle de grade para colunas de estrela"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- Grid control retargeting changes
ms.assetid: 707c064d-85e9-4ea1-aefb-e42b60b88679
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 54391538ac0b2daf307cba2f7ceff1984d26b0ce
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-grid-control39s-space-allocation-to-star-columns"></a><span data-ttu-id="457f3-102">Mitigação: alocação de espaço do controle de grade para colunas de estrela</span><span class="sxs-lookup"><span data-stu-id="457f3-102">Mitigation: Grid Control&#39;s Space Allocation to Star-columns</span></span>

<span data-ttu-id="457f3-103">A partir dos aplicativos destinados ao .NET Framework 4.7, o WPF substitui o algoritmo usado pelo controle <xref:System.Windows.Controls.Grid> para alocar espaço para colunas de \*.</span><span class="sxs-lookup"><span data-stu-id="457f3-103">Starting with applications that the .NET Framework 4.7, WPF replaces the algorithm that the <xref:System.Windows.Controls.Grid> control uses to allocate space to \*-columns.</span></span> 

## <a name="whats-changed"></a><span data-ttu-id="457f3-104">O que mudou</span><span class="sxs-lookup"><span data-stu-id="457f3-104">What's changed</span></span>

<span data-ttu-id="457f3-105">O novo algoritmo corrige vários bugs presentes no algoritmo antigo:</span><span class="sxs-lookup"><span data-stu-id="457f3-105">The new algorithm fixes several bugs present in the old algorithm:</span></span>

1. <span data-ttu-id="457f3-106">A alocação total de colunas pode exceder a largura da grade.</span><span class="sxs-lookup"><span data-stu-id="457f3-106">Total allocation to columns can exceed the Grid's width.</span></span> <span data-ttu-id="457f3-107">Isso pode ocorrer ao alocar espaço para uma coluna cujo compartilhamento proporcional seja menor que seu tamanho mínimo.</span><span class="sxs-lookup"><span data-stu-id="457f3-107">This can occur when allocating space to a column whose proportional share is less than its minimum size.</span></span> <span data-ttu-id="457f3-108">O algoritmo aloca o tamanho mínimo, o que reduz o espaço disponível para outras colunas.</span><span class="sxs-lookup"><span data-stu-id="457f3-108">The algorithm allocates the minimum size, which decreases the space available to other columns.</span></span> <span data-ttu-id="457f3-109">Se não houver nenhuma coluna de \* restante para alocar, a alocação total será muito grande.</span><span class="sxs-lookup"><span data-stu-id="457f3-109">If there are no \*-columns left to allocate, the total allocation will be too large.</span></span>

1. <span data-ttu-id="457f3-110">A alocação total pode ser menor que a largura da grade.</span><span class="sxs-lookup"><span data-stu-id="457f3-110">Total allocation can fall short of the Grid's width.</span></span> <span data-ttu-id="457f3-111">Esse é o problema duplo do n° 1, que surge ao alocar para uma coluna cujo compartilhamento proporcional é maior do que seu tamanho máximo, sem nenhuma coluna de \* restante para concluir o processo.</span><span class="sxs-lookup"><span data-stu-id="457f3-111">This is the dual problem to #1, arising when allocating to a column whose proportional share is greater than its maximum size, with no \*-columns left to take up the slack.</span></span>

1. <span data-ttu-id="457f3-112">Duas colunas de \* podem receber alocações que não sejam proporcionais a seus pesos.</span><span class="sxs-lookup"><span data-stu-id="457f3-112">Two \*-columns can receive allocations not proportional to their -weights.</span></span> <span data-ttu-id="457f3-113">Esta é uma versão atenuada da n° 1 e da n° 2, que surge ao alocar para colunas de * A, B e C (nessa ordem), quando o compartilhamento proporcional de B viola sua restrição mínima (ou máxima).</span><span class="sxs-lookup"><span data-stu-id="457f3-113">This is a milder version of #1/#2, arising when allocating to *-columns A, B, and C (in that order), where B's proportional share violates its min (or max) constraint.</span></span> <span data-ttu-id="457f3-114">Como acima, isso altera o espaço disponível para a coluna C, que obtém menos (ou mais) alocação proporcional do que A.</span><span class="sxs-lookup"><span data-stu-id="457f3-114">As above, this changes the space available to column C, who gets less (or more) proportional allocation than A did,</span></span>

1. <span data-ttu-id="457f3-115">As colunas com pesos muito grandes (> 10^298) são tratadas como se tivessem o peso 10^298.</span><span class="sxs-lookup"><span data-stu-id="457f3-115">Columns with extremely large weights (> 10^298) are all treated as if they had weight 10^298.</span></span> <span data-ttu-id="457f3-116">Não são consideradas as diferenças proporcionais entre elas (e entre colunas com pesos um pouco menores).</span><span class="sxs-lookup"><span data-stu-id="457f3-116">Proportional differences between them (and between columns with slightly smaller weights) are not honored.</span></span>

1. <span data-ttu-id="457f3-117">As colunas com pesos infinitos não são tratadas corretamente.</span><span class="sxs-lookup"><span data-stu-id="457f3-117">Columns with infinite weights are not handled correctly.</span></span> <span data-ttu-id="457f3-118">(Na verdade, você não pode definir um peso para infinito, mas essa é uma restrição artificial.</span><span class="sxs-lookup"><span data-stu-id="457f3-118">[Actually you can't set a weight to Infinity, but this is an artificial restriction.</span></span> <span data-ttu-id="457f3-119">O código de alocação tentou lidar com isso, mas não teve muito sucesso.)</span><span class="sxs-lookup"><span data-stu-id="457f3-119">The allocation code was trying to handle it, but doing a bad job.]</span></span>

1. <span data-ttu-id="457f3-120">Vários problemas menores, evitando estouro, estouro negativo, perda de precisão e problemas de ponto flutuante semelhantes.</span><span class="sxs-lookup"><span data-stu-id="457f3-120">Several minor problems while avoiding overflow, underflow, loss of precision and similar floating-point issues.</span></span>

1. <span data-ttu-id="457f3-121">Os ajustes de arredondamento de layout são incorretos em um DPI suficientemente alto.</span><span class="sxs-lookup"><span data-stu-id="457f3-121">Adjustments for layout rounding are incorrect at sufficiently high DPI.</span></span>

<span data-ttu-id="457f3-122">O novo algoritmo produz resultados que atendam aos seguintes critérios:</span><span class="sxs-lookup"><span data-stu-id="457f3-122">The new algorithm produces results that meet the following criteria:</span></span>

<span data-ttu-id="457f3-123">R.</span><span class="sxs-lookup"><span data-stu-id="457f3-123">A.</span></span> <span data-ttu-id="457f3-124">A largura real atribuída a uma coluna de * nunca é menor que sua largura mínima nem maior que sua largura máxima.</span><span class="sxs-lookup"><span data-stu-id="457f3-124">The actual width assigned to a *-column is never less than its minimum width nor greater than its maximum width.</span></span>

<span data-ttu-id="457f3-125">B.</span><span class="sxs-lookup"><span data-stu-id="457f3-125">B.</span></span> <span data-ttu-id="457f3-126">Cada coluna que não tem uma largura mínima ou máxima atribuída, tem uma largura proporcional ao seu peso atribuída.</span><span class="sxs-lookup"><span data-stu-id="457f3-126">Each -column that is not assigned its minimum or maximum width is assigned a width proportional to its -weight.</span></span> <span data-ttu-id="457f3-127">Para ser preciso, se duas colunas são declaradas com largura x e y, respectivamente, e se nenhuma coluna recebe sua largura mínima ou máxima, as larguras reais v e w atribuídas às colunas ficam na mesma proporção: v / w == x / y.</span><span class="sxs-lookup"><span data-stu-id="457f3-127">To be precise, if two columns are declared with width x and y respectively, and if neither column receives its minimum or maximum width, the actual widths v and w assigned to the columns are in the same proportion: v / w == x / y.</span></span>

<span data-ttu-id="457f3-128">C.</span><span class="sxs-lookup"><span data-stu-id="457f3-128">C.</span></span> <span data-ttu-id="457f3-129">A largura total alocada para colunas de \* "proporcionais" é igual ao espaço disponível depois de alocar para as colunas restritas (colunas fixas, automáticas e de \* que têm a largura mínima ou máxima alocada).</span><span class="sxs-lookup"><span data-stu-id="457f3-129">The total width allocated to "proportional" \*-columns is equal to the space available after allocating to the constrained columns (fixed, auto, and \*-columns that are allocated their min or max width).</span></span> <span data-ttu-id="457f3-130">Isso pode ser zero, por exemplo se a soma das larguras mínimas excede a largura disponível da grade.</span><span class="sxs-lookup"><span data-stu-id="457f3-130">This might be zero, for instance if the sum of the minimum widths exceeds the Grid's availbable width.</span></span>

<span data-ttu-id="457f3-131">D.</span><span class="sxs-lookup"><span data-stu-id="457f3-131">D.</span></span> <span data-ttu-id="457f3-132">Todas essas instruções devem ser interpretadas em relação ao layout "ideal".</span><span class="sxs-lookup"><span data-stu-id="457f3-132">All these statements are to be interpreted with respect to the "ideal" layout.</span></span> <span data-ttu-id="457f3-133">Quando o arredondamento de layout está em vigor, as larguras reais podem diferir das larguras ideais em até um pixel.</span><span class="sxs-lookup"><span data-stu-id="457f3-133">When layout rounding is in effect, the actual widths can differ from the ideal widths by as much as one pixel.</span></span>

<span data-ttu-id="457f3-134">O algoritmo antigo respeitou (A), mas não respeitou os outros critérios nos casos descritos acima.</span><span class="sxs-lookup"><span data-stu-id="457f3-134">The old algorithm honored (A) but failed to honor the other criteria in the cases outlined above.</span></span>

<span data-ttu-id="457f3-135">Tudo que foi dito sobre colunas e larguras neste tópico se aplica também a linhas e alturas.</span><span class="sxs-lookup"><span data-stu-id="457f3-135">Everything said about columns and widths in this topic applies as well to rows and heights.</span></span>

## <a name="impact"></a><span data-ttu-id="457f3-136">Impacto</span><span class="sxs-lookup"><span data-stu-id="457f3-136">Impact</span></span>

<span data-ttu-id="457f3-137">O novo algoritmo altera a largura real atribuída a colunas \* em diversos casos:</span><span class="sxs-lookup"><span data-stu-id="457f3-137">The new algorithm changes the actual width assigned to \*-columns in a number of cases:</span></span>

- <span data-ttu-id="457f3-138">Quando uma ou mais colunas de \* também têm uma largura mínima ou máxima que substitui a alocação proporcional para aquela coluna.</span><span class="sxs-lookup"><span data-stu-id="457f3-138">When one or more \*-columns also have a minimum or maximum width that overrides the proportional allocation for that column.</span></span> <span data-ttu-id="457f3-139">(A largura mínima pode ser derivada de uma declaração <xref:System.Windows.FrameworkElement.MinWidth%2A> explícita ou de um mínimo implícito obtido do conteúdo da coluna.</span><span class="sxs-lookup"><span data-stu-id="457f3-139">(The minimum width can derive from an explicit <xref:System.Windows.FrameworkElement.MinWidth%2A> declaration, or from an implicit minimum obtained from the column's content.</span></span> <span data-ttu-id="457f3-140">A largura máxima só pode ser definida explicitamente de uma declaração <xref:System.Windows.FrameworkElement.MaxWidth%2A>.)</span><span class="sxs-lookup"><span data-stu-id="457f3-140">The maximum width can only be defined explicitly, from a <xref:System.Windows.FrameworkElement.MaxWidth%2A> declaration.)</span></span>

- <span data-ttu-id="457f3-141">Quando uma ou mais colunas de \* declaram um peso de \* extremamente grande, maior que 10^298.</span><span class="sxs-lookup"><span data-stu-id="457f3-141">When one or more \*-columns declare an extremely large \*-weight, greater than 10^298.</span></span>

- <span data-ttu-id="457f3-142">Quando os pesos de \* são diferentes o suficiente para encontrar instabilidade de ponto flutuante (estouro, estouro negativo, perda de precisão).</span><span class="sxs-lookup"><span data-stu-id="457f3-142">When the \*-weights are sufficiently different to encounter floating-point instability (overflow, underflow, loss of precision).</span></span>

- <span data-ttu-id="457f3-143">Quando o arredondamento de layout está habilitado e o DPI de exibição efetivo é suficientemente alto.</span><span class="sxs-lookup"><span data-stu-id="457f3-143">When layout rounding is enabled, and the effective display DPI is sufficiently high.</span></span>

<span data-ttu-id="457f3-144">Nos dois primeiros casos, as larguras produzidas pelo novo algoritmo podem ser significativamente diferentes das produzidas pelo algoritmo antigo. No último caso, a diferença será no máximo um ou dois pixels.</span><span class="sxs-lookup"><span data-stu-id="457f3-144">In the first two cases, the widths produced by the new algorithm can be significantly different from those produced by the old algorithm; in the last case, the difference will be at most one or two pixels.</span></span>

## <a name="mitigation"></a><span data-ttu-id="457f3-145">Redução</span><span class="sxs-lookup"><span data-stu-id="457f3-145">Mitigation</span></span>

<span data-ttu-id="457f3-146">Por padrão, os aplicativos destinados a versões do .NET Framework a partir do .NET Framework 4.7 usarão o novo algoritmo, enquanto os aplicativos destinados ao .NET Framework 4.6.2 ou a versões anteriores usarão o algoritmo antigo.</span><span class="sxs-lookup"><span data-stu-id="457f3-146">By default, apps that target versions of the .NET Framework starting with the .NET Framework 4.7 will use the new algorithm, while apps that target the .NET Framework 4.6.2 or earlier versions will use the old algorithm.</span></span>

<span data-ttu-id="457f3-147">Para substituir o padrão, use a seguinte definição de configuração:</span><span class="sxs-lookup"><span data-stu-id="457f3-147">To override the default, use the following configuration setting:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true" /> 
</runtime>
```

<span data-ttu-id="457f3-148">O valor 'true' seleciona o algoritmo antigo e 'false' seleciona o novo algoritmo.</span><span class="sxs-lookup"><span data-stu-id="457f3-148">The value 'true' selects the old algorithm, and 'false' selects the new algorithm.</span></span>

## <a name="see-also"></a><span data-ttu-id="457f3-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="457f3-149">See also</span></span>
[<span data-ttu-id="457f3-150">Alterações de redirecionamento no .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="457f3-150">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

