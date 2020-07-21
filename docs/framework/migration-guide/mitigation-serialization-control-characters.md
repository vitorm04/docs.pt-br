---
title: Serialização de caracteres de controle com DataContractJsonSerializer
description: Saiba como a serialização de caracteres de controle foi alterada para estar em conformidade com ECMAScript V6 e V8 no .NET Framework 4,7.
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: a317884da014097a7a60aef2cef4ec146ccb04f7
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475379"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="407fe-103">Mitigação: serialização de caracteres de controle com o DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="407fe-103">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="407fe-104">A partir do .NET Framework 4,7, a maneira como os caracteres de controle são serializados com o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> foi alterado para estar de acordo com o ECMAScript V6 e o V8.</span><span class="sxs-lookup"><span data-stu-id="407fe-104">Starting with .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span>

## <a name="impact"></a><span data-ttu-id="407fe-105">Impacto</span><span class="sxs-lookup"><span data-stu-id="407fe-105">Impact</span></span>

<span data-ttu-id="407fe-106">No .NET Framework 4.6.2 e em versões anteriores, o não <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> serializava alguns caracteres de controle especiais, como `\b` , `\f` e `\t` , de uma forma que era compatível com os padrões do ECMAScript V6 e do V8.</span><span class="sxs-lookup"><span data-stu-id="407fe-106">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="407fe-107">Para aplicativos que visam versões do .NET Framework a partir do .NET Framework 4,7, a serialização desses caracteres de controle é compatível com ECMAScript V6 e V8.</span><span class="sxs-lookup"><span data-stu-id="407fe-107">For apps that target versions of .NET Framework starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="407fe-108">As seguintes APIs são afetadas:</span><span class="sxs-lookup"><span data-stu-id="407fe-108">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="407fe-109">Atenuação</span><span class="sxs-lookup"><span data-stu-id="407fe-109">Mitigation</span></span>

<span data-ttu-id="407fe-110">Para aplicativos que visam versões do .NET Framework a partir do .NET Framework 4,7, esse comportamento é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="407fe-110">For apps that target versions of .NET Framework starting with .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="407fe-111">Se esse comportamento não for desejado, você poderá recusar esse recurso adicionando a seguinte linha na seção `<runtime>` do arquivo app.config ou web.config:</span><span class="sxs-lookup"><span data-stu-id="407fe-111">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="407fe-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="407fe-112">See also</span></span>

- [<span data-ttu-id="407fe-113">Compatibilidade de aplicativos</span><span class="sxs-lookup"><span data-stu-id="407fe-113">Application compatibility</span></span>](application-compatibility.md)
