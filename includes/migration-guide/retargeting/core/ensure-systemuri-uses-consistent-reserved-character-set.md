---
ms.openlocfilehash: 4f92d773197c914a74dd7e9c18f5aab5309358ae
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760772"
---
### <a name="ensure-systemuri-uses-a-consistent-reserved-character-set"></a>Verifique se o System.URI usa um conjunto consistente de caracteres reservados

|   |   |
|---|---|
|Detalhes|No <xref:System.Uri?displayProperty=fullName>, determinados caracteres codificados por porcentagem que, às vezes, eram decodificados agora permanecem codificados de forma consistente. Isso ocorre nas propriedades e nos métodos que acessam os componentes de caminho, consulta, fragmento ou informações do usuário do URI. O comportamento será alterado somente quando os dois itens a seguir forem verdadeiros:<ul><li>O URI contiver a forma codificada de um dos seguintes caracteres reservados: <code>:</code>, <code>'</code>, <code>(</code>, <code>)</code>, <code>!</code> ou <code>*</code>.</li><li>O URI contiver um caractere Unicode ou não reservado codificado. Se ambas as condições acima forem verdadeiras, os caracteres reservados codificados serão deixados codificados. Nas versões anteriores do .NET Framework, eles são decodificados.</li></ul>|
|Sugestão|Para aplicativos direcionados a versões do .NET Framework começando com a 4.7.2, o novo comportamento de decodificação é habilitado por padrão. Se essa alteração não for desejada, você poderá desabilitá-la adicionando a seguinte opção [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) à seção <code>&lt;runtime&gt;</code> do arquivo de configuração de aplicativo:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Para aplicativos direcionados a versões anteriores do .NET Framework, mas executados em versões começando com o .NET Framework 4.7.2, o novo comportamento de decodificação é desabilitado por padrão. Você poderá habilitá-la adicionando a seguinte opção [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) à seção <code>&lt;runtime&gt;</code> do arquivo de configuração de aplicativo:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.7.2|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

