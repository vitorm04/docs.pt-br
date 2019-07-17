---
ms.openlocfilehash: 770e303ab261b97efb49a3e0865a015d8de33247
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802643"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Melhorias no algoritmo de alocação de espaço de linhas de estrela da grade

|   |   |
|---|---|
|Detalhes|Correção de um bug no [algoritmo para alocar tamanhos a ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) em um <xref:System.Windows.Controls.Grid> introduzido no .NET Framework 4.7.  Em alguns casos, como uma grade com <code>Height=&quot;Auto&quot;</code> contendo linhas vazias, as linhas foram organizadas na posição incorreta, possivelmente fora da grade.|
|Sugestão|Para que o aplicativo se beneficie dessas alterações, ele deve ser executado no .NET Framework 4.8 ou posterior.|
|Escopo|Principal|
|Versão|4.8|
|Tipo|Tempo de execução|

