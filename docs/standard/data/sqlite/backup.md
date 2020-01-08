---
title: Backup online
ms.date: 12/13/2019
description: Saiba como usar o recurso de backup online do SQLite.
ms.openlocfilehash: 885aa2c5555b58deb2551c0a4e6933742a093457
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447093"
---
# <a name="online-backup"></a><span data-ttu-id="f93ee-103">Backup online</span><span class="sxs-lookup"><span data-stu-id="f93ee-103">Online backup</span></span>

<span data-ttu-id="f93ee-104">O SQLite pode fazer backup de arquivos de banco de dados enquanto o aplicativo está em execução.</span><span class="sxs-lookup"><span data-stu-id="f93ee-104">SQLite can back up database files while the app is running.</span></span> <span data-ttu-id="f93ee-105">Essa funcionalidade está disponível em Microsoft. Data. SQLite como o método <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> em `SqliteConnection`.</span><span class="sxs-lookup"><span data-stu-id="f93ee-105">This functionality is available in Microsoft.Data.Sqlite as the <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> method on `SqliteConnection`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

<span data-ttu-id="f93ee-106">Atualmente, `BackupDatabase` fará o backup do banco de dados o mais rápido possível e bloqueará a gravação de outras conexões no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f93ee-106">Currently, `BackupDatabase` will back up the database as quickly as possible and blocks other connections from writing to the database.</span></span> <span data-ttu-id="f93ee-107">O problema [#13834](https://github.com/aspnet/EntityFrameworkCore/issues/13834) forneceria uma API alternativa para fazer backup do banco de dados em segundo plano e permitir que outras conexões interrompam o backup e gravem no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f93ee-107">Issue [#13834](https://github.com/aspnet/EntityFrameworkCore/issues/13834) would provide an alternative API to back up the database in the background and allow other connections to interrupt the backup and write to the database.</span></span> <span data-ttu-id="f93ee-108">Se você estiver interessado, forneça comentários sobre o problema.</span><span class="sxs-lookup"><span data-stu-id="f93ee-108">If you're interested, provide feedback on the issue.</span></span>
