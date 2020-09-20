---
ms.openlocfilehash: e8b98e465228afd07432e737bb16aefb1b979973
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770857"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a><span data-ttu-id="abad4-101">AddressHeaderCollection do WCF agora gera ArgumentException se um elemento addressHeader for nulo</span><span class="sxs-lookup"><span data-stu-id="abad4-101">WCF AddressHeaderCollection now throws an ArgumentException if an addressHeader element is null</span></span>

#### <a name="details"></a><span data-ttu-id="abad4-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="abad4-102">Details</span></span>

<span data-ttu-id="abad4-103">A partir do .NET Framework 4.7.1, o construtor <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> gera <xref:System.ArgumentException> se um elemento for `null`.</span><span class="sxs-lookup"><span data-stu-id="abad4-103">Starting with the .NET Framework 4.7.1, the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is `null`.</span></span> <span data-ttu-id="abad4-104">No .NET Framework 4.7 e versões anteriores, nenhuma exceção é gerada.</span><span class="sxs-lookup"><span data-stu-id="abad4-104">In the .NET Framework 4.7 and earlier versions, no exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="abad4-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="abad4-105">Suggestion</span></span>

<span data-ttu-id="abad4-106">Se você encontrar problemas de compatibilidade com essa alteração no .NET Framework 4.7.1 ou em uma versão posterior, poderá recusar isso adicionando a seguinte linha à `<runtime>` seção do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="abad4-106">If you encounter compatibility issues with this change on the .NET Framework 4.7.1 or a later version, you can opt-out of it by adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true" />
  </runtime>
</configuration>

| Name    | Value   |
|:--------|:--------|
| Scope   | Minor   |
| Version | 4.7.1   |
| Type    | Runtime |

#### Affected APIs

- <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>

<!--

#### Affected APIs

- `M:System.ServiceModel.Channels.AddressHeaderCollection.#ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})`

-->
