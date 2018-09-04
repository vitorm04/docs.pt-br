---
title: '&lt;workflowRuntime&gt;'
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: 849b09936f303c21fe55a6a46d561590c6a4c808
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504955"
---
# <a name="ltworkflowruntimegt"></a>&lt;workflowRuntime&gt;
Especifica configurações para uma instância de <xref:System.Workflow.Runtime.WorkflowRuntime> para hospedar os serviços do Windows Communication Foundation (WCF) baseados em fluxo de trabalho.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors >  
\<comportamento de >  
\<workflowRuntime>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"  
                                  enablePerformanceCounters="Boolean"  
                                  name="String"  
                                  validateOnCreate="Boolean">  
                 <commonParameters>  
                    <add name="String" value="String" />  
                 </commonParameters>  
                 <services>  
                    <add type="String"/>  
                 </services>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|cachedInstanceExpiration|Um recurso opcional <xref:System.TimeSpan> valor que especifica a duração máxima que uma instância de fluxo de trabalho pode permanecer na memória no estado ocioso antes de modo forçado é descarregado ou anulada. Se tiver o workflowruntime `PersistenceService` que executa unloadOnIdle, esse atributo é ignorado.|  
|enablePerformanceCounters|Um valor booleano opcional que especifica se contadores de desempenho estão habilitados. Contadores de desempenho fornecem informações sobre várias estatísticas relacionadas ao fluxo de trabalho, mas eles causam uma penalidade de desempenho quando o mecanismo de tempo de execução do fluxo de trabalho é iniciado e quando as instâncias de fluxo de trabalho estão em execução. O valor padrão é `true`.|  
|name|Uma cadeia de caracteres que contém o nome do mecanismo de tempo de execução do fluxo de trabalho. O nome é usado na saída para distinguir esse tempo de execução de outros tempos de execução podem estar em execução no sistema, por exemplo, nos contadores de desempenho.<br /><br /> O padrão é uma cadeia de caracteres vazia.|  
|validateOnCreate|Um valor booleano opcional que especifica se a validação da definição de fluxo de trabalho ocorrerá quando o WorkflowServiceHost for aberto.  Quando esse atributo é definido como `true`, a validação do fluxo de trabalho é executada sempre que `WorkflowServiceHost.Open` é chamado. Se forem encontrados erros de validação, um <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> erro será gerado.<br /><br /> Quando essa propriedade é definida como `false`, nenhuma validação de definição de fluxo de trabalho acontecerá.<br /><br /> O valor padrão desta propriedade é `true`.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|commonParameters|Uma coleção de parâmetros comuns usados pelos serviços. Esta coleção normalmente incluirão a cadeia de caracteres de conexão de banco de dados que pode ser compartilhada por serviços duráveis.|  
|serviços|Uma coleção de serviços que serão adicionados para o <xref:System.Workflow.Runtime.WorkflowRuntime> mecanismo. Os elementos são do tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  Os serviços especificados na coleção serão inicializados pelo mecanismo de tempo de execução de fluxo de trabalho e adicionados a seus serviços quando apropriado <xref:System.Workflow.Runtime.WorkflowRuntime> construtor é chamado. Portanto, os serviços especificados na coleção devem seguir determinadas regras sobre as assinaturas de seus construtores. Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<comportamento de >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um elemento de comportamento.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre como usar um arquivo de configuração para controlar o comportamento de um <xref:System.Workflow.Runtime.WorkflowRuntime> objeto de um aplicativo de host do Windows Workflow Foundation, consulte [arquivos de configuração do fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).  
  
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
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 [Arquivos de configuração do fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
