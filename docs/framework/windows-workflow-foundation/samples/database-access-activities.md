---
title: Atividades de acesso a base de dados
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: efcdd25ee3e6b86d87d551623b166eab4fa76845
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48777900"
---
# <a name="database-access-activities"></a>Atividades de acesso a base de dados
As atividades de acesso a base de dados permitem que você acesse um base de dados em um fluxo de trabalho. Essas atividades permitem acessar bancos de dados para recuperar ou modificar as informações e usar [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) para acessar o banco de dados.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
>  `<InstallDrive>:\WF_WCF_Samples`
>
>  Se este diretório não existir, vá para (página de download) Baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.
>
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a>Atividades de base de dados
 As seções a seguir detalham a lista de atividades incluídas neste exemplo.

## <a name="dbupdate"></a>DbUpdate
 Executa uma consulta SQL que gerencia uma alteração na base de dados (inserção, atualização, exclusão, e outras alterações).

 Essa classe executa seu trabalho de forma assíncrona (deriva de <xref:System.Activities.AsyncCodeActivity> e usa seus recursos assíncronas).

 Informações de conexão pode ser configurado definindo um nome invariável do provedor (`ProviderName`) e a cadeia de conexão (`ConnectionString`) ou usando apenas um nome da cadeia de conexão (`ConfigFileSectionName`) do arquivo de configuração do aplicativo.

 A consulta seja executada é configurado em sua propriedade de `Sql` e os parâmetros são passados através da coleção de `Parameters` .

 Após `DbUpdate` é executado, o número de registros afetados é retornado na propriedade de `AffectedRecords` .

```
Public class DbUpdate: AsyncCodeActivity
{
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [DependsOn("Parameters")]
    public OutArgument<int> AffectedRecords { get; set; }
}
```

|Argumento|Descrição|
|-|-|
|ProviderName|Invariável nome do provedor ADO.NET. Se esse argumento é definido, então `ConnectionString` também deve ser definido.|
|ConnectionString|Cadeia de conexão para se conectar a base de dados. Se esse argumento é definido, então `ProviderName` também deve ser definido.|
|ConfigName|Nome da seção do arquivo de configuração onde as informações de conexão é armazenada. Quando esse argumento é ajustado `ProviderName` e `ConnectionString` não são necessários.|
|CommandType|Tipo de <xref:System.Data.Common.DbCommand> a ser executado.|
|O SQL|O comando SQL ser executado.|
|Parâmetros|Coleção de parâmetros de consulta SQL.|
|AffectedRecords|Número de registros afetados pela operação a mais recente.|

## <a name="dbqueryscalar"></a>DbQueryScalar
 Executa uma consulta que recupera um único valor de base de dados.

 Essa classe executa seu trabalho de forma assíncrona (deriva de <xref:System.Activities.AsyncCodeActivity%601> e usa seus recursos assíncronas).

 Informações de conexão pode ser configurado definindo um nome invariável do provedor (`ProviderName`) e a cadeia de conexão (`ConnectionString`) ou usando apenas um nome da cadeia de conexão (`ConfigFileSectionName`) do arquivo de configuração do aplicativo.

 A consulta seja executada é configurado em sua propriedade de `Sql` e os parâmetros são passados através da coleção de `Parameters` .

 Após `DbQueryScalar` é executado, o único é retornado na `Result``out` argumento (do tipo `TResult`, que é definido na classe base <xref:System.Activities.AsyncCodeActivity%601>).

