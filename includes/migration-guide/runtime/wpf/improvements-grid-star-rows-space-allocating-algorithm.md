---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237611"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Melhorias no algoritmo de alocação de espaço de linhas de estrela da grade

|   |   |
|---|---|
|Detalhes|Correção de um bug no [algoritmo para alocar tamanhos](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) em um <xref:System.Windows.Controls.Grid> introduzido no .NET Framework 4.7.  Em alguns casos, como uma grade com <code>Height=&quot;Auto&quot;</code> contendo linhas vazias, as linhas foram organizadas na posição incorreta, possivelmente fora da grade.|
|Sugestão|Para que o aplicativo se beneficie dessas alterações, ele deve ser executado no .NET Framework 4.8 ou posterior.|
|Escopo|Principal|
|Versão|4.8|
|Tipo|Tempo de execução|
