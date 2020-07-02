---
ms.openlocfilehash: d29be721b50d1c93723b325774a06e86f77dbebf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621019"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a><span data-ttu-id="54347-101">AddressHeaderCollection do WCF agora gera ArgumentException se um elemento addressHeader for nulo</span><span class="sxs-lookup"><span data-stu-id="54347-101">WCF AddressHeaderCollection now throws an ArgumentException if an addressHeader element is null</span></span>

#### <a name="details"></a><span data-ttu-id="54347-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="54347-102">Details</span></span>

<span data-ttu-id="54347-103">A partir do .NET Framework 4.7.1, o construtor <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> gera <xref:System.ArgumentException> se um elemento for <code>null</code>.</span><span class="sxs-lookup"><span data-stu-id="54347-103">Starting with the .NET Framework 4.7.1, the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is <code>null</code>.</span></span> <span data-ttu-id="54347-104">No .NET Framework 4.7 e versões anteriores, nenhuma exceção é gerada.</span><span class="sxs-lookup"><span data-stu-id="54347-104">In the .NET Framework 4.7 and earlier versions, no exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="54347-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="54347-105">Suggestion</span></span>

<span data-ttu-id="54347-106">Se houver problemas de compatibilidade com essa alteração no .NET Framework 4.7.1 ou uma versão anterior, será possível recusá-la adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="54347-106">If you encounter compatibility issues with this change on the .NET Framework 4.7.1 or a later version, you can opt-out of it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config file::</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="54347-107">Name</span><span class="sxs-lookup"><span data-stu-id="54347-107">Name</span></span>    | <span data-ttu-id="54347-108">Valor</span><span class="sxs-lookup"><span data-stu-id="54347-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="54347-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="54347-109">Scope</span></span>   |<span data-ttu-id="54347-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="54347-110">Minor</span></span>|
|<span data-ttu-id="54347-111">Versão</span><span class="sxs-lookup"><span data-stu-id="54347-111">Version</span></span>|<span data-ttu-id="54347-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="54347-112">4.7.1</span></span>|
|<span data-ttu-id="54347-113">Type</span><span class="sxs-lookup"><span data-stu-id="54347-113">Type</span></span>|<span data-ttu-id="54347-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="54347-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="54347-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="54347-115">Affected APIs</span></span>

-<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})></li></ul>|
