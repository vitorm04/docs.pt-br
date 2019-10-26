---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887724"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Chamadas para System.Windows.Input.PenContext.Disable em sistemas habilitados para toque podem gerar ArgumentException

|   |   |
|---|---|
|Detalhes|Em algumas circunstâncias, chamadas para o método interno **System.Windows.Intput.PenContext.Disable** em sistemas habilitados para toque podem gerar uma <code>T:System.ArgumentException</code> sem tratamento devido à reentrância.|
|Sugestão|Esse problema foi resolvido no .NET Framework 4.7. Para evitar a exceção, atualize para uma versão do .NET Framework a partir de 4.7.|
|Escopo|Borda|
|Version|4.6.1|
|Digite|Redirecionando|
