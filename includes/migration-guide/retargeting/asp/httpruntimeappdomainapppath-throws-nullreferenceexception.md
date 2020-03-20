---
ms.openlocfilehash: e7154919d6a09a04e650d5546feb2ae6c6cc912f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859103"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a>HttpRuntime.AppDomainAppPath gera NullReferenceException

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.6.2, o runtime gera <code>T:System.NullReferenceException</code> ao recuperar um valor <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> que inclui caracteres nulos. No .NET Framework 4.6.1 e versões anteriores, o runtime gera <code>T:System.ArgumentNullException</code>.|
|Sugestão|Você pode fazer o seguinte para responder a essa alteração:<ul><li>Identifique o <code>T:System.NullReferenceException</code> se o aplicativo estiver sendo executado no .NET Framework 4.6.2.</li><li>Atualize para o .NET Framework 4.7, que restaura o comportamento anterior e gera <code>T:System.ArgumentNullException</code>.</li></ul>|
|Escopo|Microsoft Edge|
|Versão|4.6.2|
|Type|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|
