---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803188"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>Aplicativos ASP.NET MVC4 de criação de perfil podem causar Erro Fatal do Mecanismo de Execução

|   |   |
|---|---|
|Detalhes|Os criadores de perfil que usam NGEN/assemblies de perfil podem causar pane em aplicativos ASP.NET MVC4 de criação de perfil na inicialização com o "Erro Fatal do Mecanismo de Execução".|
|Sugestão|Esse problema foi corrigido no .NET Framework 4.5.2. Como alternativa, o criador de perfil pode evitar esse problema especificando <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> em sua máscara de evento.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
