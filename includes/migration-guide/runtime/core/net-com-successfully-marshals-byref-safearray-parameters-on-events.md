---
ms.openlocfilehash: 9c72bc686e014a0bffdf272e3813358d1b29cc66
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65198760"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>O .NET COM realiza marshaling bem-sucedido de parâmetros ByRef SafeArray em eventos

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.7.2 e versões anteriores, um parâmetro ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) em um evento COM falharia realizar marshaling de volta para o código nativo.  Com essa alteração, o [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) agora tem o marshaling realizado com êxito.<ul><li>[x] Quirked</li></ul>|
|Sugestão|Se fizer marshaling dos parâmetros ByRef SafeArray corretamente em eventos COM interrompe a execução, você poderá desabilitar esse código, adicionando a seguinte opção de configuração à sua configuração de aplicativo:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.8|
|Tipo|Tempo de execução|
