---
title: '&lt;workflowRuntime&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2860c7ddd5f3d2f0ce2749c36afebcf9abfeac3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowruntimegt"></a>&lt;workflowRuntime&gt;
Especifica configurações para uma instância de <xref:System.Workflow.Runtime.WorkflowRuntime> para a hospedagem com base em fluxo de trabalho [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] serviços.  
  
 \<sistema. ServiceModel >  
\<comportamentos >  
\<serviceBehaviors >  
\<comportamento >  
\<workflowRuntime >  
  
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
|cachedInstanceExpiration|Um recurso opcional <xref:System.TimeSpan> valor que especifica a duração máxima que uma instância de fluxo de trabalho pode permanecer na memória em estado ocioso antes de ser descarregado forçada ou anulada. Se tiver o workflowruntime `PersistenceService` que executa unloadOnIdle, esse atributo é ignorado.|  
|enablePerformanceCounters|Um valor booleano opcional que especifica se os contadores de desempenho estão habilitados. Contadores de desempenho fornecem informações sobre várias estatísticas relacionadas ao fluxo de trabalho, mas elas causam uma penalidade de desempenho quando o mecanismo de tempo de execução do fluxo de trabalho é iniciado, e quando as instâncias de fluxo de trabalho estão em execução. O valor padrão é `true`.|  
|name|Uma cadeia de caracteres que contém o nome do mecanismo de tempo de execução do fluxo de trabalho. O nome é usado na saída para distinguir esse tempo de execução de outros tempos de execução podem estar em execução no sistema, por exemplo, nos contadores de desempenho.<br /><br /> O padrão é uma cadeia de caracteres vazia.|  
|validateOnCreate|Um valor booleano opcional que especifica se a validação da definição de fluxo de trabalho ocorrerá quando o WorkflowServiceHost for aberto.  Quando esse atributo é definido como `true`, a validação do fluxo de trabalho é executada sempre que `WorkflowServiceHost.Open` é chamado. Se forem encontrados erros de validação, um <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> erro será lançado.<br /><br /> Quando essa propriedade é definida como `false`, não ocorrerá nenhuma validação de definição de fluxo de trabalho.<br /><br /> O valor padrão dessa propriedade é `true`.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|commonParameters|Uma coleção de parâmetros comuns usados pelos serviços. Normalmente, essa coleção incluirá a cadeia de caracteres de conexão de banco de dados que pode ser compartilhada com serviços duráveis.|  
|serviços|Uma coleção de serviços que serão adicionados para o <xref:System.Workflow.Runtime.WorkflowRuntime> mecanismo. Os elementos são do tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  Os serviços especificados na coleção serão inicializados pelo mecanismo de tempo de execução de fluxo de trabalho e adicionados para seus serviços quando apropriado <xref:System.Workflow.Runtime.WorkflowRuntime> construtor seja chamado. Portanto, os serviços especificados na coleção devem seguir determinadas regras sobre as assinaturas dos seus construtores. Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<comportamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um elemento de comportamento.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre como usar um arquivo de configuração para controlar o comportamento de um <xref:System.Workflow.Runtime.WorkflowRuntime> objeto de um aplicativo de host do Windows Workflow Foundation, consulte [arquivos de configuração do fluxo de trabalho](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).  
  
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
 [Arquivos de configuração do fluxo de trabalho](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)
