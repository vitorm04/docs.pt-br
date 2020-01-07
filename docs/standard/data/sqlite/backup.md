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
# <a name="online-backup"></a>Backup online

O SQLite pode fazer backup de arquivos de banco de dados enquanto o aplicativo está em execução. Essa funcionalidade está disponível em Microsoft. Data. SQLite como o método <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> em `SqliteConnection`.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

Atualmente, `BackupDatabase` fará o backup do banco de dados o mais rápido possível e bloqueará a gravação de outras conexões no banco de dados. O problema [#13834](https://github.com/aspnet/EntityFrameworkCore/issues/13834) forneceria uma API alternativa para fazer backup do banco de dados em segundo plano e permitir que outras conexões interrompam o backup e gravem no banco de dados. Se você estiver interessado, forneça comentários sobre o problema.
