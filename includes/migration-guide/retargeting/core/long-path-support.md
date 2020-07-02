---
ms.openlocfilehash: 67e3ff5000ebd38064ed8a57e4fe561afa31f8d8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614282"
---
### <a name="long-path-support"></a><span data-ttu-id="7d58b-101">Suporte a caminho longo</span><span class="sxs-lookup"><span data-stu-id="7d58b-101">Long path support</span></span>

#### <a name="details"></a><span data-ttu-id="7d58b-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7d58b-102">Details</span></span>

<span data-ttu-id="7d58b-103">A partir dos aplicativos destinados ao .NET Framework 4.6.2, caminhos longos (de até 32K caracteres) têm suporte e a limitação de 260 caracteres (ou `MAX_PATH`) para o tamanho dos caminhos foi removida. Para aplicativos recompilados para serem destinados ao .NET Framework 4.6.2, os caminhos de código que lançavam um <xref:System.IO.PathTooLongException?displayProperty=fullName> porque um caminho ultrapassava 260 caracteres agora lançam um <xref:System.IO.PathTooLongException?displayProperty=fullName> apenas sob as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="7d58b-103">Starting with apps that target the .NET Framework 4.6.2, long paths (of up to 32K characters) are supported, and the 260-character (or `MAX_PATH`) limitation on path lengths has been removed.For apps that are recompiled to target the .NET Framework 4.6.2, code paths that previously threw a <xref:System.IO.PathTooLongException?displayProperty=fullName> because a path exceeded 260 characters will now throw a <xref:System.IO.PathTooLongException?displayProperty=fullName> only under the following conditions:</span></span>

- <span data-ttu-id="7d58b-104">O tamanho do caminho é superior a <xref:System.Int16.MaxValue> (32.767) caracteres.</span><span class="sxs-lookup"><span data-stu-id="7d58b-104">The length of the path is greater than <xref:System.Int16.MaxValue> (32,767) characters.</span></span>
- <span data-ttu-id="7d58b-105">O sistema operacional retorna `COR_E_PATHTOOLONG` ou seu equivalente.</span><span class="sxs-lookup"><span data-stu-id="7d58b-105">The operating system returns `COR_E_PATHTOOLONG` or its equivalent.</span></span>
<span data-ttu-id="7d58b-106">Para aplicativos destinados ao .NET Framework 4.6.1 e versões anteriores, a runtime gera automaticamente um <xref:System.IO.PathTooLongException?displayProperty=fullName> sempre que um caminho ultrapassa 260 caracteres.</span><span class="sxs-lookup"><span data-stu-id="7d58b-106">For apps that target the .NET Framework 4.6.1 and earlier versions, the runtime automatically throws a <xref:System.IO.PathTooLongException?displayProperty=fullName> whenever a path exceeds 260 characters.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7d58b-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="7d58b-107">Suggestion</span></span>

<span data-ttu-id="7d58b-108">Para aplicativos destinados ao .NET Framework 4.6.2, é possível recusar o suporte para caminhos longos se ele não for desejável adicionando o seguinte à seção `<runtime>` do arquivo `app.config`:</span><span class="sxs-lookup"><span data-stu-id="7d58b-108">For apps that target the .NET Framework 4.6.2, you can opt out of long path support if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />
</runtime>
```

<span data-ttu-id="7d58b-109">Para aplicativos destinados a versões anteriores do .NET Framework mas executados no .NET Framework 4.6.2 ou posterior, é possível aceitar o suporte para caminhos longos adicionando o seguinte à seção `<runtime>` do arquivo `app.config`:</span><span class="sxs-lookup"><span data-stu-id="7d58b-109">For apps that target earlier versions of the .NET Framework but run on the .NET Framework 4.6.2 or later, you can opt in to long path support by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />
</runtime>
```

| <span data-ttu-id="7d58b-110">Name</span><span class="sxs-lookup"><span data-stu-id="7d58b-110">Name</span></span>    | <span data-ttu-id="7d58b-111">Valor</span><span class="sxs-lookup"><span data-stu-id="7d58b-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7d58b-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="7d58b-112">Scope</span></span>   | <span data-ttu-id="7d58b-113">Secundária</span><span class="sxs-lookup"><span data-stu-id="7d58b-113">Minor</span></span>       |
| <span data-ttu-id="7d58b-114">Versão</span><span class="sxs-lookup"><span data-stu-id="7d58b-114">Version</span></span> | <span data-ttu-id="7d58b-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="7d58b-115">4.6.2</span></span>       |
| <span data-ttu-id="7d58b-116">Type</span><span class="sxs-lookup"><span data-stu-id="7d58b-116">Type</span></span>    | <span data-ttu-id="7d58b-117">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="7d58b-117">Retargeting</span></span> |
