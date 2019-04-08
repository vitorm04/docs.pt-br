---
ms.openlocfilehash: 448a6160bd64143000c00d21a9ddecdc61b53475
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760154"
---
### <a name="serialport-background-thread-exceptions"></a>Exceções de thread de tela de fundo de SerialPort

|   |   |
|---|---|
|Detalhes|Threads em segundo plano criados com fluxos <xref:System.IO.Ports.SerialPort> não terminam o processo quando são geradas exceções do sistema operacional. <br/>Em aplicativos direcionados ao .NET Framework 4.7 e a versões anteriores, um processo é terminado quando uma exceção do sistema operacional é gerada em um thread em segundo plano criado com um fluxo <xref:System.IO.Ports.SerialPort>. <br/>Nos aplicativos direcionados ao .NET Framework 4.7.1 e a versões anteriores, os threads em segundo plano esperam pelos eventos do SO relacionados à porta serial ativa e podem falhar em alguns casos, como uma remoção repentina da porta serial.|
|Sugestão|Para aplicativos destinados ao .NET Framework 4.7.1, será possível recusar a manipulação de exceções se ela não for desejável adicionando o seguinte à seção <code>&lt;runtime&gt;</code> do arquivo <code>app.config</code>:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Para aplicativos destinados a versões anteriores do .NET Framework mas executados no .NET Framework 4.7.1 ou posterior, é possível aceitar a manipulação de exceções adicionando o seguinte à seção <code>&lt;runtime&gt;</code> do arquivo <code>app.config</code>:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.7.1|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.IO.Ports.SerialPort?displayProperty=nameWithType></li></ul>|

