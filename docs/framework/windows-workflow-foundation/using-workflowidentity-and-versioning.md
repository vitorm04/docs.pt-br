---
title: Usando WorkflowIdentity e controle de versão
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: f7e66d1827c5224ab97faeceaedc6ec0532a1923
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661207"
---
# <a name="using-workflowidentity-and-versioning"></a>Usando WorkflowIdentity e controle de versão

O <xref:System.Activities.WorkflowIdentity> fornece uma maneira para que os desenvolvedores de aplicativos de fluxo de trabalho associem um nome e uma <xref:System.Version> com uma definição de fluxo de trabalho, e para que essas informações sejam associadas a uma instância de fluxo de trabalho persistida. Essas informações de identidade podem ser usadas por desenvolvedores de aplicativos de fluxo de trabalho para habilitar cenários como execução lado a lado de várias versões de uma definição de fluxo de trabalho, e fornece o pilar para outra funcionalidade como a atualização dinâmica. Este tópico fornece uma visão geral de como usar o <xref:System.Activities.WorkflowIdentity> com hospedagem <xref:System.Activities.WorkflowApplication>. Para obter informações sobre a execução lado a lado das definições de fluxo de trabalho em um serviço de fluxo de trabalho, consulte [controle de versão lado a lado no WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md). Para obter informações sobre a atualização dinâmica, consulte [atualização dinâmica](dynamic-update.md).

## <a name="in-this-topic"></a>Neste tópico

