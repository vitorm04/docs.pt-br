---
ms.openlocfilehash: 06a21b664ea0981663219a697fbc1bfc9be50287
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859132"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a>CspParameters.ParentWindowHandle agora espera o valor HWND

|   |   |
|---|---|
|Detalhes|O valor <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle>, introduzido no .NET Framework 2.0, permite que um aplicativo registre um valor de identificador de janela pai, de modo que qualquer interface do usuário necessária para acessar a chave (por exemplo, uma caixa de diálogo de solicitação de PIN ou de consentimento) seja aberta como um filho modal para a janela especificada. A partir dos aplicativos destinados ao .NET Framework 4.7, um aplicativo do Windows Forms pode definir a propriedade <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> com código como o seguinte:<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>Em versões anteriores do .NET Framework, esperava-se que o valor fosse um <xref:System.IntPtr?displayProperty=name> representando um local na memória em que o valor de [HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND) residia. Definir a propriedade como form.Handle no Windows 7 e em versões anteriores não tinha efeito. No Windows 8 e em versões posteriores, isso resulta em uma &quot;<xref:System.Security.Cryptography.CryptographicException?displayProperty=name>: o parâmetro está incorreto.&quot;|
|Sugestão|Os aplicativos direcionados ao .NET Framework 4.7 ou posterior que desejam registrar um relacionamento de janela pai são incentivados a usar o formato simplificado:<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>Usuários que identificaram que o valor correto a ser passado era o endereço de um local da memória que mantinha o valor de <code>form.Handle</code> podem recusar essa alteração de comportamento definindo o comutador AppContext <code>Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle</code> como <code>true</code>:<ol><li>Configurando de forma programática as opções de compatibilidade em AppContext, conforme explicado [aqui](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</li><li>Adicionando a seguinte linha na seção <code>&lt;runtime&gt;</code> do arquivo app.config:</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Por outro lado, usuários que quiserem aceitar o novo comportamento no tempo de execução do .NET Framework 4.7 quando o aplicativo for carregado em versões anteriores do .NET Framework podem definir a opção de AppContext como <code>false</code>.|
|Escopo|Secundário|
|Versão|4.7|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType></li></ul>|

