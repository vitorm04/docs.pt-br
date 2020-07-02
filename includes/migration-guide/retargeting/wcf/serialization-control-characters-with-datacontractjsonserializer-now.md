---
ms.openlocfilehash: afdf1e20db7dc564ddfb6028238604f97e00971a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614295"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a><span data-ttu-id="f79e3-101">Serialização de caracteres de controle com DataContractJsonSerializer agora é compatível com ECMAScript V6 e V8</span><span class="sxs-lookup"><span data-stu-id="f79e3-101">Serialization of control characters with DataContractJsonSerializer is now compatible with ECMAScript V6 and V8</span></span>

#### <a name="details"></a><span data-ttu-id="f79e3-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f79e3-102">Details</span></span>

<span data-ttu-id="f79e3-103">No .NET Framework 4.6.2 e versões anteriores, o não <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> serializava alguns caracteres de controle especiais, como \b, \f e \t, de forma que fosse compatível com os padrões ECMAScript V6 e V8.</span><span class="sxs-lookup"><span data-stu-id="f79e3-103">In .NET Framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> did not serialize some special control characters, such as \b, \f, and \t, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span> <span data-ttu-id="f79e3-104">A partir do .NET Framework 4,7, a serialização desses caracteres de controle é compatível com ECMAScript V6 e V8.</span><span class="sxs-lookup"><span data-stu-id="f79e3-104">Starting with .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f79e3-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="f79e3-105">Suggestion</span></span>

<span data-ttu-id="f79e3-106">Por padrão, esse novo layout é habilitado para aplicativos que se destinam ao .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="f79e3-106">For apps that target the .NET Framework 4.7, this feature is enabled by default.</span></span> <span data-ttu-id="f79e3-107">Se esse comportamento não for desejado, você poderá recusar esse recurso adicionando a seguinte linha na seção `<runtime>` do arquivo app.config ou web.config:</span><span class="sxs-lookup"><span data-stu-id="f79e3-107">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

| <span data-ttu-id="f79e3-108">Name</span><span class="sxs-lookup"><span data-stu-id="f79e3-108">Name</span></span>    | <span data-ttu-id="f79e3-109">Valor</span><span class="sxs-lookup"><span data-stu-id="f79e3-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f79e3-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="f79e3-110">Scope</span></span>   | <span data-ttu-id="f79e3-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="f79e3-111">Edge</span></span>        |
| <span data-ttu-id="f79e3-112">Versão</span><span class="sxs-lookup"><span data-stu-id="f79e3-112">Version</span></span> | <span data-ttu-id="f79e3-113">4.7</span><span class="sxs-lookup"><span data-stu-id="f79e3-113">4.7</span></span>         |
| <span data-ttu-id="f79e3-114">Type</span><span class="sxs-lookup"><span data-stu-id="f79e3-114">Type</span></span>    | <span data-ttu-id="f79e3-115">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="f79e3-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="f79e3-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="f79e3-116">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType>