- [Usando WorkflowIdentity](using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)

  - [Execução lado a lado com WorkflowIdentity](using-workflowidentity-and-versioning.md#SxS)

- [Atualizando bancos de dados do .NET Framework 4 de persistência para dar suporte a controle de versão de fluxo de trabalho](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)

  - [Para atualizar o esquema de banco de dados](using-workflowidentity-and-versioning.md#ToUpgrade)

## <a name="UsingWorkflowIdentity"></a> Usando WorkflowIdentity

Para usar <xref:System.Activities.WorkflowIdentity>, crie uma instância, configure-a e associe-a a uma instância <xref:System.Activities.WorkflowApplication>. Uma instância <xref:System.Activities.WorkflowIdentity> contém três informações de identificação. <xref:System.Activities.WorkflowIdentity.Name%2A> e <xref:System.Activities.WorkflowIdentity.Version%2A> contêm um nome e um <xref:System.Version> e são necessários, e <xref:System.Activities.WorkflowIdentity.Package%2A> é opcional e pode ser usado para especificar uma cadeia de caracteres adicional que contém informações como o nome do assembly ou outras informações desejadas. Um <xref:System.Activities.WorkflowIdentity> é exclusivo se qualquer uma de suas três propriedades for diferente da outra <xref:System.Activities.WorkflowIdentity>.

> [!IMPORTANT]
> Um <xref:System.Activities.WorkflowIdentity> não deve conter informações pessoalmente identificáveis (PII). As informações sobre o <xref:System.Activities.WorkflowIdentity> usadas para criar uma instância são emitidas para todos os serviços de rastreamento configurados em vários pontos diferentes do ciclo de vida da atividade em tempo de execução. O Rastreamento WF não tem nenhum mecanismo para ocultar o PII (dados de usuário confidenciais). Portanto, uma instância <xref:System.Activities.WorkflowIdentity> não deve conter nenhum dado de PII porque será emitido pelo tempo de execução em registros de rastreamento e pode estar visível para qualquer um com acesso para exibir os registros de rastreamento.

No exemplo a seguir, <xref:System.Activities.WorkflowIdentity> é criado e associado a uma instância de um trabalho criada usando uma definição de trabalho `MortgageWorkflow`.

```csharp
WorkflowIdentity identityV1 = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1",
    Version = new Version(1, 0, 0, 0)
};

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Run the workflow.
wfApp.Run();
```

Para recarregar e retomar um fluxo de trabalho, um <xref:System.Activities.WorkflowIdentity> que está configurado para corresponder o <xref:System.Activities.WorkflowIdentity> da instância do fluxo de trabalho persistida deve ser usado.

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the workflow.
wfApp.Load(instanceId);

// Resume the workflow...
```

Se o <xref:System.Activities.WorkflowIdentity> usado ao recarregar a instância de fluxo de trabalho não corresponder ao <xref:System.Activities.WorkflowIdentity> persistido, uma <xref:System.Activities.VersionMismatchException> é gerada. No exemplo a seguir, uma tentativa de carregamento é feita na instância `MortgageWorkflow` que foi persistida no exemplo anterior. Essa tentativa de carregamento é feita usando um <xref:System.Activities.WorkflowIdentity> configurado para uma versão mais nova do fluxo de trabalho de hipoteca que não corresponde à instância persistida.

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Attempt to load the workflow instance.
wfApp.Load(instanceId);

// Resume the workflow...
```

Quando o código anterior for executado, o <xref:System.Activities.VersionMismatchException> a seguir será gerado.

```
The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.
```

### <a name="SxS"></a> Execução lado a lado com WorkflowIdentity

O <xref:System.Activities.WorkflowIdentity> pode ser usado para facilitar a execução de várias versões de um fluxo de trabalho lado a lado. Um cenário comum é a mudança de requisitos comerciais em um fluxo de trabalho de execução longa. Muitas instâncias de um fluxo de trabalho podem ser executadas quando uma versão atualizada é implantada. O aplicativo de host pode ser configurado para usar a definição atualizada do fluxo de trabalho ao iniciar novas instâncias e é responsabilidade do aplicativo host fornecer a definição correta do fluxo de trabalho ao retomar instâncias. O <xref:System.Activities.WorkflowIdentity> pode ser usado para identificar e fornecer a definição de fluxo de trabalho correspondente ao retomar instâncias de fluxo de trabalho.

Para recuperar o <xref:System.Activities.WorkflowIdentity> de uma instância do fluxo de trabalho persistida, o método <xref:System.Activities.WorkflowApplication.GetInstance%2A> é usado. O método <xref:System.Activities.WorkflowApplication.GetInstance%2A> usa a <xref:System.Activities.WorkflowApplication.Id%2A> da instância do fluxo de trabalho persistida e o <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> que contém a instância persistida e retorna um <xref:System.Activities.WorkflowApplicationInstance>. Um <xref:System.Activities.WorkflowApplicationInstance> contém informações sobre uma instância do fluxo de trabalho persistida, incluindo o <xref:System.Activities.WorkflowIdentity> associado. Esse <xref:System.Activities.WorkflowIdentity> associado pode ser usado pelo host para fornecer a definição correta de fluxo de trabalho ao carregar e retomar a instância de fluxo de trabalho.

> [!NOTE]
> Um <xref:System.Activities.WorkflowIdentity> nulo é válido e pode ser usado pelo host para mapear as instâncias que foram persistidas sem <xref:System.Activities.WorkflowIdentity> associado para a definição adequada de fluxo de trabalho. Este cenário poderá ocorrer quando um aplicativo de fluxo de trabalho não tiver sido inicialmente escrito com controle de versão de fluxo de trabalho ou quando um aplicativo for atualizado do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]. Para obter mais informações, consulte [atualizando o .NET Framework 4 persistência bancos de dados ao controle de versão de fluxo de trabalho de suporte](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).

No exemplo a seguir uma `Dictionary<WorkflowIdentity, Activity>` é usado para associar <xref:System.Activities.WorkflowIdentity> instâncias com suas definições de fluxo de trabalho correspondente e um fluxo de trabalho é iniciado usando o `MortgageWorkflow` definição de fluxo de trabalho, que está associada com o `identityV1` <xref:System.Activities.WorkflowIdentity>.

```csharp
WorkflowIdentity identityV1 = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1",
    Version = new Version(1, 0, 0, 0)
};

WorkflowIdentity identityV2 = new WorkflowIdentity
{
    Name = "MortgageWorkflow v2",
    Version = new Version(2, 0, 0, 0)
};

Dictionary<WorkflowIdentity, Activity> WorkflowVersionMap = new Dictionary<WorkflowIdentity, Activity>();
WorkflowVersionMap.Add(identityV1, new MortgageWorkflow());
WorkflowVersionMap.Add(identityV2, new MortgageWorkflow_v2());

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Run the workflow.
wfApp.Run();
```

No exemplo a seguir, as informações sobre a instância do fluxo de trabalho persistida do exemplo anterior são recuperadas chamando <xref:System.Activities.WorkflowApplication.GetInstance%2A>, e as informações persistidas do <xref:System.Activities.WorkflowIdentity> são usadas para recuperar a definição de fluxo de trabalho correspondente. Essas informações são usadas para configurar o <xref:System.Activities.WorkflowApplication> e, em seguida, o fluxo de trabalho é carregado. Observe que, como a sobrecarga do <xref:System.Activities.WorkflowApplication.Load%2A> que usa o <xref:System.Activities.WorkflowApplicationInstance> é usada, o <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> que foi configurado no <xref:System.Activities.WorkflowApplicationInstance> é usado pelo <xref:System.Activities.WorkflowApplication> e, portanto, a propriedade de <xref:System.Activities.WorkflowApplication.InstanceStore%2A> não precisa ser configurada.

> [!NOTE]
>  Se a propriedade <xref:System.Activities.WorkflowApplication.InstanceStore%2A> for definida, ela deverá ser definida com a mesma instância <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> usada pelo <xref:System.Activities.WorkflowApplicationInstance> ou um <xref:System.ArgumentException> será gerado com a seguinte mensagem: `The instance is configured with a different InstanceStore than this WorkflowApplication.`

```csharp
// Get the WorkflowApplicationInstance of the desired workflow from the specified
// SqlWorkflowInstanceStore.
WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(instanceId, store);

// Use the persisted WorkflowIdentity to retrieve the correct workflow
// definition from the dictionary.
Activity definition = WorkflowVersionMap[instance.DefinitionIdentity];

WorkflowApplication wfApp = new WorkflowApplication(definition, instance.DefinitionIdentity);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the persisted workflow instance.
wfApp.Load(instance);

// Resume the workflow...
```

## <a name="UpdatingWF4PersistenceDatabases"></a> Atualizando bancos de dados do .NET Framework 4 de persistência para dar suporte a controle de versão de fluxo de trabalho

Um script de banco de dados SqlWorkflowInstanceStoreSchemaUpgrade.sql é fornecido para atualizar bancos de dados de persistência criados usando os scripts de banco de dados do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]. Esse script atualiza os bancos de dados para dar suporte a novos recursos de controle de versão introduzidos no .NET Framework 4.5. As instâncias de fluxo de trabalho persistidas nos bancos de dados recebem valores padrão do controle de versão e podem participar da execução lado a lado e da atualização dinâmica.

