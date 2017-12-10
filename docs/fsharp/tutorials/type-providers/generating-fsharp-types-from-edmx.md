---
title: "Instruções passo a passo: gerando tipos F# com base em um arquivo de esquema EDMX (F#)"
description: "Saiba como criar tipos F # para dados representados pela entidade de dados EDM (modelo) em F # 3.0, onde o esquema está especificado em um arquivo. edmx."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 81adb2eb-625f-4ad8-aeaa-8f672a6d79a2
ms.openlocfilehash: 1df0344e8dab2b40d82d1b9c61ccd2f026906243
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-generating-f-types-from-an-edmx-schema-file"></a>Instruções passo a passo: gerando tipos F# com base em um arquivo de esquema EDMX

> [!NOTE]
Este guia foi escrito para F # 3.0 e será atualizado.  Consulte [FSharp.Data](http://fsharp.github.io/FSharp.Data/) para provedores de tipo de plataforma cruzada atualizados.

> [!NOTE]
Os links de referência de API levará você para o MSDN.  A referência da API docs.microsoft.com não está completa.

Este guia passo a passo para o F# 3.0 mostra como criar tipos para dados que são representados pelo EDM (Modelo de Dados de Entidade), o esquema para o qual é especificado em um arquivo .edmx. Esse guia também mostra como usar o provedor de tipos EdmxFile. Antes de começar, considere se um provedor de tipos SqlEntityConnection é uma opção mais apropriada de provedor de tipos. O provedor de tipos SqlEntityConnection funciona melhor em cenários onde você tem um banco de dados dinâmico ao qual você pode se conectar durante a fase de desenvolvimento de seu projeto e você não se importa em especificar a cadeia de conexão em tempo de compilação. No entanto, esse provedor de tipos também é limitado na medida que expõe tanta funcionalidade de banco de dados quanto o provedor de tipos EdmxFile. Além de isso, se você não tiver uma conexão de banco de dados dinâmico para um projeto de banco de dados que use o Modelo de Dados de Entidade, será possível usar o arquivo .edmx para codificação em relação ao banco de dados. Quando você usa o provedor de tipos EdmxFile, o compilador F# executa EdmGen.exe para gerar os tipos que ele fornece.

Este guia passo a passo ilustra as seguintes tarefas que você deve executar nesta ordem para que as instruções sejam bem-sucedidas:


- Criando um arquivo EDMX
<br />

- Criando o projeto
<br />

- Localizando ou criando a cadeia de conexão do Modelo de Dados de Entidade
<br />

- Configurando o provedor de tipos
<br />

- Consultando os dados
<br />

- Chamando um procedimento armazenado
<br />


## <a name="prerequisites"></a>Pré-requisitos

## <a name="creating-an-edmx-file"></a>Criando um arquivo EDMX
Se você já tiver um arquivo EDMX, pule esta etapa.


#### <a name="to-create-an-edmx-file"></a>Para criar um arquivo EDMX

- Se você ainda não tiver um arquivo EDMX, você pode seguir as instruções no final deste passo a passo na etapa [configurar o modelo de dados de entidade](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model).
<br />

## <a name="creating-the-project"></a>Criando o projeto
Nesta etapa, você criará um projeto e adicionará referências apropriadas a ele para usar o provedor de tipos EDMX.


#### <a name="to-create-and-set-up-an-f-project"></a>Para criar e configurar um projeto de F#

1. Feche o projeto anterior, crie outro projeto e o chame SchoolEDM.
<br />

2. Em **Solution Explorer**, abra o menu de atalho para **referências**e, em seguida, escolha **adicionar referência**.
<br />

3. No **Assemblies** área, escolha o **Framework** nó.
<br />

4. Na lista de assemblies disponíveis, escolha o **System.Data.Entity** e **System.Data.Linq** assemblies e, em seguida, escolha o **adicionar** botão para adicionar referências a eles assemblies ao seu projeto.
<br />

5. No **Assemblies** área, selecione o **extensões** nó.
<br />

6. Na lista de extensões disponíveis, adicione uma referência ao assembly FSharp.Data.TypeProviders.
<br />

7. Adicione o código a seguir para abrir os namespaces apropriados.
<br />

