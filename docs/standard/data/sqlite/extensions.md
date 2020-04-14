---
title: Extensões
ms.date: 12/13/2019
description: Aprenda a carregar extensões SQLite.
ms.openlocfilehash: 51c705349c25240fe42e0edda8004a3e3b013ca3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242953"
---
# <a name="extensions"></a>Extensões

O SQLite suporta extensões de carregamento em tempo de execução. As extensões incluem coisas como funções SQL adicionais, colagens, tabelas virtuais e muito mais.

O .NET Core inclui lógica adicional para localizar bibliotecas nativas em lugares adicionais, como pacotes NuGet referenciados. Infelizmente, o SQLite não pode aproveitar essa lógica; ele chama a API da plataforma diretamente para carregar bibliotecas. Por causa disso, você pode precisar modificar as variáveis de ambiente PATH, LD_LIBRARY_PATH ou DYLD_LIBRARY_PATH antes de carregar extensões SQLite. Há [uma amostra](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) no GitHub que demonstra encontrar binários para o tempo de execução atual dentro de um pacote NuGet referenciado.

Para carregar uma extensão, ligue para o <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> método. O Microsoft.Data.Sqlite garantirá que a extensão permaneça carregada mesmo que a conexão seja fechada e reaberta.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a>Confira também

* [Extensões carregáveis em tempo de execução](https://www.sqlite.org/loadext.html)
