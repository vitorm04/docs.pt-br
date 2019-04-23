---
ms.openlocfilehash: ad624a665dbe8e989ea05acc20213809e515e6ac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803167"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>Geração de código incorreto ao passar e comparar valores UInt16

|   |   |
|---|---|
|Detalhes|Em virtude das alterações realizadas no .NET Framework 4.7, em alguns casos, o código gerado pelo compilador JIT em aplicativos em execução no .NET Framework 4.7 é incorretamente comparado com dois valores <code>T:System.UInt16</code>. Para obter mais informações, confira [Problema nº 11508: Geração de código silenciosa incorreta ao passar e comparar ushort args](https://github.com/dotnet/coreclr/issues/11508) no GitHub.com.|
|Sugestão|Se houver problemas na comparação dos valores sem sinal de 16 bits no .NET Framework 4.7, atualize para o .NET Framework 4.7.1.|
|Escopo|Microsoft Edge|
|Versão|4.7|
|Tipo|Tempo de execução|
