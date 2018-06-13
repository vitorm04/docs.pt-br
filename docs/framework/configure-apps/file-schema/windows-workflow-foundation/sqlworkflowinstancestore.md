---
title: '&lt;sqlWorkflowInstanceStore&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
ms.openlocfilehash: 223108502395311f0db19753addc2a3f2345beac
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757873"
---
# <a name="ltsqlworkflowinstancestoregt"></a>&lt;sqlWorkflowInstanceStore&gt;
Um comportamento de serviço que permite configurar o recurso <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, que dá suporte a informações de estado persistentes para instâncias de serviço de fluxo de trabalho em um banco de dados do SQL Server 2005 ou do SQL Server 2008. Para obter mais informações sobre esse recurso, consulte [armazenamento de instância de fluxo de trabalho do SQL](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).  
  
\<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors >  
\<comportamento >  
\<sqlWorkflowInstanceStore >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sqlWorkflowInstanceStore connectionStringName="String" 
                                honstLockRenewalPeriod="TimeSpan" 
                                instanceCompletionAction="DeleteNothing/DeleteAll" 
                                instanceEncodingAction="None/GZip" 
                                instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry" 
                                runnableInstancesDetectionPeriod="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|connectionString|Uma cadeia de caracteres que contém uma cadeia de conexão usada para se conectar a um banco de dados de persistência subjacente.|  
|connectionStringName|Uma cadeia de caracteres que contém uma cadeia de caracteres de conexão nomeada para o servidor de banco de dados. Um exemplo de uma cadeia de caracteres de conexão nomeada é "DefaultConnectionString".|  
|honstLockRenewalPeriod|Um valor de Timespan que especifica o período de tempo em que o host deve renovar o bloqueio em uma instância. Se o host não renova o bloqueio no período de tempo especificado, a instância é desbloqueada e pode ser selecionada por outro host.<br /><br /> Descarregar um fluxo de trabalho significa que ele também é mantido. Se esse atributo for definido como zero, a instância de fluxo de trabalho é mantida e carregada imediatamente após o fluxo de trabalho se torna ocioso. Definir esse atributo como TimeSpan. MaxValue efetivamente desabilita a operação. Instâncias de fluxo de trabalho ocioso nunca são descarregadas.|  
|instanceCompletionAction|Um valor que especifica se os dados da instância de fluxo de trabalho são mantidos no armazenamento de persistência depois que a instância de fluxo de trabalho seja concluída ou se ele for excluído nesse ponto. Esse valor é do tipo <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.<br /><br /> As ações enumeradas consistem em Excluir os dados da instância do armazenamento de persistência ou não excluir os dados da instância do armazenamento de persistência, quando a instância concluiu sua operação.<br /><br /> Manter instâncias após conclusão faz com que o banco de dados de persistência crescer rapidamente e isso afeta o desempenho do banco de dados. Você deve configurar uma política de limpeza do banco de dados para excluir esses registros periodicamente para garantir que o desempenho do banco de dados está no nível que atender às suas necessidades de desempenho.|  
|instanceEncodingOption|Um valor opcional que especifica se as informações de estado da instância são compactadas usando o algoritmo de GZip antes que as informações são salvas no armazenamento de persistência. Esse valor é do tipo `System.Activities.DurableInstancing.InstanceEncodingAction`. Os valores possíveis para essa propriedade são "None", que não especifica nenhuma compactação e "GZip", que especifica a essa instância de dados são compactados e usa o algoritmo gzip.|  
|instanceLockedExceptionAction|Um valor que especifica a ação que ocorre em resposta a uma exceção que é lançada quando o host tenta bloquear uma instância porque a instância está atualmente bloqueada por outro host. Esse valor é do tipo <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.<br /><br /> As opções permitidas para este campo são: None, repetição básica e repita agressiva. O valor padrão é None. A lista a seguir fornece descrições para esses três opções:<br /><br /> – Nenhum. O host de serviço não tenta bloquear a instância e passa o <xref:System.Runtime.DurableInstancing.InstanceLockedException> ao chamador.<br />-Repetição básica. O host de serviço reattempts bloquear a instância com um intervalo de repetição linear e passa a exceção para o chamador no final da sequência.<br />-Repetição agressiva. Reattempts de host do serviço bloquear a instância com um atraso cresce exponencialmente e passa o <xref:System.Runtime.DurableInstancing.InstanceLockedException> ao chamador no final da sequência.|  
|runnableInstancesDetectionPeriod||  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<comportamento > de \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Especifica um elemento de comportamento.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>  
 [Repositório de instâncias de fluxo de trabalho do SQL](../../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)
