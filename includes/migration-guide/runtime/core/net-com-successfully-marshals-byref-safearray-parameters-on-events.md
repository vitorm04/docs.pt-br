---
ms.openlocfilehash: 6ff23bbe8c48235770d39cb7d35a1df7de6c5201
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68440247"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>O .NET COM realiza marshaling bem-sucedido de parâmetros ByRef SafeArray em eventos

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.7.2 e versões anteriores, um parâmetro ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) em um evento COM falharia realizar marshaling de volta para o código nativo.  Com essa alteração, agora o marshal do [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) foi realizado com êxito.<ul><li>[x] Quirked</li></ul>|
|Sugestão|Se a realização de marshal dos parâmetros ByRef SafeArray corretamente em eventos COM interromper a execução, será possível desabilitar esse código adicionando a seguinte opção de configuração à sua configuração de aplicativo:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.8|
|Tipo|Tempo de execução|
