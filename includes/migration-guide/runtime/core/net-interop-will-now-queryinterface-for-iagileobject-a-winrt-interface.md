---
ms.openlocfilehash: 0036fc2b03dde64d24d883e55b9f00c931f0c218
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997539"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>A Interoperabilidade do .NET agora fará QueryInterface para IAgileObject (uma interface do WinRT)

|   |   |
|---|---|
|Detalhes|Ao usar um evento de WinRT com um delegado do .NET, Windows fará QI para IAgileObject começando com o .NET Framework 4.8.  Nas versões anteriores do .NET Framework, o runtime falharia nessa QI e o evento não poderia ser assinado.<ul><li>[x] Quirked</li></ul>|
|Sugestão|Se a habilitação de QI para IAgileObject interromper a execução, você poderá desabilitar esse código definindo a configuração a seguir. <h4>Método 1: Variável de ambiente</h4> Defina a variável de ambiente a seguir:COMPLUS_DisableCCWSupportIAgileObject=1Esse método afeta qualquer ambiente que herda essa variável de ambiente. Esta pode ser apenas uma única sessão de console, ou pode afetar toda a máquina se você definir a variável ambiente globalmente. O nome da variável ambiente não é sensível a maiúsculas e minúsculas. <h4>Método 2: Registro</h4> Usando o Editor de Registro (regedit.exe), encontre qualquer uma das seguintes subchaves:HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER\SOFTWARE\Microsoft.NETFrameworkEmadicionar o seguinte:Nome de valor: DesativarCCWSupportIAgileObject Tipo: DWORD (32 bits) Valor (também chamado de REG_WORD) Valor: 1Você pode usar o REG do Windows. Ferramenta EXE para adicionar esse valor a partir de um ambiente de linha de comando ou scripting. Por exemplo: <pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>Nesse caso, <code>HKLM</code> é usado em vez de <code>HKEY_LOCAL_MACHINE</code>. Use <code>reg add /?</code> para ver ajuda nesta sintaxe. O nome do valor do registro não é sensível a maiúsculas e minúsculas.|
|Escopo|Microsoft Edge|
|Versão|4.8|
|Type|Runtime|
