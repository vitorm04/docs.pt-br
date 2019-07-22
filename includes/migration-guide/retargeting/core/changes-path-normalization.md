---
ms.openlocfilehash: d5ef5da90dd3fc39febf8e4cd4955b4113343976
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235560"
---
### <a name="changes-in-path-normalization"></a>Alterações na normalização de caminho

|   |   |
|---|---|
|Detalhes|A partir de aplicativos destinados ao .NET Framework 4.6.2, a maneira como o tempo de execução normaliza caminhos foi alterada. Normalizar um caminho envolve modificar a cadeia de caracteres que identifica um arquivo ou caminho para que ela corresponda a um caminho válido no sistema operacional de destino. Normalmente, a normalização envolve:<ul><li>Padronização de separadores de diretório e componente.</li><li>Aplicação do diretório atual a um caminho relativo.</li><li>Avaliação do diretório relativo (.) ou do diretório pai (..) em um caminho.</li><li>Remoção de determinados caracteres.</li></ul>A partir dos aplicativos destinados ao .NET Framework 4.6.2, as seguintes alterações na normalização do caminho são habilitadas por padrão:<ul><li>O tempo de execução atende à função [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) do sistema operacional para normalizar caminhos.</li><li>A normalização não envolve mais a remoção do fim dos segmentos do diretório (como um espaço no fim do nome de um diretório).</li><li>Suporte para sintaxe de caminho do dispositivo em confiança total, incluindo <code>\\.\</code> and, for file I/O APIs in mscorlib.dll, <code>\\?\</code>.</li><li>The runtime does not validate device syntax paths.</li><li>The use of device syntax to access alternate data streams is supported.</li></ul>These changes improve performance while allowing methods to access previously inaccessible paths. Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.|
|Sugestão|Aplicativos destinados ao .NET Framework 4.6.2 ou posteriores podem recusar essa alteração e usar a normalização herdada adicionando o seguinte à seção <code>&lt;runtime&gt;</code> do arquivo de configuração de aplicativo:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplicativos destinados ao .NET Framework 4.6.1 ou anteriores, mas que são executados no .NET Framework 4.6.2 ou posteriores podem habilitar as alterações na normalização de caminho adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo de configuração de aplicativo:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.6.2|
|Tipo|Redirecionando|
