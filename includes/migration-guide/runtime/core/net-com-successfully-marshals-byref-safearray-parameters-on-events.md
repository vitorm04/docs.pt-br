---
ms.openlocfilehash: 77e9d28d79a92cf1523e4ef5779d78394b00ae80
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621911"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="f182b-101">O .NET COM realiza marshaling bem-sucedido de parâmetros ByRef SafeArray em eventos</span><span class="sxs-lookup"><span data-stu-id="f182b-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

#### <a name="details"></a><span data-ttu-id="f182b-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f182b-102">Details</span></span>

<span data-ttu-id="f182b-103">No .NET Framework 4.7.2 e versões anteriores, um parâmetro ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) em um evento COM falharia realizar marshaling de volta para o código nativo.</span><span class="sxs-lookup"><span data-stu-id="f182b-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="f182b-104">Com essa alteração, agora o marshal do [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) foi realizado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f182b-104">With this change the [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="f182b-105">[x] Quirked</span><span class="sxs-lookup"><span data-stu-id="f182b-105">[ x ] Quirked</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="f182b-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="f182b-106">Suggestion</span></span>

<span data-ttu-id="f182b-107">Se a realização de marshal dos parâmetros ByRef SafeArray corretamente em eventos COM interromper a execução, será possível desabilitar esse código adicionando a seguinte opção de configuração à sua configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="f182b-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="f182b-108">Name</span><span class="sxs-lookup"><span data-stu-id="f182b-108">Name</span></span>    | <span data-ttu-id="f182b-109">Valor</span><span class="sxs-lookup"><span data-stu-id="f182b-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f182b-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="f182b-110">Scope</span></span>   |<span data-ttu-id="f182b-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="f182b-111">Minor</span></span>|
|<span data-ttu-id="f182b-112">Versão</span><span class="sxs-lookup"><span data-stu-id="f182b-112">Version</span></span>|<span data-ttu-id="f182b-113">4.8</span><span class="sxs-lookup"><span data-stu-id="f182b-113">4.8</span></span>|
|<span data-ttu-id="f182b-114">Type</span><span class="sxs-lookup"><span data-stu-id="f182b-114">Type</span></span>|<span data-ttu-id="f182b-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="f182b-115">Runtime</span></span>|
