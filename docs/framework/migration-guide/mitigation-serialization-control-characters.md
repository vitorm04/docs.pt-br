---
title: 'Mitigação: Serialização de caracteres de controle com o DataContractJsonSerializer'
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3355841298e039652eb81918eac98186c1a1f833
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182111"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="547a7-102">Mitigação: Serialização de caracteres de controle com o DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="547a7-102">Mitigation: Serialization of Control Characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="547a7-103">A partir do .NET Framework 4.7, a maneira com a qual os caracteres de controle são serializados com o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> foi alterada para estar em conformidade com o ECMAScript V6 e V8.</span><span class="sxs-lookup"><span data-stu-id="547a7-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="547a7-104">Impacto</span><span class="sxs-lookup"><span data-stu-id="547a7-104">Impact</span></span>

<span data-ttu-id="547a7-105">No .NET framework 4.6.2 e nas versões anteriores, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> não serializava alguns caracteres de controle especiais, como `\b`, `\f` e `\t`, de uma forma compatível com os padrões ECMAScript V6 e V8.</span><span class="sxs-lookup"><span data-stu-id="547a7-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="547a7-106">Para aplicativos destinados a versões do .NET Framework, a partir do .NET Framework 4.7, a serialização desses caracteres de controle é compatível com o ECMAScript V6 e V8.</span><span class="sxs-lookup"><span data-stu-id="547a7-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="547a7-107">As seguintes APIs são afetadas:</span><span class="sxs-lookup"><span data-stu-id="547a7-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a><span data-ttu-id="547a7-108">Redução</span><span class="sxs-lookup"><span data-stu-id="547a7-108">Mitigation</span></span>

<span data-ttu-id="547a7-109">Para aplicativos destinados a versões do .NET Framework, a partir do .NET Framework 4.7, esse comportamento é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="547a7-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="547a7-110">Se esse comportamento não for desejado, você poderá recusar esse recurso adicionando a seguinte linha na seção `<runtime>` do arquivo app.config ou web.config:</span><span class="sxs-lookup"><span data-stu-id="547a7-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="547a7-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="547a7-111">See also</span></span>

- [<span data-ttu-id="547a7-112">Alterações de redirecionamento no .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="547a7-112">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
