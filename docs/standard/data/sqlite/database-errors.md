---
title: Erros de banco de dados
ms.date: 12/13/2019
description: Descreve como os erros e os rearos de banco de dados são tratados pela biblioteca.
ms.openlocfilehash: 9a613b6f94a89dc40e627c14f46836be77080035
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447268"
---
# <a name="database-errors"></a><span data-ttu-id="fcccd-103">Erros de banco de dados</span><span class="sxs-lookup"><span data-stu-id="fcccd-103">Database errors</span></span>

<span data-ttu-id="fcccd-104"><xref:Microsoft.Data.Sqlite.SqliteException> é gerada quando um erro do SQLite é encontrado.</span><span class="sxs-lookup"><span data-stu-id="fcccd-104"><xref:Microsoft.Data.Sqlite.SqliteException> is thrown when a SQLite error is encountered.</span></span> <span data-ttu-id="fcccd-105">A mensagem é fornecida pelo SQLite.</span><span class="sxs-lookup"><span data-stu-id="fcccd-105">The message is provided by SQLite.</span></span> <span data-ttu-id="fcccd-106">As propriedades `SqliteErrorCode` e `SqliteExtendedErrorCode` contêm o [código de resultado](https://www.sqlite.org/rescode.html) do SQLite do erro.</span><span class="sxs-lookup"><span data-stu-id="fcccd-106">The `SqliteErrorCode` and `SqliteExtendedErrorCode` properties contain the SQLite [result code](https://www.sqlite.org/rescode.html) of the error.</span></span>

<span data-ttu-id="fcccd-107">Erros podem ser encontrados sempre que o Microsoft. Data. sqlite interage com a biblioteca SQLite nativa.</span><span class="sxs-lookup"><span data-stu-id="fcccd-107">Errors may be encountered any time the Microsoft.Data.Sqlite interacts with the native SQLite library.</span></span> <span data-ttu-id="fcccd-108">A lista a seguir mostra os cenários comuns em que podem ocorrer erros:</span><span class="sxs-lookup"><span data-stu-id="fcccd-108">The following list shows the common scenarios where errors can occur:</span></span>

* <span data-ttu-id="fcccd-109">Abrindo uma conexão.</span><span class="sxs-lookup"><span data-stu-id="fcccd-109">Opening a connection.</span></span>
* <span data-ttu-id="fcccd-110">Iniciando uma transação.</span><span class="sxs-lookup"><span data-stu-id="fcccd-110">Beginning a transaction.</span></span>
* <span data-ttu-id="fcccd-111">Execução de um comando.</span><span class="sxs-lookup"><span data-stu-id="fcccd-111">Executing a command.</span></span>
* <span data-ttu-id="fcccd-112">Chamando <xref:Microsoft.Data.Sqlite.SqliteDataReader.NextResult%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcccd-112">Calling <xref:Microsoft.Data.Sqlite.SqliteDataReader.NextResult%2A>.</span></span>

<span data-ttu-id="fcccd-113">Considere atentamente como seu aplicativo tratará esses erros.</span><span class="sxs-lookup"><span data-stu-id="fcccd-113">Consider carefully how your app will handle these errors.</span></span>

## <a name="locking-retries-and-timeouts"></a><span data-ttu-id="fcccd-114">Bloqueio, novas tentativas e tempos limite</span><span class="sxs-lookup"><span data-stu-id="fcccd-114">Locking, retries, and timeouts</span></span>

<span data-ttu-id="fcccd-115">O SQLite é agressivo quando se trata de bloquear tabelas e arquivos de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="fcccd-115">SQLite is aggressive when it comes to locking tables and database files.</span></span> <span data-ttu-id="fcccd-116">Se seu aplicativo habilitar qualquer acesso simultâneo ao banco de dados, você provavelmente encontrará erros ocupados e bloqueados.</span><span class="sxs-lookup"><span data-stu-id="fcccd-116">If your app enables any concurrent database access, you'll likely encounter busy and locked errors.</span></span> <span data-ttu-id="fcccd-117">Você pode atenuar muitos erros usando um [cache compartilhado](connection-strings.md#cache) e um [log write-ahead](async.md).</span><span class="sxs-lookup"><span data-stu-id="fcccd-117">You can mitigate many errors by using a [shared cache](connection-strings.md#cache) and [write-ahead logging](async.md).</span></span>

<span data-ttu-id="fcccd-118">Sempre que o Microsoft. Data. sqlite encontrar um erro ocupado ou bloqueado, ele será automaticamente repetido até ter sucesso ou o tempo limite do comando for atingido.</span><span class="sxs-lookup"><span data-stu-id="fcccd-118">Whenever Microsoft.Data.Sqlite encounters a busy or locked error, it will automatically retry until it succeeds or the command timeout is reached.</span></span>

<span data-ttu-id="fcccd-119">Você pode aumentar o tempo limite do comando definindo <xref:Microsoft.Data.Sqlite.SqliteCommand.CommandTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcccd-119">You can increase the timeout of command by setting <xref:Microsoft.Data.Sqlite.SqliteCommand.CommandTimeout%2A>.</span></span> <span data-ttu-id="fcccd-120">O tempo limite padrão é de 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="fcccd-120">The default timeout is 30 seconds.</span></span> <span data-ttu-id="fcccd-121">Um valor de `0` significa sem tempo limite.</span><span class="sxs-lookup"><span data-stu-id="fcccd-121">A value of `0` means no timeout.</span></span>

```csharp
// Retry for 60 seconds while locked
command.CommandTimeout = 60;
```

<span data-ttu-id="fcccd-122">O Microsoft. Data. sqlite às vezes precisa criar um objeto de comando implícito.</span><span class="sxs-lookup"><span data-stu-id="fcccd-122">Microsoft.Data.Sqlite sometimes needs to create an implicit command object.</span></span> <span data-ttu-id="fcccd-123">Por exemplo, durante BeginTransaction.</span><span class="sxs-lookup"><span data-stu-id="fcccd-123">For example, during BeginTransaction.</span></span> <span data-ttu-id="fcccd-124">Para definir o tempo limite para esses comandos, use <xref:Microsoft.Data.Sqlite.SqliteConnection.DefaultTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcccd-124">To set the timeout for these commands, use <xref:Microsoft.Data.Sqlite.SqliteConnection.DefaultTimeout%2A>.</span></span>

```csharp
// Set the default timeout of all commands on this connection
connection.DefaultTimeout = 60;
```

## <a name="see-also"></a><span data-ttu-id="fcccd-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="fcccd-125">See also</span></span>

* [<span data-ttu-id="fcccd-126">Códigos de erro do SQLite</span><span class="sxs-lookup"><span data-stu-id="fcccd-126">SQLite Error Codes</span></span>](https://www.sqlite.org/rescode.html)
* [<span data-ttu-id="fcccd-127">Bloqueio de arquivo no SQLite</span><span class="sxs-lookup"><span data-stu-id="fcccd-127">File Locking In SQLite</span></span>](https://www.sqlite.org/lockingv3.html)
* [<span data-ttu-id="fcccd-128">Modo de cache compartilhado</span><span class="sxs-lookup"><span data-stu-id="fcccd-128">Shared-Cache Mode</span></span>](https://www.sqlite.org/sharedcache.html)
* [<span data-ttu-id="fcccd-129">Log write-ahead</span><span class="sxs-lookup"><span data-stu-id="fcccd-129">Write-Ahead Logging</span></span>](https://www.sqlite.org/wal.html)