```
public class DbQueryScalar<TResult> : AsyncCodeActivity<TResult>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|Argumento|Descrição|
|-|-|
|ProviderName|Invariável nome do provedor ADO.NET. Se esse argumento é definido, então `ConnectionString` também deve ser definido.|
|ConnectionString|Cadeia de conexão para se conectar a base de dados. Se esse argumento é definido, então `ProviderName` também deve ser definido.|
|ConfigName|Nome da seção do arquivo de configuração onde as informações de conexão é armazenada. Quando esse argumento é ajustado `ProviderName` e `ConnectionString` não são necessários.|
|CommandType|Tipo de <xref:System.Data.Common.DbCommand> a ser executado.|
|O SQL|O comando SQL ser executado.|
|Parâmetros|Coleção de parâmetros de consulta SQL.|
|Resultado|Escalar que é obtido depois que a consulta é executada. Esse argumento é do tipo `TResult`.|

## <a name="dbquery"></a>DbQuery
 Executa uma consulta que recupera uma lista de objetos. Depois que a consulta é executada, uma função de mapeamento é executada (pode ser <xref:System.Func%601> < `DbDataReader`, `TResult`> ou uma <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>). Essa função de mapeamento obtém um registro em `DbDataReader` e mapear-lo ao objeto a ser retornado.

 Informações de conexão pode ser configurado definindo um nome invariável do provedor (`ProviderName`) e a cadeia de conexão (`ConnectionString`) ou usando apenas um nome da cadeia de conexão (`ConfigFileSectionName`) do arquivo de configuração do aplicativo.

 A consulta seja executada é configurado em sua propriedade de `Sql` e os parâmetros são passados através da coleção de `Parameters` .

 Os resultados da consulta SQL são recuperados usando `DbDataReader`. A atividade itera com `DbDataReader` e mapeia as linhas em `DbDataReader` a uma instância de `TResult`. O usuário do `DbQuery` tem que fornecer o código de mapeamento e isso podem ser feitos de duas maneiras: usando um <xref:System.Func%601> < `DbDataReader`, `TResult`> ou um <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>. No primeiro caso, o mapa é feito em um único pulso de execução. Portanto, é mais rápido, mas isto não pode ser serializado em XAML. No último caso, o mapa é executado em vários pulsos. Portanto, pode ser mais lento mas pode ser serializada para XAML e ser criado declarativamente (quaisquer atividades existente pode participar no mapeamento).

```
public class DbQuery<TResult> : AsyncCodeActivity<IList<TResult>> where TResult : class
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [OverloadGroup("DirectMapping")]
    [DefaultValue(null)]
    public Func<DbDataReader, TResult> Mapper { get; set; }

    [OverloadGroup("MultiplePulseMapping")]
    [DefaultValue(null)]
    public ActivityFunc<DbDataReader, TResult> MapperFunc { get; set; }
}
```

|Argumento|Descrição|
|-|-|
|ProviderName|Invariável nome do provedor ADO.NET. Se esse argumento é definido, então `ConnectionString` também deve ser definido.|
|ConnectionString|Cadeia de conexão para se conectar a base de dados. Se esse argumento é definido, então `ProviderName` também deve ser definido.|
|ConfigName|Nome da seção do arquivo de configuração onde as informações de conexão é armazenada. Quando esse argumento é ajustado `ProviderName` e `ConnectionString` não são necessários.|
|CommandType|Tipo de <xref:System.Data.Common.DbCommand> a ser executado.|
|O SQL|O comando SQL ser executado.|
|Parâmetros|Coleção de parâmetros de consulta SQL.|
|Mapeador|Função de mapeamento (<xref:System.Func%601><`DbDataReader`, `TResult`>) que utiliza um registro no `DataReader` obtidas como resultado da execução da consulta e retorna uma instância de um objeto do tipo `TResult` a ser adicionado para o `Result` coleção.<br /><br /> Nesse caso, o mapeamento é feito em um único pulso de execução, mas não pode ser criado declarativamente usando o designer.|
|MapperFunc|Função de mapeamento (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) que utiliza um registro no `DataReader` obtidas como resultado da execução da consulta e retorna uma instância de um objeto do tipo `TResult` a ser adicionado para o `Result` coleção.<br /><br /> Nesse caso, o mapeamento é feito em vários pulsos de execução. Essa função pode ser serializada para XAML e ser criado declarativamente (quaisquer atividades existente pode participar no mapeamento).|
|Resultado|Lista de objetos obtidos como o resultado de executar a consulta e executar a função de mapeamento para cada registro em `DataReader`.|

## <a name="dbquerydataset"></a>DbQueryDataSet
 Executa uma consulta que retorna <xref:System.Data.DataSet>. Essa classe executa seu trabalho de forma assíncrona. Ele deriva <xref:System.Activities.AsyncCodeActivity> < `TResult`> e usa seus recursos assíncronas.

 Informações de conexão pode ser configurado definindo um nome invariável do provedor (`ProviderName`) e a cadeia de conexão (`ConnectionString`) ou usando apenas um nome da cadeia de conexão (`ConfigFileSectionName`) do arquivo de configuração do aplicativo.

 A consulta seja executada é configurado em sua propriedade de `Sql` e os parâmetros são passados através da coleção de `Parameters` .

 Após o `DbQueryDataSet` é executado o `DataSet` é retornado na `Result``out` argumento (do tipo `TResult`, que é definido na classe base <xref:System.Activities.AsyncCodeActivity%601>).

```
public class DbQueryDataSet : AsyncCodeActivity<DataSet>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|Argumento|Descrição|
|-|-|
|ProviderName|Invariável nome do provedor ADO.NET. Se esse argumento é definido, então `ConnectionString` também deve ser definido.|
|ConnectionString|Cadeia de conexão para se conectar a base de dados. Se esse argumento é definido, então `ProviderName` também deve ser definido.|
|ConfigName|Nome da seção do arquivo de configuração onde as informações de conexão é armazenada. Quando esse argumento é ajustado `ProviderName` e `ConnectionString` não são necessários.|
|CommandType|Tipo de <xref:System.Data.Common.DbCommand> a ser executado.|
|O SQL|O comando SQL ser executado.|
|Parâmetros|Coleção de parâmetros de consulta SQL.|
|Resultado|<xref:System.Data.DataSet> que é obtido depois que a consulta é executada.|

