---
title: Serialização de caracteres de controle com DataContractJsonSerializer
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: b6468bc4ae37765d969a1f92b16967cc656ab7ff
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452624"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="ff94f-102">Mitigação: serialização de caracteres de controle com o DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="ff94f-102">Mitigation: Serialization of control characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="ff94f-103">A partir do .NET Framework 4,7, a maneira como os caracteres de controle são serializados com a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> foi alterada para estar em conformidade com ECMAScript V6 e V8.</span><span class="sxs-lookup"><span data-stu-id="ff94f-103">Starting with .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="ff94f-104">Impacto</span><span class="sxs-lookup"><span data-stu-id="ff94f-104">Impact</span></span>

<span data-ttu-id="ff94f-105">No .NET Framework 4.6.2 e versões anteriores, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> não serializava alguns caracteres de controle especiais, como `\b`, `\f`e `\t`, de forma que fosse compatível com os padrões ECMAScript V6 e V8.</span><span class="sxs-lookup"><span data-stu-id="ff94f-105">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="ff94f-106">Para aplicativos que visam versões do .NET Framework a partir do .NET Framework 4,7, a serialização desses caracteres de controle é compatível com ECMAScript V6 e V8.</span><span class="sxs-lookup"><span data-stu-id="ff94f-106">For apps that target versions of .NET Framework starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="ff94f-107">As seguintes APIs são afetadas:</span><span class="sxs-lookup"><span data-stu-id="ff94f-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a><span data-ttu-id="ff94f-108">Atenuação</span><span class="sxs-lookup"><span data-stu-id="ff94f-108">Mitigation</span></span>

<span data-ttu-id="ff94f-109">Para aplicativos que visam versões do .NET Framework a partir do .NET Framework 4,7, esse comportamento é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="ff94f-109">For apps that target versions of .NET Framework starting with .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="ff94f-110">Se esse comportamento não for desejado, você poderá recusar esse recurso adicionando a seguinte linha na seção `<runtime>` do arquivo app.config ou web.config:</span><span class="sxs-lookup"><span data-stu-id="ff94f-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="ff94f-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="ff94f-111">See also</span></span>

- [<span data-ttu-id="ff94f-112">Compatibilidade de aplicativos</span><span class="sxs-lookup"><span data-stu-id="ff94f-112">Application compatibility</span></span>](application-compatibility.md)
