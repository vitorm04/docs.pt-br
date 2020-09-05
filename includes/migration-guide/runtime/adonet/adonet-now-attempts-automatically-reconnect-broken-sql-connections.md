---
ms.openlocfilehash: 7f7e718d543a4abdf2b8a87e52d8c0e2ba28203f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496488"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a><span data-ttu-id="cc0bf-101">Agora, ADO.NET tentará reconectar automaticamente conexões SQL interrompidas</span><span class="sxs-lookup"><span data-stu-id="cc0bf-101">ADO.NET now attempts to automatically reconnect broken SQL connections</span></span>

#### <a name="details"></a><span data-ttu-id="cc0bf-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="cc0bf-102">Details</span></span>

<span data-ttu-id="cc0bf-103">A partir do .NET Framework 4.5.1, o .NET Framework tentará reconectar automaticamente conexões SQL interrompidas.</span><span class="sxs-lookup"><span data-stu-id="cc0bf-103">Beginning in the .NET Framework 4.5.1, the .NET Framework will attempt to automatically reconnect broken SQL connections.</span></span> <span data-ttu-id="cc0bf-104">Embora, normalmente, isso torne os aplicativos mais confiáveis, há casos de borda em que um aplicativo precisa saber que a conexão foi perdida para tomar medidas sobre a reconexão.</span><span class="sxs-lookup"><span data-stu-id="cc0bf-104">Although this will typically make apps more reliable, there are edge cases in which an app needs to know that the connection was lost so that it can take some action upon reconnection.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cc0bf-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="cc0bf-105">Suggestion</span></span>

<span data-ttu-id="cc0bf-106">Se esse recurso for indesejável devido a preocupações de compatibilidade, ele poderá ser desabilitado por meio da configuração da propriedade <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> de uma cadeia de conexão (ou <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) para 0.</span><span class="sxs-lookup"><span data-stu-id="cc0bf-106">If this feature is undesirable due to compatibility concerns, it can be disabled by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> property of a connection string (or <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) to 0.</span></span>

| <span data-ttu-id="cc0bf-107">Nome</span><span class="sxs-lookup"><span data-stu-id="cc0bf-107">Name</span></span>    | <span data-ttu-id="cc0bf-108">Valor</span><span class="sxs-lookup"><span data-stu-id="cc0bf-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cc0bf-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="cc0bf-109">Scope</span></span>   |<span data-ttu-id="cc0bf-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="cc0bf-110">Edge</span></span>|
|<span data-ttu-id="cc0bf-111">Versão</span><span class="sxs-lookup"><span data-stu-id="cc0bf-111">Version</span></span>|<span data-ttu-id="cc0bf-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="cc0bf-112">4.5.1</span></span>|
|<span data-ttu-id="cc0bf-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="cc0bf-113">Type</span></span>|<span data-ttu-id="cc0bf-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="cc0bf-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="cc0bf-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="cc0bf-115">Affected APIs</span></span>

- <xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType>
- <xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType>
- <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType>
- <xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor>
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)>
- <xref:System.Data.Common.DbConnectionStringBuilder.%23ctor>
- <xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)>

<!--

#### Affected APIs

- `P:System.Data.IDbConnection.ConnectionString`
- `P:System.Data.SqlClient.SqlConnection.ConnectionString`
- `P:System.Configuration.ConnectionStringSettings.ConnectionString`
- `P:System.Data.Common.DbConnection.ConnectionString`
- `P:System.Data.Common.DbConnectionStringBuilder.ConnectionString`
- `M:System.Data.SqlClient.SqlConnectionStringBuilder.#ctor`
- `M:System.Data.SqlClient.SqlConnectionStringBuilder.#ctor(System.String)`
- `M:System.Data.Common.DbConnectionStringBuilder.#ctor`
- `M:System.Data.Common.DbConnectionStringBuilder.#ctor(System.Boolean)`

-->
