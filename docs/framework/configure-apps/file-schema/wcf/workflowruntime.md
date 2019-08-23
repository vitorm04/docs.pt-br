---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: 0cd04f66cc4b73eb5f1c43bd6c8dc9189dfceff1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915211"
---
# <a name="workflowruntime"></a>\<workflowRuntime>
Especifica as configurações para uma instância <xref:System.Workflow.Runtime.WorkflowRuntime> do para hospedar serviços de Windows Communication Foundation baseado em fluxo de trabalho (WCF).  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<> de portais  
\<> de comportamento  
\<workflowRuntime>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"
                 enablePerformanceCounters="Boolean"
                 name="String"
                 validateOnCreate="Boolean">
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|cachedInstanceExpiration|Um valor <xref:System.TimeSpan> opcional que especifica a duração máxima em que uma instância de fluxo de trabalho pode permanecer na memória no estado ocioso antes de ser descarregada ou anulada de modo forçado. Se o WorkflowRuntime tiver `PersistenceService` que executar UnloadOnIdle, esse atributo será ignorado.|  
|enablePerformanceCounters|Um valor booliano opcional que especifica se os contadores de desempenho estão habilitados. Os contadores de desempenho fornecem informações sobre várias estatísticas relacionadas ao fluxo de trabalho, mas causam uma penalidade de desempenho quando o mecanismo de tempo de execução do fluxo de trabalho é iniciado e quando as instâncias de fluxo de trabalho estão em execução. O valor padrão é `true`.|  
|name|Uma cadeia de caracteres que contém o nome do mecanismo de tempo de execução do fluxo de trabalho. O nome é usado na saída para distinguir esse tempo de execução de outros tempos de execução que podem estar em execução no sistema, por exemplo, em contadores de desempenho.<br /><br /> O padrão é uma cadeia de caracteres vazia.|  
|validateOnCreate|Um valor booliano opcional que especifica se a validação da definição de fluxo de trabalho ocorrerá quando o WorkflowServiceHost for aberto.  Quando esse atributo é definido como `true`, a validação do fluxo de trabalho é `WorkflowServiceHost.Open` executada toda vez que é chamada. Se forem encontrados erros de validação, <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> um erro será gerado.<br /><br /> Quando essa propriedade é definida como `false`, nenhuma validação de definição de fluxo de trabalho ocorrerá.<br /><br /> O valor padrão para essa propriedade é `true`.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|commonParameters|Uma coleção de parâmetros comuns usados por serviços. Normalmente, essa coleção inclui a cadeia de conexão do banco de dados que pode ser compartilhada por serviços duráveis.|  
|serviços|Uma coleção de serviços que serão adicionados ao <xref:System.Workflow.Runtime.WorkflowRuntime> mecanismo. Os elementos são do tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  Os serviços especificados na coleção serão inicializados pelo mecanismo de tempo de execução do fluxo de trabalho e adicionados aos seus <xref:System.Workflow.Runtime.WorkflowRuntime> serviços quando o construtor apropriado for chamado. Portanto, os serviços especificados na coleção devem seguir determinadas regras sobre as assinaturas de seus construtores. Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<> de comportamento](behavior-of-endpointbehaviors.md)|Especifica um elemento de comportamento.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre como usar um arquivo de configuração para controlar o <xref:System.Workflow.Runtime.WorkflowRuntime> comportamento de um objeto de um aplicativo host Windows Workflow Foundation, consulte [arquivos de configuração de fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).  
  
## <a name="example"></a>Exemplo  
  
```xml  
<serviceBehaviors>
   <behavior name="ServiceBehavior">
      <workflowRuntime name="WorkflowServiceHostRuntime"
                       validateOnCreate="true"
                       enablePerformanceCounters="true">
         <commonParameters>
            <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
            <add name="EnableRetries" value="True" />
         </commonParameters>
         <services>
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>
         </services>
      </workflowRuntime>
   </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- [Arquivos de configuração de fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
