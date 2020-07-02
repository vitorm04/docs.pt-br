---
ms.openlocfilehash: c7500550cd9714a9788a7dea68af04823f000f7f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614296"
---
### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a><span data-ttu-id="fdee4-101">Os rastreamentos de pilha obtidos ao usar PDBs portáteis agora incluem informações de arquivo de origem e de linha, quando solicitadas</span><span class="sxs-lookup"><span data-stu-id="fdee4-101">Stack traces obtained when using portable PDBs now include source file and line information if requested</span></span>

#### <a name="details"></a><span data-ttu-id="fdee4-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="fdee4-102">Details</span></span>

<span data-ttu-id="fdee4-103">Começando com o .NET Framework 4.7.2, os rastreamentos de pilha obtidos ao usar PDBs portáteis incluem informações de arquivo de origem e de linha, quando solicitadas.</span><span class="sxs-lookup"><span data-stu-id="fdee4-103">Starting with .NET Framework 4.7.2, stack traces obtained when using portable PDBs include source file and line information when requested.</span></span> <span data-ttu-id="fdee4-104">Nas versões anteriores do .NET Framework 4.7.2, as informações de arquivo de origem e de linha não estariam disponíveis ao usar PDBs portáteis, mesmo quando solicitadas explicitamente.</span><span class="sxs-lookup"><span data-stu-id="fdee4-104">In versions prior to .NET Framework 4.7.2, source file and line information would be unavailable when using portable PDBs even if explicitly requested.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fdee4-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="fdee4-105">Suggestion</span></span>

<span data-ttu-id="fdee4-106">Para os aplicativos direcionados ao .NET Framework 4.7.2, você pode recusar as informações de arquivo de origem e de linha ao usar PDBs portáteis, caso não as deseje, adicionando o seguinte à seção `<runtime>` do arquivo `app.config`:</span><span class="sxs-lookup"><span data-stu-id="fdee4-106">For applications that target the .NET Framework 4.7.2, you can opt out of the source file and line information when using portable PDBs if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true" />
</runtime>
```

<span data-ttu-id="fdee4-107">Para aplicativos direcionados a versões anteriores do .NET Framework mas executados no .NET Framework 4.7.2 ou posterior, você pode aceitar as informações de arquivo de origem e de linha ao usar PDBs portáteis adicionando o seguinte à seção `<runtime>` do arquivo `app.config`:</span><span class="sxs-lookup"><span data-stu-id="fdee4-107">For applications that target earlier versions of the .NET Framework but run on the .NET Framework 4.7.2 or later, you can opt in to the source file and line information when using portable PDBs by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false" />
</runtime>
```

| <span data-ttu-id="fdee4-108">Name</span><span class="sxs-lookup"><span data-stu-id="fdee4-108">Name</span></span>    | <span data-ttu-id="fdee4-109">Valor</span><span class="sxs-lookup"><span data-stu-id="fdee4-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fdee4-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="fdee4-110">Scope</span></span>   | <span data-ttu-id="fdee4-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="fdee4-111">Edge</span></span>        |
| <span data-ttu-id="fdee4-112">Versão</span><span class="sxs-lookup"><span data-stu-id="fdee4-112">Version</span></span> | <span data-ttu-id="fdee4-113">4.7.2</span><span class="sxs-lookup"><span data-stu-id="fdee4-113">4.7.2</span></span>       |
| <span data-ttu-id="fdee4-114">Type</span><span class="sxs-lookup"><span data-stu-id="fdee4-114">Type</span></span>    | <span data-ttu-id="fdee4-115">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="fdee4-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="fdee4-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="fdee4-116">Affected APIs</span></span>

- <xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)>
