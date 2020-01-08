---
title: Extensões do
ms.date: 12/13/2019
description: Saiba como carregar extensões do SQLite.
ms.openlocfilehash: ab00ccf31b8a22407fc177c18149fe4825a19091
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447254"
---
# <a name="extensions"></a>Extensões do

O SQLite dá suporte ao carregamento de extensões em tempo de execução. As extensões incluem itens como funções SQL adicionais, agrupamentos, tabelas virtuais e muito mais.

O .NET Core inclui lógica adicional para a localização de bibliotecas nativas em locais adicionais, como pacotes NuGet referenciados. Infelizmente, o SQLite não pode aproveitar essa lógica; Ele chama a API da plataforma diretamente para carregar bibliotecas. Por isso, seu aplicativo pode precisar modificar o caminho, LD_LIBRARY_PATH ou DYLD_LIBRARY_PATH variáveis de ambiente antes de carregar as extensões do SQLite. Há [um exemplo](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) no GitHub que demonstra a localização de binários para o tempo de execução atual dentro de um pacote NuGet referenciado.

Para carregar uma extensão, chame o método <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A>. Microsoft. Data. sqlite garantirá que a extensão permaneça carregada mesmo se a conexão for fechada e reaberta.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a>Veja também

* [Extensões carregáveis de tempo de execução](https://www.sqlite.org/loadext.html)
