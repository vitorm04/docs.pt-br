---
ms.openlocfilehash: 9c9c4ec55143ef991e9b69a389e0f3368263bb4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614303"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a><span data-ttu-id="b4013-101">NullReferenceException no código de tratamento de exceções de ImageSourceConverter.ConvertFrom</span><span class="sxs-lookup"><span data-stu-id="b4013-101">NullReferenceException in exception handling code from ImageSourceConverter.ConvertFrom</span></span>

#### <a name="details"></a><span data-ttu-id="b4013-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="b4013-102">Details</span></span>

<span data-ttu-id="b4013-103">Um erro no código de manipulação de exceções para <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> fez um <xref:System.NullReferenceException?displayProperty=fullName> incorreto ser gerado, em vez da exceção pretendida (<xref:System.IO.DirectoryNotFoundException?displayProperty=fullName> ou <xref:System.IO.FileNotFoundException?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="b4013-103">An error in the exception handling code for <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> caused an incorrect <xref:System.NullReferenceException?displayProperty=fullName> to be thrown instead of the intended exception ( <xref:System.IO.DirectoryNotFoundException?displayProperty=fullName> or <xref:System.IO.FileNotFoundException?displayProperty=fullName>).</span></span> <span data-ttu-id="b4013-104">Essa alteração corrige esse erro, de modo que o método agora gera a exceção certa.</span><span class="sxs-lookup"><span data-stu-id="b4013-104">This change corrects that error so that the method now throws the right exception.</span></span> <p/><span data-ttu-id="b4013-105">Por padrão todos os aplicativos direcionados ao .NET Framework 4.6.2 e anteriores continuam a gerar <xref:System.NullReferenceException?displayProperty=fullName> para manter a compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="b4013-105">By default all applications targeting .NET Framework 4.6.2 and earlier continue to throw <xref:System.NullReferenceException?displayProperty=fullName> for compatibility.</span></span> <span data-ttu-id="b4013-106">Os desenvolvedores que direcionarem ao .NET Framework 4.7 e superiores, observação as exceções certas.</span><span class="sxs-lookup"><span data-stu-id="b4013-106">Developers targeting .NET Framework 4.7 and above should see the right exceptions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b4013-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="b4013-107">Suggestion</span></span>

<span data-ttu-id="b4013-108">Os desenvolvedores que desejam reverter para receber <xref:System.NullReferenceException?displayProperty=fullName> quando tiverem o .NET Framework 4.7 ou mais recentes como destino podem adicionar/mesclar o seguinte ao arquivo App.config do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="b4013-108">Developers who wish to revert to getting <xref:System.NullReferenceException?displayProperty=fullName> when targeting .NET Framework 4.7 or later can add/merge the following to their application's App.config file:</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="b4013-109">Name</span><span class="sxs-lookup"><span data-stu-id="b4013-109">Name</span></span>    | <span data-ttu-id="b4013-110">Valor</span><span class="sxs-lookup"><span data-stu-id="b4013-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b4013-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="b4013-111">Scope</span></span>   | <span data-ttu-id="b4013-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="b4013-112">Edge</span></span>        |
| <span data-ttu-id="b4013-113">Versão</span><span class="sxs-lookup"><span data-stu-id="b4013-113">Version</span></span> | <span data-ttu-id="b4013-114">4.7</span><span class="sxs-lookup"><span data-stu-id="b4013-114">4.7</span></span>         |
| <span data-ttu-id="b4013-115">Type</span><span class="sxs-lookup"><span data-stu-id="b4013-115">Type</span></span>    | <span data-ttu-id="b4013-116">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="b4013-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="b4013-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b4013-117">Affected APIs</span></span>

- <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType>