Se um aplicativo de fluxo de trabalho do .NET Framework 4.5 tentar qualquer operação de persistência que usam os novos recursos de controle de versão em um banco de dados de persistência que não foi atualizado usando o script fornecido, um <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> será lançada com uma mensagem semelhante do mensagem a seguir.

```
The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.
```

### <a name="ToUpgrade"></a> Para atualizar o esquema de banco de dados

1. Abra o SQL Server Management Studio e conecte-se para o servidor de banco de dados de persistência, por exemplo **. \SQLEXPRESS**.

2. Escolher **aberto**, **arquivo** do **arquivo** menu. Navegue até a pasta a seguir: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`

3. Selecione **Sqlworkflowinstancestoreschemaupgrade** e clique em **abrir**.

4. Selecione o nome do banco de dados de persistência na **bancos de dados disponíveis** lista suspensa.

5. Escolher **Execute** da **consulta** menu.

Quando a consulta tiver sido concluída, o esquema de banco de dados é atualizado e, se desejar, você poderá exibir a identidade padrão de fluxo de trabalho que foi atribuída a instâncias de fluxo de trabalho persistidas. Expanda o banco de dados de persistência na **bancos de dados** nó do **Pesquisador de objetos**e, em seguida, expanda o **modos de exibição** nó. Clique com botão direito **System.Activities.DurableInstancing.Instances** e escolha **selecionar 1000 linhas superiores**. Role até o final das colunas e observe que há seis colunas adicionais adicionadas ao modo de exibição: **IdentityName**, **IdentityPackage**, **Build**, **principais**, **secundárias**, e **revisão**. Quaisquer fluxos de trabalho persistidos terão um valor de **nulo** para esses campos, representando uma identidade de fluxo de trabalho nula.
