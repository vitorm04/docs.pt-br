---
ms.openlocfilehash: a133c2ea48df11915f8708029c70549e8a1ccefd
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497906"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="68b82-101">Janelas do WPF são renderizadas sem distorção ao se estender para fora de um único monitor</span><span class="sxs-lookup"><span data-stu-id="68b82-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

#### <a name="details"></a><span data-ttu-id="68b82-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="68b82-102">Details</span></span>

<span data-ttu-id="68b82-103">No .NET Framework 4.6 em execução no Windows 8 e superior, a janela inteira é renderizada sem distorção quando ela se estende para fora da exibição única em um cenário de vários monitores.</span><span class="sxs-lookup"><span data-stu-id="68b82-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="68b82-104">Isso é diferente de versões anteriores do .NET Framework, que distorceriam janelas do WPF que se estendiam para fora de uma única exibição.</span><span class="sxs-lookup"><span data-stu-id="68b82-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="68b82-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="68b82-105">Suggestion</span></span>

<span data-ttu-id="68b82-106">Esse comportamento (com distorção ou não) pode ser definido explicitamente usando o elemento <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> em <code>&lt;appSettings&gt;</code> no arquivo de configuração do aplicativo ou definindo a propriedade <code>EnableMultiMonitorDisplayClipping</code> durante a inicialização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="68b82-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>

| <span data-ttu-id="68b82-107">Nome</span><span class="sxs-lookup"><span data-stu-id="68b82-107">Name</span></span>    | <span data-ttu-id="68b82-108">Valor</span><span class="sxs-lookup"><span data-stu-id="68b82-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="68b82-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="68b82-109">Scope</span></span>   |<span data-ttu-id="68b82-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="68b82-110">Minor</span></span>|
|<span data-ttu-id="68b82-111">Versão</span><span class="sxs-lookup"><span data-stu-id="68b82-111">Version</span></span>|<span data-ttu-id="68b82-112">4.6</span><span class="sxs-lookup"><span data-stu-id="68b82-112">4.6</span></span>|
|<span data-ttu-id="68b82-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="68b82-113">Type</span></span>|<span data-ttu-id="68b82-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="68b82-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="68b82-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="68b82-115">Affected APIs</span></span>

<span data-ttu-id="68b82-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="68b82-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
