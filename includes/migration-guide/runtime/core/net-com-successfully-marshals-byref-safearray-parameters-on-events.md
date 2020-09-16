---
ms.openlocfilehash: aadf5eb85c8736c29639d49bc8baf21545d2467c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606327"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="dbb52-101">O .NET COM realiza marshaling bem-sucedido de parâmetros ByRef SafeArray em eventos</span><span class="sxs-lookup"><span data-stu-id="dbb52-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

#### <a name="details"></a><span data-ttu-id="dbb52-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="dbb52-102">Details</span></span>

<span data-ttu-id="dbb52-103">No .NET Framework 4.7.2 e versões anteriores, um parâmetro ByRef [SafeArray](/windows/desktop/api/oaidl/ns-oaidl-safearray) em um evento COM falharia realizar marshaling de volta para o código nativo.</span><span class="sxs-lookup"><span data-stu-id="dbb52-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="dbb52-104">Com essa alteração, agora o marshal do [SafeArray](/windows/desktop/api/oaidl/ns-oaidl-safearray) foi realizado com êxito.</span><span class="sxs-lookup"><span data-stu-id="dbb52-104">With this change the [SafeArray](/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="dbb52-105">[x] Quirked</span><span class="sxs-lookup"><span data-stu-id="dbb52-105">[ x ] Quirked</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="dbb52-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="dbb52-106">Suggestion</span></span>

<span data-ttu-id="dbb52-107">Se a realização de marshal dos parâmetros ByRef SafeArray corretamente em eventos COM interromper a execução, será possível desabilitar esse código adicionando a seguinte opção de configuração à sua configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="dbb52-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="dbb52-108">Name</span><span class="sxs-lookup"><span data-stu-id="dbb52-108">Name</span></span>    | <span data-ttu-id="dbb52-109">Valor</span><span class="sxs-lookup"><span data-stu-id="dbb52-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="dbb52-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="dbb52-110">Scope</span></span>   |<span data-ttu-id="dbb52-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="dbb52-111">Minor</span></span>|
|<span data-ttu-id="dbb52-112">Versão</span><span class="sxs-lookup"><span data-stu-id="dbb52-112">Version</span></span>|<span data-ttu-id="dbb52-113">4.8</span><span class="sxs-lookup"><span data-stu-id="dbb52-113">4.8</span></span>|
|<span data-ttu-id="dbb52-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="dbb52-114">Type</span></span>|<span data-ttu-id="dbb52-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="dbb52-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="dbb52-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="dbb52-116">Affected APIs</span></span>

<span data-ttu-id="dbb52-117">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="dbb52-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
