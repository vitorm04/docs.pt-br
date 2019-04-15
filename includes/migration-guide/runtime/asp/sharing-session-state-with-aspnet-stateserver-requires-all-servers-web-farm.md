---
ms.openlocfilehash: 958a89015420ce5632d596688963d576c40b4cb6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235059"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a>Compartilhamento de estado de sessão com StateServer Asp.Net exige que todos os servidores no web farm usem a mesma versão do .NET Framework

|   |   |
|---|---|
|Detalhes|Ao habilitar o estado de sessão <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name>, todos os servidores no web farm fornecido devem usar a mesma versão do .NET Framework para o estado ser compartilhado corretamente.|
|Sugestão|Certifique-se de atualizar as versões do .NET Framework em servidores Web que compartilham o estado ao mesmo tempo.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|
