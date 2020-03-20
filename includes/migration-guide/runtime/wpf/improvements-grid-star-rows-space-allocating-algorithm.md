---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237611"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Melhorias no algoritmo de alocação de espaço de linhas de estrela da grade

|   |   |
|---|---|
|Detalhes|Correção de um bug no [algoritmo para alocar tamanhos](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) em um <xref:System.Windows.Controls.Grid> introduzido no .NET Framework 4.7.  Em alguns casos, como uma grade com <code>Height=&quot;Auto&quot;</code> contendo linhas vazias, as linhas foram organizadas na posição incorreta, possivelmente fora da grade.|
|Sugestão|Para que o aplicativo se beneficie dessas alterações, ele deve ser executado no .NET Framework 4.8 ou posterior.|
|Escopo|Principal|
|Versão|4.8|
|Type|Runtime|
