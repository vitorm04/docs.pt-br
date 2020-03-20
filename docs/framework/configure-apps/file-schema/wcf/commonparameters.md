---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 73d8549f68e8ca77115619431c857c4a2aac3fdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153016"
---
# <a name="commonparameters"></a>\<parâmetros comuns>
Representa uma coleção de parâmetros que são usados globalmente em vários serviços. Essa coleção normalmente incluirá a seqüência de conexão de banco de dados que pode ser compartilhada por serviços duráveis.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModelo>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportamentos>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviçocomportamentos>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportamento>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<fluxo de trabalho>detempo de execução**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parâmetros comuns>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<adicionar>](add-of-commonparameters.md)|Adiciona um par de parâmetros comuns usados pelos serviços à coleção.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<fluxo de trabalho>detempo de execução](workflowruntime.md)|Especifica configurações para uma <xref:System.Workflow.Runtime.WorkflowRuntime> instância de hospedagem de serviços wcf baseados em fluxo de trabalho baseados no Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Comentários  
 O `<commonParameters>` elemento define quaisquer parâmetros que são usados `ConnectionString` globalmente <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>em vários serviços, por exemplo, ao usar o .  
  
> [!NOTE]
> O serviço sql tracking não `ConnectionString` usa consistentemente o `<commonParameters>` valor se for especificado na seção. Algumas de suas operações, `StateMachineWorkflowInstance.StateHistory` como recuperar a propriedade, podem falhar. Para contornar isso, `ConnectionString` especifique o atributo na seção de configuração para o provedor de rastreamento, conforme indicado no exemplo a seguir.  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 Para serviços que comprometem lotes de <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> trabalho <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>em lojas de persistência, como e `EnableRetries` , você pode permitir que eles tritimem novamente sua transação usando o parâmetro como mostrado no exemplo a seguir:  
  
```xml  
<workflowRuntime name="SampleApplication"
                 unloadOnIdle="false">
  <commonParameters>
    <add name="ConnectionString"
         value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
    <add name="EnableRetries"
         value="True" />
  </commonParameters>
  <services>
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime,
               Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 Observe que `EnableRetries` o parâmetro pode ser definido em nível global (como mostrado na seção *CommonParameters)* ou para serviços individuais que suportam `EnableRetries` (como mostrado na seção *Serviços).*  
  
 O código de amostra a seguir mostra como alterar os parâmetros comuns de forma programática:
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 Para obter mais informações sobre o uso <xref:System.Workflow.Runtime.WorkflowRuntime> de um arquivo de configuração para controlar o comportamento de um objeto de um aplicativo de host do Windows Workflow Foundation, consulte [Arquivos de configuração do fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).  
  
## <a name="example"></a>Exemplo  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- [Arquivos de configuração do fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
- [\<adicionar>](add-of-commonparameters.md)
