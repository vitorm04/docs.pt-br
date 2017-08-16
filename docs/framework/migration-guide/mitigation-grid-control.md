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
# <a name="mitigation-grid-control39s-space-allocation-to-star-columns"></a>Mitigação: alocação de espaço do controle de grade para colunas de estrela

A partir dos aplicativos destinados ao .NET Framework 4.7, o WPF substitui o algoritmo usado pelo controle <xref:System.Windows.Controls.Grid> para alocar espaço para colunas de \*. 

## <a name="whats-changed"></a>O que mudou

O novo algoritmo corrige vários bugs presentes no algoritmo antigo:

1. A alocação total de colunas pode exceder a largura da grade. Isso pode ocorrer ao alocar espaço para uma coluna cujo compartilhamento proporcional seja menor que seu tamanho mínimo. O algoritmo aloca o tamanho mínimo, o que reduz o espaço disponível para outras colunas. Se não houver nenhuma coluna de \* restante para alocar, a alocação total será muito grande.

1. A alocação total pode ser menor que a largura da grade. Esse é o problema duplo do n° 1, que surge ao alocar para uma coluna cujo compartilhamento proporcional é maior do que seu tamanho máximo, sem nenhuma coluna de \* restante para concluir o processo.

1. Duas colunas de \* podem receber alocações que não sejam proporcionais a seus pesos. Esta é uma versão atenuada da n° 1 e da n° 2, que surge ao alocar para colunas de * A, B e C (nessa ordem), quando o compartilhamento proporcional de B viola sua restrição mínima (ou máxima). Como acima, isso altera o espaço disponível para a coluna C, que obtém menos (ou mais) alocação proporcional do que A.

1. As colunas com pesos muito grandes (> 10^298) são tratadas como se tivessem o peso 10^298. Não são consideradas as diferenças proporcionais entre elas (e entre colunas com pesos um pouco menores).

1. As colunas com pesos infinitos não são tratadas corretamente. (Na verdade, você não pode definir um peso para infinito, mas essa é uma restrição artificial. O código de alocação tentou lidar com isso, mas não teve muito sucesso.)

1. Vários problemas menores, evitando estouro, estouro negativo, perda de precisão e problemas de ponto flutuante semelhantes.

1. Os ajustes de arredondamento de layout são incorretos em um DPI suficientemente alto.

O novo algoritmo produz resultados que atendam aos seguintes critérios:

R. A largura real atribuída a uma coluna de * nunca é menor que sua largura mínima nem maior que sua largura máxima.

B. Cada coluna que não tem uma largura mínima ou máxima atribuída, tem uma largura proporcional ao seu peso atribuída. Para ser preciso, se duas colunas são declaradas com largura x e y, respectivamente, e se nenhuma coluna recebe sua largura mínima ou máxima, as larguras reais v e w atribuídas às colunas ficam na mesma proporção: v / w == x / y.

C. A largura total alocada para colunas de \* "proporcionais" é igual ao espaço disponível depois de alocar para as colunas restritas (colunas fixas, automáticas e de \* que têm a largura mínima ou máxima alocada). Isso pode ser zero, por exemplo se a soma das larguras mínimas excede a largura disponível da grade.

D. Todas essas instruções devem ser interpretadas em relação ao layout "ideal". Quando o arredondamento de layout está em vigor, as larguras reais podem diferir das larguras ideais em até um pixel.

O algoritmo antigo respeitou (A), mas não respeitou os outros critérios nos casos descritos acima.

Tudo que foi dito sobre colunas e larguras neste tópico se aplica também a linhas e alturas.

## <a name="impact"></a>Impacto

O novo algoritmo altera a largura real atribuída a colunas \* em diversos casos:

- Quando uma ou mais colunas de \* também têm uma largura mínima ou máxima que substitui a alocação proporcional para aquela coluna. (A largura mínima pode ser derivada de uma declaração <xref:System.Windows.FrameworkElement.MinWidth%2A> explícita ou de um mínimo implícito obtido do conteúdo da coluna. A largura máxima só pode ser definida explicitamente de uma declaração <xref:System.Windows.FrameworkElement.MaxWidth%2A>.)

- Quando uma ou mais colunas de \* declaram um peso de \* extremamente grande, maior que 10^298.

- Quando os pesos de \* são diferentes o suficiente para encontrar instabilidade de ponto flutuante (estouro, estouro negativo, perda de precisão).

- Quando o arredondamento de layout está habilitado e o DPI de exibição efetivo é suficientemente alto.

Nos dois primeiros casos, as larguras produzidas pelo novo algoritmo podem ser significativamente diferentes das produzidas pelo algoritmo antigo. No último caso, a diferença será no máximo um ou dois pixels.

## <a name="mitigation"></a>Redução

Por padrão, os aplicativos destinados a versões do .NET Framework a partir do .NET Framework 4.7 usarão o novo algoritmo, enquanto os aplicativos destinados ao .NET Framework 4.6.2 ou a versões anteriores usarão o algoritmo antigo.

Para substituir o padrão, use a seguinte definição de configuração:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true" /> 
</runtime>
```

O valor 'true' seleciona o algoritmo antigo e 'false' seleciona o novo algoritmo.

## <a name="see-also"></a>Consulte também
[Alterações de redirecionamento no .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

