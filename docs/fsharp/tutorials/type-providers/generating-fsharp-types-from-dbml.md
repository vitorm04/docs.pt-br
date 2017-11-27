---
title: "Instruções passo a passo: gerando tipos F# com base em um arquivo DBML (F#)"
description: "Saiba como criar tipos F # para dados de um banco de dados em F # 3.0 quando você tiver informações de esquema codificadas em um arquivo dbml."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6fbb6ccc-248f-4226-95e9-f6f99541dbe4
ms.openlocfilehash: 50e0a2bb6378c82b5c6425589da8a982b5fc496a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-generating-f-types-from-a-dbml-file"></a>Instruções passo a passo: gerando tipos F# com base em um arquivo DBML

> [!NOTE]
Este guia foi escrito para F # 3.0 e será atualizado.  Consulte [FSharp.Data](http://fsharp.github.io/FSharp.Data/) para provedores de tipo de plataforma cruzada atualizados.

> [!NOTE]
Os links de referência de API levará você para o MSDN.  A referência da API docs.microsoft.com não está completa.

Este passo a passo para F # 3.0 descreve como criar tipos de dados de um banco de dados quando você tiver informações de esquema codificadas em um arquivo dbml. O LINQ to SQL usa esse formato de arquivo para representar o esquema de banco de dados. Você pode gerar um arquivo LINQ to SQL esquema no Visual Studio usando o Designer relacional de objeto (Object Relational). Para obter mais informações, consulte [Object Relational Designer Overview](https://msdn.microsoft.com/library/bb384511.aspx) e [geração de código em LINQ to SQL](https://msdn.microsoft.com/library/bb386976).

O provedor de tipo de linguagem de marcação de banco de dados (DBML) permite que você escreva código que usa tipos com base em um esquema de banco de dados sem a necessidade de especificar uma cadeia de caracteres de conexão estática em tempo de compilação. Isso pode ser útil se você precisar permitir a possibilidade de que o aplicativo final usará um banco de dados diferente, credenciais diferentes ou uma cadeia de caracteres de conexão diferentes que você pode usar para desenvolver o aplicativo. Se você tiver uma conexão direta do banco de dados que você pode usar em tempo de compilação e esse é o mesmo banco de dados e as credenciais que você ainda usará em seu aplicativo compilado, você também pode usar o provedor de tipos SQLDataConnection. Para obter mais informações, consulte [passo a passo: acessando um banco de dados SQL usando provedores de tipos](accessing-a-sql-database.md).

Esta explicação passo a passo mostra as seguintes tarefas. Que devem ser concluídas na ordem para a passo a passo para ter êxito:


- Criando um arquivo dbml
<br />

- Criando e configurando um projeto F #
<br />

- Configurar o provedor de tipos e gerar os tipos de
<br />

- Consultando o banco de dados
<br />


## <a name="prerequisites"></a>Pré-requisitos

## <a name="creating-a-dbml-file"></a>Criando um arquivo dbml
Se você não tiver um banco de dados de teste em, crie um seguindo as instruções na parte inferior da [passo a passo: acessando um banco de dados SQL usando provedores de tipos](accessing-a-sql-database.md). Se você seguir estas instruções, você criará um banco de dados chamado MyDatabase que contém algumas tabelas simples e procedimentos armazenados no SQL Server.

Se você já tiver um arquivo dbml, você pode ignorar a seção **criar e definir a um projeto F #**. Caso contrário, você pode criar um arquivo dbml fornecido a um banco de dados SQL e usando a linha de comando ferramenta SqlMetal.exe.


#### <a name="to-create-a-dbml-file-by-using-sqlmetalexe"></a>Para criar um arquivo dbml usando SqlMetal.exe

1. Abra um **Prompt de comando do desenvolvedor**.
<br />

2. Verifique se você tem acesso ao SqlMetal.exe digitando `SqlMetal.exe /?` no prompt de comando. SqlMetal.exe é normalmente instalado no **SDKs do Microsoft** pasta **arquivos de programa** ou **arquivos de programa (x86)**.
<br />

3. Execute SqlMetal.exe com as seguintes opções de linha de comando. Substituir por um caminho correto no lugar de `c:\destpath` para criar o arquivo dbml e inserir os valores apropriados para o servidor de banco de dados, nome da instância e o nome de banco de dados.
<br />

```
  SqlMetal.exe /sprocs /dbml:C:\destpath\MyDatabase.dbml /server:SERVER\INSTANCE /database:MyDatabase
```