```fsharp
open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

## <a name="finding-or-creating-the-connection-string-for-the-entity-data-model"></a>Localizando ou criando a cadeia de conexão para o Modelo de Dados de Entidade
A cadeia de conexão para o Modelo de Dados de Entidade (cadeia de conexão EDMX) inclui não somente a cadeia de conexão para o provedor de banco de dados, mas também informações adicionais. Por exemplo, a cadeia de conexão EDMX para um banco de dados SQL Server simples lembra o código a seguir.

```fsharp
let edmConnectionString = "metadata=res://*/;provider=System.Data.SqlClient;Provider Connection String='Server=SERVER\Instance;Initial Catalog=DatabaseName;Integrated Security=SSPI;'"
```

Para obter mais informações sobre cadeias de caracteres de conexão EDMX, consulte [cadeias de caracteres de Conexão](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).


#### <a name="to-find-or-create-the-connection-string-for-the-entity-data-model"></a>Para localizar ou criar a cadeia de conexão para o Modelo de Dados de Entidade

1. A geração manual de cadeias de conexão EDMX pode ser difícil, portanto, é possível economizar tempo gerando-as via programação. Se você souber a sua cadeia de conexão EDMX, ignore esta etapa e simplesmente use essa cadeia na próxima etapa. Em caso negativo, use o código a seguir para gerar a cadeia de conexão EDMX de uma cadeia de conexão de banco de dados fornecida por você.
<br />

```fsharp
open System
open System.Data
open System.Data.SqlClient
open System.Data.EntityClient
open System.Data.Metadata.Edm

let getEDMConnection(dbConnectionString) =
  let dbConnection = new SqlConnection(dbConnectionString)
  let resourceArray = [| "res://*/" |]
  let assemblyList = [| System.Reflection.Assembly.GetCallingAssembly() |]
  let metaData = MetadataWorkspace(resourceArray, assemblyList)
  new EntityConnection(metaData, dbConnection)
```

## <a name="configuring-the-type-provider"></a>Configurando o provedor de tipos
Nesta etapa, você criará e configurará o provedor de tipos com a cadeia de conexão EDMX e você gerará tipos para o esquema definido no arquivo .edmx.


#### <a name="to-configure-the-type-provider-and-generate-types"></a>Para configurar o provedor de tipos e gerar tipos

1. Copie o arquivo .edmx que você gerou na primeira etapa deste guia passo a passo na pasta de seu projeto.
<br />

2. Abrir o menu de atalho para o nó de projeto em seu projeto de F #, escolher **Add Existing Item**e, em seguida, escolha o arquivo. edmx para adicioná-lo ao seu projeto.
<br />

3. Insira o código a seguir para ativar o provedor de tipos para o seu arquivo .edmx. Substituir *servidor*\*instância * com o nome do servidor que está executando o SQL Server e o nome da sua instância e usar o nome do arquivo. edmx da primeira etapa neste passo a passo.
<br />

```fsharp
type edmx = EdmxFile<"Model1.edmx", ResolutionFolder = @"<path-tofolder-that-containsyour.edmx-file>">

use edmConnection =
  getEDMConnection("Data Source=SERVER\instance;Initial Catalog=School;Integrated Security=true;")
