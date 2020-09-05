---
ms.openlocfilehash: 8dc947f584d3433f0638a72f4db86ac2680c8dbf
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497907"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a><span data-ttu-id="70691-101">SqlConnection não pode mais se conectar ao SQL Server 1997 ou a bancos de dados usando o adaptador VIA</span><span class="sxs-lookup"><span data-stu-id="70691-101">SqlConnection can no longer connect to SQL Server 1997 or databases using the VIA adapter</span></span>

#### <a name="details"></a><span data-ttu-id="70691-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="70691-102">Details</span></span>

<span data-ttu-id="70691-103">Conexões a bancos de dados do SQL Server usando o [Protocolo VIA (Virtual Interface Adapter)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) não têm mais suporte.</span><span class="sxs-lookup"><span data-stu-id="70691-103">Connections to SQL Server databases using the [Virtual Interface Adapter (VIA) protocol](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) are no longer supported.</span></span> <span data-ttu-id="70691-104">O protocolo usado para se conectar a um banco de dados do SQL Server fica visível na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="70691-104">The protocol used to connect to a SQL Server database is visible in the connection string.</span></span> <span data-ttu-id="70691-105">Uma conexão VIA conterá via:&lt;nomedoservidor&gt;.</span><span class="sxs-lookup"><span data-stu-id="70691-105">A VIA connection will contain via:&lt;servername&gt;.</span></span> <span data-ttu-id="70691-106">Se esse aplicativo estiver se conectando ao SQL por meio de um protocolo diferente de VIA (TCP: ou NP: por exemplo), nenhuma alteração significativa será encontrada.</span><span class="sxs-lookup"><span data-stu-id="70691-106">If this app is connecting to SQL via a protocol other than VIA (tcp: or np: for example), then no breaking change will be encountered.</span></span> <span data-ttu-id="70691-107">Além disso, não há mais suporte para conexões com SQL Server 7 (1997).</span><span class="sxs-lookup"><span data-stu-id="70691-107">Also, connections to SQL Server 7 (1997) are no longer supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="70691-108">Sugestão</span><span class="sxs-lookup"><span data-stu-id="70691-108">Suggestion</span></span>

<span data-ttu-id="70691-109">O protocolo VIA foi preterido, de modo que um protocolo alternativo deve ser usado para se conectar a bancos de dados SQL.</span><span class="sxs-lookup"><span data-stu-id="70691-109">The VIA protocol is deprecated, so an alternative protocol should be used to connect to SQL databases.</span></span> <span data-ttu-id="70691-110">O protocolo mais usado é o TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="70691-110">The most common protocol used is TCP/IP.</span></span> <span data-ttu-id="70691-111">Para obter mais informações sobre como se conectar por meio de TCP/IP, confira [Habilitar o protocolo TCP/IP para uma instância de banco de dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="70691-111">For more information about connecting through TCP/IP, see [Enable the TCP/IP protocol for a database instance](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)).</span></span> <span data-ttu-id="70691-112">Se o banco de dados for acessado somente de dentro de uma intranet, o protocolo de pipes compartilhado poderá fornecer um melhor desempenho se a rede estiver lenta.</span><span class="sxs-lookup"><span data-stu-id="70691-112">If the database is only accessed from within an intranet, the shared pipes protocol may provide better performance if the network is slow.</span></span>

| <span data-ttu-id="70691-113">Nome</span><span class="sxs-lookup"><span data-stu-id="70691-113">Name</span></span>    | <span data-ttu-id="70691-114">Valor</span><span class="sxs-lookup"><span data-stu-id="70691-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="70691-115">Escopo</span><span class="sxs-lookup"><span data-stu-id="70691-115">Scope</span></span>   |<span data-ttu-id="70691-116">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="70691-116">Edge</span></span>|
|<span data-ttu-id="70691-117">Versão</span><span class="sxs-lookup"><span data-stu-id="70691-117">Version</span></span>|<span data-ttu-id="70691-118">4.5</span><span class="sxs-lookup"><span data-stu-id="70691-118">4.5</span></span>|
|<span data-ttu-id="70691-119">Tipo</span><span class="sxs-lookup"><span data-stu-id="70691-119">Type</span></span>|<span data-ttu-id="70691-120">Runtime</span><span class="sxs-lookup"><span data-stu-id="70691-120">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="70691-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="70691-121">Affected APIs</span></span>

- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)>
- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)>

<!--

#### Affected APIs

- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String)`
- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String,System.Data.SqlClient.SqlCredential)`

-->