>[!NOTE]
Se SqlMetal.exe tiver problemas para criar o arquivo devido a problemas de permissões, altere o diretório atual para uma pasta que você tem acesso de gravação.


4. Você também pode examinar as outras opções de linha de comando disponíveis. Por exemplo, há opções que você pode usar se desejar exibições e funções SQL incluídas entre os tipos gerados. Para obter mais informações, consulte [SqlMetal.exe &#40; Ferramenta de geração de código &#41; ](https://msdn.microsoft.com/library/bb386987).
<br />


## <a name="creating-and-setting-up-an-f-project"></a>Criando e configurando um projeto F #
Nesta etapa, você pode cria um projeto e adicionar referências apropriadas para usar o provedor de tipo DBML.


#### <a name="to-create-and-set-up-an-f-project"></a>Para criar e configurar um projeto de F#

1. Adicione um novo projeto de aplicativo de Console em F # para sua solução.
<br />

2. Em **Solution Explorer**, abra o menu de atalho para **referências**e, em seguida, escolha **adicionar referência**.
<br />

3. No **Assemblies** área, escolha o **Framework** nó e, em seguida, na lista de assemblies disponíveis, escolha o **System. Data** e **System.Data.Linq**  assemblies.
<br />

4. No **Assemblies** área, escolha **extensões**e, em seguida, na lista de assemblies disponíveis, escolha **FSharp.Data.TypeProviders**.
<br />

5. Escolha o **Okey** botão para adicionar referências a esses assemblies ao seu projeto.
<br />

6. (Opcional). Copie o arquivo dbml que você criou na etapa anterior e, em seguida, cole o arquivo na pasta principal para o seu projeto. Esta pasta contém o arquivo de projeto (fsproj) e arquivos de código. Na barra de menus, escolha **projeto**, **Add Existing Item**e, em seguida, especifique o arquivo dbml para adicioná-lo ao seu projeto. Se você concluir essas etapas, você pode omitir o parâmetro static ResolutionFolder na próxima etapa.
<br />

## <a name="configuring-the-type-provider"></a>Configurando o provedor de tipos
Nesta seção, você cria um provedor de tipos e gerar tipos de esquema que é descrito no arquivo dbml.


#### <a name="to-configure-the-type-provider-and-generate-the-types"></a>Para configurar o provedor de tipos e gerar os tipos

- Adicione o código que abre o **TypeProviders** namespace e instancia o provedor de tipos para o arquivo dbml que você deseja usar. Se você adicionou o arquivo dbml ao seu projeto, você pode omitir o parâmetro estático ResolutionFolder.
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ResolutionFolder = @"<path-to-folder-that-contains-.dbml-file>">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let dataContext = new dbml.Mydatabase(connectionString)
```

O tipo DataContext fornece acesso a todos os tipos gerados e herda do `System.Data.Linq.DataContext`. O provedor de tipos DbmlFile tem vários parâmetros estáticos que podem ser definidas. Por exemplo, você pode usar um nome diferente para o tipo DataContext especificando `DataContext=MyDataContext`. Nesse caso, seu código semelhante ao exemplo a seguir:
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ContextTypeName = "MyDataContext">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let db = new dbml.MyDataContext(connectionString)
```

## <a name="querying-the-database"></a>Consultando o banco de dados
Nesta seção, você pode usar expressões de consulta do F # para consultar o banco de dados.


#### <a name="to-query-the-data"></a>Para consultar os dados

- Adicione código para consultar o banco de dados.
<br />

```fsharp
  query {
    for row in db.Table1 do
    where (row.TestData1 > 2)
    select row
  } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

## <a name="next-steps"></a>Próximas etapas
Você pode continuar a usar outras expressões de consulta, ou obter uma conexão de banco de dados do contexto de dados e executar operações normais de dados ADO.NET. Para obter as etapas adicionais, consulte as seções depois de "Consulta os dados" em [passo a passo: acessando um banco de dados SQL usando provedores de tipos](accessing-a-sql-database.md).


## <a name="see-also"></a>Consulte também
[Tipo DbmlFile](https://msdn.microsoft.com/visualfsharpdocs/conceptual/dbmlfile-type-provider-%5bfsharp%5d)

[Provedores de Tipos](index.md)

[Instruções passo a passo: acessando um banco de dados SQL por meio de provedores de tipos](accessing-a-sql-database.md)

[SqlMetal.exe &#40; Ferramenta de geração de código &#41;](https://msdn.microsoft.com/library/bb386987)

[Expressões de Consulta](../../language-reference/query-expressions.md)
