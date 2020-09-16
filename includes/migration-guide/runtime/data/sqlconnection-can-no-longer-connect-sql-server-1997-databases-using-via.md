---
ms.openlocfilehash: e65ba0edb132f5cded244a69d58e43ffea76a039
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606518"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a><span data-ttu-id="4b3ff-101">SqlConnection não pode mais se conectar ao SQL Server 1997 ou a bancos de dados usando o adaptador VIA</span><span class="sxs-lookup"><span data-stu-id="4b3ff-101">SqlConnection can no longer connect to SQL Server 1997 or databases using the VIA adapter</span></span>

#### <a name="details"></a><span data-ttu-id="4b3ff-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4b3ff-102">Details</span></span>

<span data-ttu-id="4b3ff-103">Conexões a bancos de dados do SQL Server usando o [Protocolo VIA (Virtual Interface Adapter)](/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) não têm mais suporte.</span><span class="sxs-lookup"><span data-stu-id="4b3ff-103">Connections to SQL Server databases using the [Virtual Interface Adapter (VIA) protocol](/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) are no longer supported.</span></span> <span data-ttu-id="4b3ff-104">O protocolo usado para se conectar a um banco de dados do SQL Server fica visível na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="4b3ff-104">The protocol used to connect to a SQL Server database is visible in the connection string.</span></span> <span data-ttu-id="4b3ff-105">Uma conexão VIA conterá via:&lt;nomedoservidor&gt;.</span><span class="sxs-lookup"><span data-stu-id="4b3ff-105">A VIA connection will contain via:&lt;servername&gt;.</span></span> <span data-ttu-id="4b3ff-106">Se esse aplicativo estiver se conectando ao SQL por meio de um protocolo diferente de VIA (TCP: ou NP: por exemplo), nenhuma alteração significativa será encontrada.</span><span class="sxs-lookup"><span data-stu-id="4b3ff-106">If this app is connecting to SQL via a protocol other than VIA (tcp: or np: for example), then no breaking change will be encountered.</span></span> <span data-ttu-id="4b3ff-107">Além disso, não há mais suporte para conexões com SQL Server 7 (1997).</span><span class="sxs-lookup"><span data-stu-id="4b3ff-107">Also, connections to SQL Server 7 (1997) are no longer supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4b3ff-108">Sugestão</span><span class="sxs-lookup"><span data-stu-id="4b3ff-108">Suggestion</span></span>

<span data-ttu-id="4b3ff-109">O protocolo VIA foi preterido, de modo que um protocolo alternativo deve ser usado para se conectar a bancos de dados SQL.</span><span class="sxs-lookup"><span data-stu-id="4b3ff-109">The VIA protocol is deprecated, so an alternative protocol should be used to connect to SQL databases.</span></span> <span data-ttu-id="4b3ff-110">O protocolo mais usado é o TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="4b3ff-110">The most common protocol used is TCP/IP.</span></span> <span data-ttu-id="4b3ff-111">Para obter mais informações sobre como se conectar por meio de TCP/IP, confira [Habilitar o protocolo TCP/IP para uma instância de banco de dados](/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4b3ff-111">For more information about connecting through TCP/IP, see [Enable the TCP/IP protocol for a database instance](/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)).</span></span> <span data-ttu-id="4b3ff-112">Se o banco de dados for acessado somente de dentro de uma intranet, o protocolo de pipes compartilhado poderá fornecer um melhor desempenho se a rede estiver lenta.</span><span class="sxs-lookup"><span data-stu-id="4b3ff-112">If the database is only accessed from within an intranet, the shared pipes protocol may provide better performance if the network is slow.</span></span>

| <span data-ttu-id="4b3ff-113">Name</span><span class="sxs-lookup"><span data-stu-id="4b3ff-113">Name</span></span>    | <span data-ttu-id="4b3ff-114">Valor</span><span class="sxs-lookup"><span data-stu-id="4b3ff-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4b3ff-115">Escopo</span><span class="sxs-lookup"><span data-stu-id="4b3ff-115">Scope</span></span>   |<span data-ttu-id="4b3ff-116">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="4b3ff-116">Edge</span></span>|
|<span data-ttu-id="4b3ff-117">Versão</span><span class="sxs-lookup"><span data-stu-id="4b3ff-117">Version</span></span>|<span data-ttu-id="4b3ff-118">4.5</span><span class="sxs-lookup"><span data-stu-id="4b3ff-118">4.5</span></span>|
|<span data-ttu-id="4b3ff-119">Tipo</span><span class="sxs-lookup"><span data-stu-id="4b3ff-119">Type</span></span>|<span data-ttu-id="4b3ff-120">Runtime</span><span class="sxs-lookup"><span data-stu-id="4b3ff-120">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="4b3ff-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="4b3ff-121">Affected APIs</span></span>

- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)>
- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)>

<!--

#### Affected APIs

- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String)`
- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String,System.Data.SqlClient.SqlCredential)`

-->
