---
title: Serialização de caracteres de controle com DataContractJsonSerializer
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: b60b78f9ee944552fafbe75754ecd29d60dd4093
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181204"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="fc399-102">Mitigação: Serialização de caracteres de controle com o DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="fc399-102">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="fc399-103">Começando com .NET Framework 4.7, a forma como <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> os caracteres de controle são serializados com o mudou para estar em conformidade com eCMAScript V6 e V8.</span><span class="sxs-lookup"><span data-stu-id="fc399-103">Starting with .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span>

## <a name="impact"></a><span data-ttu-id="fc399-104">Impacto</span><span class="sxs-lookup"><span data-stu-id="fc399-104">Impact</span></span>

<span data-ttu-id="fc399-105">No .NET Framework 4.6.2 e <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nas versões anteriores, `\b`o `\f`não `\t`serializava alguns caracteres de controle especiais, como , e , de uma forma compatível com os padrões ECMAScript V6 e V8.</span><span class="sxs-lookup"><span data-stu-id="fc399-105">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="fc399-106">Para aplicativos que visam versões do .NET Framework a partir do .NET Framework 4.7, a serialização desses caracteres de controle é compatível com ECMAScript V6 e V8.</span><span class="sxs-lookup"><span data-stu-id="fc399-106">For apps that target versions of .NET Framework starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="fc399-107">As seguintes APIs são afetadas:</span><span class="sxs-lookup"><span data-stu-id="fc399-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="fc399-108">Atenuação</span><span class="sxs-lookup"><span data-stu-id="fc399-108">Mitigation</span></span>

<span data-ttu-id="fc399-109">Para aplicativos que visam versões do .NET Framework a partir do .NET Framework 4.7, esse comportamento é ativado por padrão.</span><span class="sxs-lookup"><span data-stu-id="fc399-109">For apps that target versions of .NET Framework starting with .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="fc399-110">Se esse comportamento não for desejado, você poderá recusar esse recurso adicionando a seguinte linha na seção `<runtime>` do arquivo app.config ou web.config:</span><span class="sxs-lookup"><span data-stu-id="fc399-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="fc399-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="fc399-111">See also</span></span>

- [<span data-ttu-id="fc399-112">Compatibilidade de aplicativos</span><span class="sxs-lookup"><span data-stu-id="fc399-112">Application compatibility</span></span>](application-compatibility.md)
