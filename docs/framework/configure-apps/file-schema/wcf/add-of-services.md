---
title: <add> de <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: dc769097a3aede2522c1fa7a4cf8e36c2d8fdfe8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398286"
---
# <a name="add-of-services"></a>\<Adicionar > de \<serviços >
Especifica as configurações para uma instância <xref:System.Workflow.Runtime.WorkflowRuntime> do para hospedar serviços de Windows Communication Foundation baseado em fluxo de trabalho (WCF). Esse elemento é do tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de workflowRuntime**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Serviços >** ](services-of-workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<workflowRuntime>
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
|tipo|Uma cadeia de caracteres que especifica o nome do tipo qualificado por assembly do serviço a ser inicializado. O serviço especificado deve seguir determinadas regras sobre as assinaturas de seus construtores. Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Serviços >](services-of-workflowruntime.md)|Uma coleção de serviços que serão adicionados ao <xref:System.Workflow.Runtime.WorkflowRuntime> mecanismo. Os elementos são do tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  Os serviços especificados na coleção serão inicializados pelo mecanismo de tempo de execução do fluxo de trabalho e adicionados aos seus <xref:System.Workflow.Runtime.WorkflowRuntime> serviços quando o construtor apropriado for chamado. Portanto, os serviços especificados na coleção devem seguir determinadas regras sobre as assinaturas de seus construtores. Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.|  
  
## <a name="remarks"></a>Comentários  
 O serviço especificado neste elemento será inicializado pelo mecanismo de tempo de execução do fluxo de trabalho e adicionado aos seus <xref:System.Workflow.Runtime.WorkflowRuntime> serviços quando o construtor apropriado for chamado. Portanto, o serviço especificado deve seguir determinadas regras sobre as assinaturas de seus construtores. Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<serviceBehaviors>
  <behavior name="ServiceBehavior">
    <workflowRuntime name="WorkflowServiceHostRuntime"
                     validateOnCreate="true"
                     enablePerformanceCounters="true">
      <services>
        <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common" />
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
