---
ms.openlocfilehash: 0036fc2b03dde64d24d883e55b9f00c931f0c218
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997539"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>A Interoperabilidade do .NET agora fará QueryInterface para IAgileObject (uma interface do WinRT)

|   |   |
|---|---|
|Detalhes|Ao usar um evento de WinRT com um delegado do .NET, Windows fará QI para IAgileObject começando com o .NET Framework 4.8.  Nas versões anteriores do .NET Framework, o tempo de execução falharia nessa QI e o evento não poderia ser assinado.<ul><li>[x] Quirked</li></ul>|
|Sugestão|Se a habilitação de QI para IAgileObject interromper a execução, você poderá desabilitar esse código definindo a configuração a seguir. <h4>Método 1: Variável de ambiente</h4> Defina a variável de ambiente a seguir:COMPLUS_DisableCCWSupportIAgileObject=1Esse método afeta qualquer ambiente que herda essa variável de ambiente. Isso pode ser apenas uma única sessão de console ou pode afetar o computador inteiro se você definir a variável de ambiente globalmente. O nome da variável de ambiente não diferencia maiúsculas de minúsculas. <h4>Método 2: Registro</h4> Usando o Editor do Registro (regedit.exe), localize qualquer uma das seguintes subchaves:HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER\SOFTWARE\Microsoft.NETFrameworkEm seguida, adicione o seguinte:Nome do valor: DisableCCWSupportIAgileObject Tipo: DWORD (32 bits) Valor (também chamado REG_WORD) Valor: 1É possível usar a ferramenta REG.EXE do Windows para adicionar esse valor de uma linha de comando ou ambiente de script. Por exemplo:<pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>Nesse caso, <code>HKLM</code> é usado em vez de <code>HKEY_LOCAL_MACHINE</code>. Use <code>reg add /?</code> para ver a ajuda nessa sintaxe. O nome do valor do registro não diferencia maiúsculas de minúsculas.|
|Escopo|Microsoft Edge|
|Version|4.8|
|Tipo|Tempo de execução|
