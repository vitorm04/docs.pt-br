---
title: Comparação com System. Data. SQLite
ms.date: 12/13/2019
description: Descreve algumas das diferenças entre as bibliotecas Microsoft. Data. SQLite e System. Data. SQLite.
ms.openlocfilehash: dee90c132b108f2c876c0d8becc1b02035a47b61
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447016"
---
# <a name="comparison-to-systemdatasqlite"></a>Comparação com System. Data. SQLite

Em 2005, Robert Simpson criou System. Data. SQLite, um provedor SQLite para ADO.NET 2,0. Em 2010, a equipe do SQLite assumiu a manutenção e o desenvolvimento do projeto. Também vale a pena observar que a equipe mono forku o código em 2007 como mono. Data. sqlite. System. Data. SQLite tem um longo histórico e evoluiu para um provedor de ADO.NET estável e completo com recursos completos com ferramentas do Visual Studio. Novas versões continuam a fornecer assemblies compatíveis com cada versão do .NET Framework de volta para a versão 2,0 e até mesmo .NET Compact Framework 3,5.

A primeira versão do .NET Core (lançada em 2016) era uma implementação única, leve, moderna e entre plataformas do .NET. APIs e APIs obsoletas com alternativas mais modernas foram removidas intencionalmente. ADO.NET não incluía nenhuma das APIs do conjunto de um (incluindo DataTable e DataAdapter).

A equipe de Entity Framework foi um tanto familiar com a base de código System. Data. SQLite. Brice Lambson, membro da equipe do EF, já ajudou a equipe do SQLite a adicionar suporte para Entity Framework versões 5 e 6. O Brice também estava experimentando sua própria implementação de um provedor de ADO.NET do SQLite ao mesmo tempo em que o .NET Core estava sendo planejado. Após uma longa discussão, a equipe de Entity Framework decidiu criar o Microsoft. Data. sqlite com base no protótipo do Brice. Isso permitiria que eles criassem uma nova implementação leve e moderna que se alinharia com as metas do .NET Core.

Como exemplo do que queremos dizer mais moderno, aqui está o código para criar uma [função definida pelo usuário](user-defined-functions.md) em System. Data. SQLite e Microsoft. Data. sqlite.

```csharp
// System.Data.SQLite
connection.BindFunction(
    new SQLiteFunctionAttribute("ceiling", 1, FunctionType.Scalar),
    (Func<object[], object>)((object[] args) => Math.Ceiling((double)((object[])args[1])[0])),
    null);

// Microsoft.Data.Sqlite
connection.CreateFunction(
    "ceiling",
    (double arg) => Math.Ceiling(arg));
```

Em 2017, o .NET Core 2,0 sofreu uma mudança na estratégia. Foi decidido que a compatibilidade com .NET Framework era vital para o sucesso do .NET Core. Muitas das APIs removidas, incluindo as APIs de DataSet, foram adicionadas de volta. Como fazia para muitos outros, esse System. Data. SQLite desbloqueado, permitindo que ele também seja transportado para o .NET Core. O objetivo original do Microsoft. Data. sqlite ser leve e moderno, no entanto, ainda permanece. Consulte [limitações do ADO.net](adonet-limitations.md) para obter detalhes sobre as APIs do ADO.net não implementadas pelo Microsoft. Data. sqlite.

Quando novos recursos são adicionados ao Microsoft. Data. sqlite, o design de System. Data. SQLite é levado em conta. Podemos tentar, quando possível, minimizar as alterações entre as duas para facilitar a transição entre elas.

## <a name="data-types"></a>Tipos de dados

A maior diferença entre Microsoft. Data. SQLite e System. Data. SQLite é como os tipos de dados são tratados. Conforme descrito em [tipos de dados](types.md), o Microsoft. Data. sqlite não tenta ocultar a peculiaridade subjacente do SQLite, que permite que qualquer cadeia de caracteres arbitrária seja especificada como o tipo de coluna e tenha apenas quatro tipos primitivos: Integer, real, Text e BLOB.

System. Data. SQLite aplica semântica adicional a tipos de coluna que os mapeiam diretamente para tipos .NET. Isso dá ao provedor uma sensação mais fortemente tipada, mas tem algumas bordas aproximadas. Por exemplo, eles tinham que introduzir uma nova instrução SQL (tipos) para especificar os tipos de coluna de expressões em instruções SELECT.

## <a name="connection-strings"></a>Cadeias de conexão

Microsoft. Data. sqlite tem muito menos palavras-chave de [cadeia de conexão](connection-strings.md) . A tabela a seguir mostra alternativas que podem ser usadas em seu lugar.

| Palavra-chave          | Alternativa                                         |
| ---------------- | --------------------------------------------------- |
| Tamanho do Cache       | Enviar `PRAGMA cache_size = <pages>`                  |
| Tempo limite padrão  | Use a propriedade defaultTimeout em SqliteConnection |
| FailIfMissing    | Use `Mode=ReadWrite`.                                |
| FullUri          | Usar a palavra-chave de fonte de dados                         |
| Modo de diário     | Enviar `PRAGMA journal_mode = <mode>`                 |
| Formato herdado    | Enviar `PRAGMA legacy_file_format = 1`                |
| Contagem máxima de páginas   | Enviar `PRAGMA max_page_count = <pages>`              |
| Tamanho da Página        | Enviar `PRAGMA page_size = <bytes>`                   |
| Somente Leitura        | Use `Mode=ReadOnly`.                                 |
| Synchronous      | Enviar `PRAGMA synchronous = <mode>`                  |
| URI              | Usar a palavra-chave de fonte de dados                         |
| UseUTF16Encoding | Enviar `PRAGMA encoding = 'UTF-16'`                   |

## <a name="authorization"></a>Autorização

Microsoft. Data. sqlite não tem nenhuma API expondo o retorno de chamada de autorização do SQLite. Use o problema [#13835](https://github.com/aspnet/EntityFrameworkCore/issues/13835) para fornecer comentários sobre esse recurso.

## <a name="data-change-notifications"></a>Notificações de alteração de dados

Microsoft. Data. sqlite não tem nenhuma API expondo as notificações de alteração de dados do SQLite. Use o problema [#13827](https://github.com/aspnet/EntityFrameworkCore/issues/13827) para fornecer comentários sobre esse recurso.

## <a name="virtual-table-modules"></a>Módulos de tabela virtual

Microsoft. Data. sqlite não tem nenhuma API para criar módulos de tabela virtual. Use o problema [#13823](https://github.com/aspnet/EntityFrameworkCore/issues/13823) para fornecer comentários sobre esse recurso.

## <a name="see-also"></a>Veja também

* [Tipos de dados](types.md)
* [Cadeias de conexão](connection-strings.md)
* [Criptografia](encryption.md)
* [Limitações do ADO.NET](adonet-limitations.md)
* [Limitações do Dapper](dapper-limitations.md)
