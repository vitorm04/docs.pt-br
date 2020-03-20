---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887724"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Chamadas para System.Windows.Input.PenContext.Disable em sistemas habilitados para toque podem gerar ArgumentException

|   |   |
|---|---|
|Detalhes|Em algumas circunstâncias, chamadas para o método interno **System.Windows.Intput.PenContext.Disable** em sistemas habilitados para toque podem gerar uma <code>T:System.ArgumentException</code> sem tratamento devido à reentrância.|
|Sugestão|Esse problema foi resolvido no .NET Framework 4.7. Para evitar a exceção, atualize para uma versão do .NET Framework a partir de 4.7.|
|Escopo|Microsoft Edge|
|Versão|4.6.1|
|Type|Redirecionando|
