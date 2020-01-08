---
title: '{1&gt;Visão Geral&lt;1}'
ms.date: 12/13/2019
description: Uma visão geral do Microsoft. Data. sqlite
ms.openlocfilehash: a5dc1366cc0ddfcd5501e26bf2a994456bcd5d98
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447226"
---
# <a name="microsoftdatasqlite-overview"></a>Visão geral do Microsoft. Data. sqlite

Microsoft. Data. SQLite é um provedor [ADO.net](../../../framework/data/adonet/index.md) leve para SQLite. O provedor de [Entity Framework Core](/ef/core/) para SQLite é criado sobre esta biblioteca. No entanto, ele também pode ser usado de forma independente ou com outras bibliotecas de acesso a dados.

## <a name="installation"></a>Instalação

A versão estável mais recente está disponível no [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).

### <a name="net-core-clitabnetcore-cli"></a>[CLI do .NET Core](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studiotabvisual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a>Medição de

Essa biblioteca implementa as abstrações ADO.NET comuns para conexões, comandos, leitores de dados e assim por diante.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a>Veja também

* [Cadeias de conexão](connection-strings.md)
* [Referência de API](/dotnet/api/?view=msdata-sqlite-3.0.0)
* [Sintaxe SQL](https://www.sqlite.org/lang.html)