## <a name="configuring-connection-information"></a>Configurando as informações de conexão
 Qualquer compartilhamento de DbActivities os mesmos parâmetros de configuração. Podem ser configurados em duas maneiras:

-   `ConnectionString + InvariantName`: Defina o nome e a cadeia de conexão invariável do provedor ADO.NET.

    ```
    Activity dbSelectCount = new DbQueryScalar<DateTime>()
    {
        ProviderName = "System.Data.SqlClient",
        ConnectionString = @"Data Source=.\SQLExpress;
                             Initial Catalog=DbActivitiesSample;
                             Integrated Security=True",
        Sql = "SELECT GetDate()"
    };
    ```

-   `ConfigName`: Defina o nome da seção de configuração que contém informações de conexão.

    ```xml
    <connectionStrings>
        <add name="DbActivitiesSample"
             providerName="System.Data.SqlClient"
             connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
      </connectionStrings>
    ```

-   Na atividade:

    ```
    Activity dbSelectCount = new DbQueryScalar<int>()
    {
        ConfigName = "DbActivitiesSample",
        Sql = "SELECT COUNT(*) FROM Roles"
    };
    ```

## <a name="running-this-sample"></a>Executando este exemplo

### <a name="setup-instructions"></a>Instruções de configuração
 Este exemplo usa uma base de dados. Um script de instalação e de carregamento (Setup.cmd) é fornecido com o exemplo. Você deve executar esse arquivo usando o prompt de comando.

 O script de Setup.cmd chama o arquivo de script CreateDb.sql, que contém os comandos SQL que façam o seguinte:

-   Cria um base de dados chamado DbActivitiesSample.

-   Cria as funções da tabela.

-   Cria a tabela employees.

-   Insere três registros nas funções da tabela.

-   Insere doze registros na tabela employees.

##### <a name="to-run-setupcmd"></a>Para executar Setup.cmd

1.  Abra um prompt de comando.

2.  Vá para a pasta de DbActivities.

3.  Digite "Setup. cmd" e pressione ENTER.

    > [!NOTE]
    >  Setup.cmd tentar instalar o exemplo em sua instância de SqlExpress do computador local. Se você deseja instalá-lo em outra instância do SQL server, a edição Setup.cmd com o novo nome da instância.

##### <a name="to-uninstall-the-sample-database"></a>Para desinstalar o base de dados de exemplo

1.  Executar Cleanup.cmd da pasta de exemplo em um prompt de comando.

##### <a name="to-run-the-sample"></a>Para executar a amostra

1.  Abra a solução no Visual Studio 2010

2.  Para criar a solução, pressione CTRL+SHIFT+B.

3.  Para executar o exemplo sem depuração, pressione CTRL+F5.

> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
