---
title: Backup online
ms.date: 12/13/2019
description: Saiba como usar o recurso de backup online do SQLite.
ms.openlocfilehash: d857dcb69f2b2d10b034a0abf222b30c2e20bb41
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901279"
---
# <a name="online-backup"></a>Backup online

O SQLite pode fazer backup de arquivos de banco de dados enquanto o aplicativo está em execução. Essa funcionalidade está disponível em Microsoft. Data. SQLite como o <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> método em `SqliteConnection`.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

No momento `BackupDatabase` , o fará backup do banco de dados o mais rápido possível e bloqueará a gravação de outras conexões no banco de dados. O problema [#13834](https://github.com/dotnet/efcore/issues/13834) forneceria uma API alternativa para fazer backup do banco de dados em segundo plano e permitir que outras conexões interrompam o backup e gravem no banco de dados. Se você estiver interessado, forneça comentários sobre o problema.
