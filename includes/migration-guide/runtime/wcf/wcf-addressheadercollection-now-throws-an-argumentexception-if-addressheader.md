---
ms.openlocfilehash: 3506653bfc749ae3d8002715ca72ca89de7a681b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91024959"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a><span data-ttu-id="dd9e3-101">AddressHeaderCollection do WCF agora gera ArgumentException se um elemento addressHeader for nulo</span><span class="sxs-lookup"><span data-stu-id="dd9e3-101">WCF AddressHeaderCollection now throws an ArgumentException if an addressHeader element is null</span></span>

#### <a name="details"></a><span data-ttu-id="dd9e3-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="dd9e3-102">Details</span></span>

<span data-ttu-id="dd9e3-103">A partir do .NET Framework 4.7.1, o construtor <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> gera <xref:System.ArgumentException> se um elemento for `null`.</span><span class="sxs-lookup"><span data-stu-id="dd9e3-103">Starting with the .NET Framework 4.7.1, the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is `null`.</span></span> <span data-ttu-id="dd9e3-104">No .NET Framework 4.7 e versões anteriores, nenhuma exceção é gerada.</span><span class="sxs-lookup"><span data-stu-id="dd9e3-104">In the .NET Framework 4.7 and earlier versions, no exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="dd9e3-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="dd9e3-105">Suggestion</span></span>

<span data-ttu-id="dd9e3-106">Se você encontrar problemas de compatibilidade com essa alteração no .NET Framework 4.7.1 ou em uma versão posterior, poderá recusar isso adicionando a seguinte linha à `<runtime>` seção do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="dd9e3-106">If you encounter compatibility issues with this change on the .NET Framework 4.7.1 or a later version, you can opt-out of it by adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="dd9e3-107">Name</span><span class="sxs-lookup"><span data-stu-id="dd9e3-107">Name</span></span>    | <span data-ttu-id="dd9e3-108">Valor</span><span class="sxs-lookup"><span data-stu-id="dd9e3-108">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="dd9e3-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="dd9e3-109">Scope</span></span>   | <span data-ttu-id="dd9e3-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="dd9e3-110">Minor</span></span>   |
| <span data-ttu-id="dd9e3-111">Versão</span><span class="sxs-lookup"><span data-stu-id="dd9e3-111">Version</span></span> | <span data-ttu-id="dd9e3-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="dd9e3-112">4.7.1</span></span>   |
| <span data-ttu-id="dd9e3-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="dd9e3-113">Type</span></span>    | <span data-ttu-id="dd9e3-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="dd9e3-114">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="dd9e3-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="dd9e3-115">Affected APIs</span></span>

- <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>

<!--

#### Affected APIs

- `M:System.ServiceModel.Channels.AddressHeaderCollection.#ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})`

-->
