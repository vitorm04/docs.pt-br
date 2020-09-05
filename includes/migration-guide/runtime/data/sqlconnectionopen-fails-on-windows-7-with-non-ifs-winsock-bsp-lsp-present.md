---
ms.openlocfilehash: 9ab1686f60bcdbfef5f18576be17aee8c931f9aa
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496396"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a><span data-ttu-id="544fe-101">SqlConnection.Open falha no Windows 7 com BSP ou LSP Winsock não IFS presente</span><span class="sxs-lookup"><span data-stu-id="544fe-101">SqlConnection.Open fails on Windows 7 with non-IFS Winsock BSP or LSP present</span></span>

#### <a name="details"></a><span data-ttu-id="544fe-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="544fe-102">Details</span></span>

<span data-ttu-id="544fe-103"><xref:System.Data.SqlClient.SqlConnection.Open> e <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> falharão no .NET Framework 4.5 se forem executados em um computador com Windows 7 sem a presença de um BSP ou LSP não IFS Winsock. Para determinar se um BSP ou LSP não IFS está instalado, use o comando <code>netsh WinSock Show Catalog</code> e analise cada item <code>Winsock Catalog Provider Entry</code> retornado.</span><span class="sxs-lookup"><span data-stu-id="544fe-103"><xref:System.Data.SqlClient.SqlConnection.Open> and <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> fail in the .NET Framework 4.5 if running on a Windows 7 machine with a non-IFS Winsock BSP or LSP are present on the computer.To determine whether a non-IFS BSP or LSP is installed, use the <code>netsh WinSock Show Catalog</code> command, and examine every <code>Winsock Catalog Provider Entry</code> item that is returned.</span></span> <span data-ttu-id="544fe-104">Se o valor de Sinalizadores de Serviço tiver o bit <code>0x20000</code> definido, o provedor usará os identificadores do IFS e funcionará corretamente.</span><span class="sxs-lookup"><span data-stu-id="544fe-104">If the Service Flags value has the <code>0x20000</code> bit set, the provider uses IFS handles and will work correctly.</span></span> <span data-ttu-id="544fe-105">Se o bit <code>0x20000</code> estiver limpo (não definido), trata-se de um BSP ou LSP não IFS.</span><span class="sxs-lookup"><span data-stu-id="544fe-105">If the <code>0x20000</code> bit is clear (not set), it is a non-IFS BSP or LSP.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="544fe-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="544fe-106">Suggestion</span></span>

<span data-ttu-id="544fe-107">Esse bug foi corrigido no .NET Framework 4.5.2, portanto, ele pode ser evitado com a atualização do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="544fe-107">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="544fe-108">Como alternativa, ele pode ser evitado com a remoção de qualquer LSP Winsock não IFS instalado.</span><span class="sxs-lookup"><span data-stu-id="544fe-108">Alternatively, it can be avoided by removing any installed non-IFS Winsock LSPs.</span></span>

| <span data-ttu-id="544fe-109">Nome</span><span class="sxs-lookup"><span data-stu-id="544fe-109">Name</span></span>    | <span data-ttu-id="544fe-110">Valor</span><span class="sxs-lookup"><span data-stu-id="544fe-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="544fe-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="544fe-111">Scope</span></span>   |<span data-ttu-id="544fe-112">Secundária</span><span class="sxs-lookup"><span data-stu-id="544fe-112">Minor</span></span>|
|<span data-ttu-id="544fe-113">Versão</span><span class="sxs-lookup"><span data-stu-id="544fe-113">Version</span></span>|<span data-ttu-id="544fe-114">4.5</span><span class="sxs-lookup"><span data-stu-id="544fe-114">4.5</span></span>|
|<span data-ttu-id="544fe-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="544fe-115">Type</span></span>|<span data-ttu-id="544fe-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="544fe-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="544fe-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="544fe-117">Affected APIs</span></span>

- <xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Data.SqlClient.SqlConnection.Open`
- `M:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)`

-->
