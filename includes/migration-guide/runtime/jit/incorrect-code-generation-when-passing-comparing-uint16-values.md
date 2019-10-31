---
ms.openlocfilehash: b23909c53b451b4b18bf0ccdf59f51e7c8e3114f
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802561"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>Geração de código incorreto ao passar e comparar valores UInt16

|   |   |
|---|---|
|Detalhes|Em virtude das alterações realizadas no .NET Framework 4.7, em alguns casos, o código gerado pelo compilador JIT em aplicativos em execução no .NET Framework 4.7 é incorretamente comparado com dois valores <code>T:System.UInt16</code>. Para obter mais informações, confira [Problema nº 11508: Geração de código silenciosa incorreta ao passar e comparar ushort args](https://github.com/dotnet/coreclr/issues/11508) no GitHub.com.|
|Sugestão|Se houver problemas na comparação dos valores sem sinal de 16 bits no .NET Framework 4.7, atualize para o .NET Framework 4.7.1.|
|Escopo|Microsoft Edge|
|Versão|4.7|
|Tipo|Tempo de execução|