use context = new edmx.SchoolModel.SchoolEntities(edmConnection)
```

## <a name="querying-the-data"></a>Consultando os dados
Nesta etapa, você usa expressões de consulta do F# para consultar o banco de dados.


#### <a name="to-query-the-data"></a>Para consultar os dados

- Insira o código a seguir para consultar os dados no modelo de dados de entidade.
<br />

```fsharp
query { 
  for course in context.Courses do
  select course 
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.Person do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results
query { 
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="calling-a-stored-procedure"></a>Chamando um procedimento armazenado
Você pode chamar procedimentos armazenados ao usar o provedor de tipos EDMX. O procedimento a seguir, o banco de dados de escola contém um procedimento armazenado, **UpdatePerson**, que atualiza um registro, determinados novos valores para as colunas. Você pode usar esse procedimento armazenado porque ele está exposto como um método no tipo DataContext.


#### <a name="to-call-a-stored-procedure"></a>Para chamar um procedimento armazenado

- Adicione o código a seguir para atualizar registros.
<br />

```fsharp
// Call a stored procedure.
let nullable value = new System.Nullable<_>(value)

// Assume now that you must correct someone's hire date.
// Throw an exception if more than one matching person is found.
let changeHireDate(lastName, firstName, hireDate) =

  query { 
    for person in context.People do
    where (person.LastName = lastName &&
           person.FirstName = firstName)
    exactlyOne 
  } |> (fun person ->
            context.UpdatePerson(nullable person.PersonID, person.LastName, person.FirstName, nullable hireDate, person.EnrollmentDate))

changeHireDate("Abercrombie", "Kim", DateTime.Parse("1/12/1998"))
|> printfn "Result: %d"
```

O resultado será 1 se houver êxito. Observe que **exactlyOne** é usado na expressão de consulta para garantir que apenas um resultado é retornado; caso contrário, uma exceção será lançada. Além disso, para trabalhar com valores anuláveis mais facilmente, você pode usar o simples **anulável** função que está definida nesse código para criar um valor nulo fora de um valor comum.

<br />

## <a name="configuring-the-entity-data-model"></a>Configurando o Modelo de Dados de Entidade
Você deve concluir este procedimento somente se você desejar saber como gerar um Modelo de Dados de Entidade completo de um banco de dados e não tiver um banco de dados com o qual testar.


#### <a name="to-configure-the-entity-data-model"></a>Para configurar o Modelo de Dados de Entidade

1. Na barra de menus, escolha **SQL**, **Editor Transact-SQL**, **nova consulta** para criar um banco de dados. Caso sejam solicitados, especifique o servidor e a instância de banco de dados.
<br />

2. Copie e cole o conteúdo do script de banco de dados que cria o banco de dados do aluno, conforme descrito no [documentação do Entity Framework](http://msdn.microsoft.com/data/JJ614587.aspx) no Centro de desenvolvedores de dados.
<br />

3. Execute o script SQL escolhendo o botão de barra de ferramentas com o símbolo de triângulo ou escolhendo as teclas Ctrl + Q.
<br />

4. Em **Server Explorer**, abra o menu de atalho para **conexões de dados**, escolha **Adicionar Conexão**e, em seguida, digite o nome do servidor de banco de dados, o nome da instância e o banco de dados de escola.
<br />

5. Criar um projeto c# ou Visual Basic aplicativo de Console, abra o menu de atalho, escolha **Adicionar Novo Item**e, em seguida, escolha **modelo de dados de entidade ADO.NET**.
<br />  O Assistente do Modelo de Dados de Entidade será aberto. Ao usar este assistente, você poderá escolher como deseja criar o Modelo de Dados de Entidade.
<br />

6. Em **escolher o modelo de conteúdo**, selecione o **gerar do banco de dados** caixa de seleção.
<br />

7. Na próxima página, escolha o banco de dados escolar recém-criado como a conexão de dados.
<br />  Deve ser semelhante a esta conexão  **&lt;servername&gt;.&lt; InstanceName&gt;. School.dbo**.
<br />

8. Copie sua cadeia de conexão de entidade para a Área de Transferência porque essa cadeia de caracteres pode ser importante posteriormente.
<br />

9. Verifique se a caixa de seleção para salvar a cadeia de caracteres de conexão de entidade para o **App. config** arquivo está selecionado e anote o valor de cadeia de caracteres na caixa de texto, que deve ajudá-lo a localizar a cadeia de caracteres de conexão mais tarde, se necessário.
<br />

10. Na próxima página, escolha **tabelas** e **procedimentos armazenados e funções**.
<br />  Ao escolher esses nós de nível superior, você escolherá todas as tabelas, procedimentos armazenados e funções. Você também pode escolhê-los individualmente se desejar.
<br />

11. Certifique-se de que as caixas de seleção para as outras configurações estejam selecionadas.
<br />  A primeira **Pluralizar ou singularizar nomes de objetos gerados** caixa de seleção indica se deve alterar as formas singulares para plural para corresponder as convenções de nomenclatura de objetos que representam as tabelas de banco de dados. O **incluir colunas de chave estrangeira no modelo** caixa de seleção determina se deve incluir campos para os quais o objetivo é unir a outros campos nos tipos de objeto que são gerados para o esquema de banco de dados. A terceira caixa de seleção indica se procedimentos armazenados e funções devem ser incluídos no modelo.
<br />

12. Selecione o **concluir** botão para gerar um arquivo. edmx que contém um modelo de dados de entidade com base no banco de dados School.
<br />  Um arquivo **Model1.edmx**, é adicionado ao seu projeto, e um diagrama de banco de dados é exibida.
<br />

13. Na barra de menus, escolha **exibição**, **outras janelas**, **Entity Data Model Browser** para exibir todos os detalhes do modelo ou **mapeamento detalhes do modelo de dados de entidade**  para abrir uma janela que mostra como o modelo de objeto gerado mapeia colunas e tabelas de banco de dados.
<br />


## <a name="next-steps"></a>Próximas etapas
Explore outras consultas, observando os operadores de consulta disponíveis conforme listado em [expressões de consulta](../../language-reference/query-expressions.md).


## <a name="see-also"></a>Consulte também
[Provedores de Tipos](index.md)

[Tipo EdmxFile](https://msdn.microsoft.com/visualfsharpdocs/conceptual/edmxfile-type-provider-%5bfsharp%5d)

[Instruções passo a passo: acessando um banco de dados SQL por meio de provedores de tipos e entidades](accessing-a-sql-database-entities.md)

[Entity Framework](http://msdn.microsoft.com/data/ef)

[Visão geral do arquivo. edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)

[Gerador EDM &#40; EdmGen.exe &#41;](https://msdn.microsoft.com/library/bb387165)

