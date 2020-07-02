---
ms.openlocfilehash: b88f7d4a17f885b687d99ab9410a56039e176080
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614270"
---
### <a name="calls-to-claimsidentity-constructors"></a><span data-ttu-id="ec594-101">Chamadas para construtores ClaimsIdentity</span><span class="sxs-lookup"><span data-stu-id="ec594-101">Calls to ClaimsIdentity constructors</span></span>

#### <a name="details"></a><span data-ttu-id="ec594-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ec594-102">Details</span></span>

<span data-ttu-id="ec594-103">A partir do .NET Framework 4.6.2, haverá uma alteração na maneira como os construtores <xref:System.Security.Claims.ClaimsIdentity> com um parâmetro <xref:System.Security.Principal.IIdentity?displayProperty=fullName> configuram a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="ec594-103">Starting with the .NET Framework 4.6.2, there is a change in how <xref:System.Security.Claims.ClaimsIdentity> constructors with an <xref:System.Security.Principal.IIdentity?displayProperty=fullName> parameter set the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property.</span></span> <span data-ttu-id="ec594-104">Se o argumento <xref:System.Security.Principal.IIdentity?displayProperty=fullName> for um objeto <xref:System.Security.Claims.ClaimsIdentity> e a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> desse objeto <xref:System.Security.Claims.ClaimsIdentity> não for `null`, a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> será anexada usando o método <xref:System.Security.Claims.ClaimsIdentity.Clone>.</span><span class="sxs-lookup"><span data-stu-id="ec594-104">If the <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argument is a <xref:System.Security.Claims.ClaimsIdentity> object, and the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of that <xref:System.Security.Claims.ClaimsIdentity> object is not `null`, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property is attached by using the <xref:System.Security.Claims.ClaimsIdentity.Clone> method.</span></span> <span data-ttu-id="ec594-105">No Framework 4.6.1 e versões anteriores, a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> é anexada como uma referência existente. Por causa desta alteração, a partir do .NET Framework 4.6.2, a propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> do novo objeto <xref:System.Security.Claims.ClaimsIdentity> não será igual à propriedade <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> do argumento <xref:System.Security.Principal.IIdentity?displayProperty=fullName> do construtor.</span><span class="sxs-lookup"><span data-stu-id="ec594-105">In the Framework 4.6.1 and earlier versions, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property is attached as an existing reference.Because of this change, starting with the .NET Framework 4.6.2, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of the new <xref:System.Security.Claims.ClaimsIdentity> object is not equal to the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of the constructor's <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argument.</span></span> <span data-ttu-id="ec594-106">No .NET Framework 4.6.1 e nas versões anteriores, ele é igual.</span><span class="sxs-lookup"><span data-stu-id="ec594-106">In the .NET Framework 4.6.1 and earlier versions, it is equal.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ec594-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ec594-107">Suggestion</span></span>

<span data-ttu-id="ec594-108">Se esse comportamento for indesejável, restaure o comportamento anterior definindo a opção `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` no arquivo de configuração do aplicativo como `true`.</span><span class="sxs-lookup"><span data-stu-id="ec594-108">If this behavior is undesirable, you can restore the previous behavior by setting the `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` switch in your application configuration file to `true`.</span></span> <span data-ttu-id="ec594-109">Isso exige que você adicione o seguinte à seção `<runtime>` do arquivo web.config:</span><span class="sxs-lookup"><span data-stu-id="ec594-109">This requires that you add the following to the `<runtime>` section of your web.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="ec594-110">Name</span><span class="sxs-lookup"><span data-stu-id="ec594-110">Name</span></span>    | <span data-ttu-id="ec594-111">Valor</span><span class="sxs-lookup"><span data-stu-id="ec594-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ec594-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="ec594-112">Scope</span></span>   | <span data-ttu-id="ec594-113">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="ec594-113">Edge</span></span>        |
| <span data-ttu-id="ec594-114">Versão</span><span class="sxs-lookup"><span data-stu-id="ec594-114">Version</span></span> | <span data-ttu-id="ec594-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="ec594-115">4.6.2</span></span>       |
| <span data-ttu-id="ec594-116">Type</span><span class="sxs-lookup"><span data-stu-id="ec594-116">Type</span></span>    | <span data-ttu-id="ec594-117">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="ec594-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ec594-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ec594-118">Affected APIs</span></span>

- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)>
