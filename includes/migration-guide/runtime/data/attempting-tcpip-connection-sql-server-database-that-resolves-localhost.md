---
ms.openlocfilehash: 87cb2570d3d47a2acb85b5557141c0fef885516a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621764"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a><span data-ttu-id="2bcde-101">Falha ao tentar uma conexão TCP/IP com um banco de dados do SQL Server resolvida para `localhost`</span><span class="sxs-lookup"><span data-stu-id="2bcde-101">Attempting a TCP/IP connection to a SQL Server database that resolves to `localhost` fails</span></span>

#### <a name="details"></a><span data-ttu-id="2bcde-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2bcde-102">Details</span></span>

<span data-ttu-id="2bcde-103">No .NET Framework 4.6 e 4.6.1, tentar uma conexão TCP/IP com um banco de dados do SQL Server resolvida para <code>localhost</code> falha com o erro &quot;Ocorreu um erro relacionado à rede ou específico da instância durante o estabelecimento de uma conexão com o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2bcde-103">In the .NET Framework 4.6 and 4.6.1, attempting a TCP/IP connection to a SQL Server database that resolves to <code>localhost</code> fails with the error, &quot;A network-related or instance-specific error occurred while establishing a connection to SQL Server.</span></span> <span data-ttu-id="2bcde-104">O servidor não foi encontrado ou não estava acessível.</span><span class="sxs-lookup"><span data-stu-id="2bcde-104">The server was not found or was not accessible.</span></span> <span data-ttu-id="2bcde-105">Verifique se o nome de instância está correto e se o SQL Server está configurado para permitir conexões remotas.</span><span class="sxs-lookup"><span data-stu-id="2bcde-105">Verify that the instance name is correct and that SQL Server is configured to allow remote connections.</span></span> <span data-ttu-id="2bcde-106">(provedor: Adaptadores de Rede do SQL, erro: 26 – Erro ao Localizar Servidor/Instância Especificada)&quot;</span><span class="sxs-lookup"><span data-stu-id="2bcde-106">(provider: SQL Network Interfaces, error: 26 - Error Locating Server/Instance Specified)&quot;</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2bcde-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="2bcde-107">Suggestion</span></span>

<span data-ttu-id="2bcde-108">Esse problema foi resolvido e o comportamento anterior restaurado no .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="2bcde-108">This issue has been addressed and the previous behavior restored in the .NET Framework 4.6.2.</span></span> <span data-ttu-id="2bcde-109">Para se conectar a um banco de dados do SQL Server que seja resolvido para <code>localhost</code>, faça a atualização para o .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="2bcde-109">To connect to a SQL Server database that resolves to <code>localhost</code>, upgrade to the .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="2bcde-110">Name</span><span class="sxs-lookup"><span data-stu-id="2bcde-110">Name</span></span>    | <span data-ttu-id="2bcde-111">Valor</span><span class="sxs-lookup"><span data-stu-id="2bcde-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2bcde-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="2bcde-112">Scope</span></span>   |<span data-ttu-id="2bcde-113">Secundária</span><span class="sxs-lookup"><span data-stu-id="2bcde-113">Minor</span></span>|
|<span data-ttu-id="2bcde-114">Versão</span><span class="sxs-lookup"><span data-stu-id="2bcde-114">Version</span></span>|<span data-ttu-id="2bcde-115">4.6</span><span class="sxs-lookup"><span data-stu-id="2bcde-115">4.6</span></span>|
|<span data-ttu-id="2bcde-116">Type</span><span class="sxs-lookup"><span data-stu-id="2bcde-116">Type</span></span>|<span data-ttu-id="2bcde-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="2bcde-117">Runtime</span></span>|
