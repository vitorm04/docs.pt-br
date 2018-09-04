---
title: Rastreamento personalizada
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: c986d9845bb76219ad8b0657a3a7252aaaf4c6cd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43533764"
---
# <a name="custom-tracking"></a>Rastreamento personalizada
Este exemplo demonstra como criar um participante personalizado de rastreamento e gravar o conteúdo dos dados de acompanhamento no console. Além disso, o exemplo demonstra como emitir os objetos de <xref:System.Activities.Tracking.CustomTrackingRecord> preenchido com dados definidos pelo usuário. O participante controlando console- base filtra os objetos de <xref:System.Activities.Tracking.TrackingRecord> emissores pelo fluxo de trabalho usando um objeto de perfil de rastreamento criado em código.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Windows Workflow Foundation (WF) fornece uma infraestrutura de acompanhamento para controlar a execução de uma instância de fluxo de trabalho. O tempo de execução de rastreamento implementa uma instância de fluxo de trabalho para emitir os eventos relacionados ao ciclo de vida de fluxo de trabalho, os eventos de atividades de fluxo de trabalho e eventos personalizados de rastreamento. A tabela a seguir detalha os componentes principais de infraestrutura de rastreamento.  
  
|Componente|Descrição|  
|---------------|-----------------|  
|Tempo de execução de rastreamento|Fornece a infraestrutura para emitir registros de rastreamento.|  
|Participantes de rastreamento|Consome os registros de rastreamento. vem de[!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] com um participante de rastreamento que grava registros de rastreamento como o rastreamento de evento para eventos do Windows (ETW).|  
|Controlando o perfil|Um mecanismo de filtragem que permite que um participante de rastreamento assine para um subconjunto de registros de rastreamento emissores de uma instância de fluxo de trabalho.|  
  
 A tabela a seguir detalha os registros de rastreamento que o tempo de execução de fluxo de trabalho se emite.  
  
|Registro de Rastreamento|Descrição|  
|---------------------|-----------------|  
|Registros de rastreamento de instância de fluxo de trabalho.|Descreve o ciclo de vida de instância de fluxo de trabalho. Por exemplo, um registro de instância é emitida quando o fluxo de trabalho inicia ou termina.|  
|Estado da atividade que acompanha registros.|Detalha a execução da atividade. Esses registros indicam o estado de uma atividade de fluxo de trabalho como quando uma atividade é agendada ou quando a atividade completa ou quando uma falha é lançada.|  
|Registro de ressunção do indexador.|Emitido sempre que um marcador em uma instância de fluxo de trabalho que é.|  
|Registros personalizados de rastreamento.|Um autor de fluxo de trabalho pode criar registros personalizados de rastreamento e emitir os dentro da atividade personalizado.|  
  
 O participante de rastreamento assinatura para um subconjunto dos objetos emissores de <xref:System.Activities.Tracking.TrackingRecord> usando perfis de rastreamento. Um perfil de rastreamento contém consultas de rastreamento que permitem assinar para um tipo de registro específico de rastreamento. Controlar perfis pode ser especificado no código ou na configuração.  
  
### <a name="custom-tracking-participant"></a>Participante de rastreamento personalizada  
 O participante API de rastreamento permite a extensão de rastreamento com um usuário fornecido pelo participante que pode incluir a lógica personalizada para manipular os objetos de <xref:System.Activities.Tracking.TrackingRecord> emissores em tempo de execução de fluxo de trabalho.  
  
 Para gravar um participante de rastreamento o usuário deve implementar <xref:System.Activities.Tracking.TrackingParticipant>. Especificamente, o método de <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> precisa ser implementado por participante personalizado. Este método é chamado quando <xref:System.Activities.Tracking.TrackingRecord> é emitida em tempo de execução de fluxo de trabalho.  
  
```csharp  
public abstract class TrackingParticipant  
{  
    protected TrackingParticipant();  
  
    public virtual TrackingProfile TrackingProfile { get; set; }  
    public abstract void Track(TrackingRecord record, TimeSpan timeout);  
}  
```  
  
 O participante completo de rastreamento é implementado no arquivo de ConsoleTrackingParticipant.cs. O exemplo de código é o método de <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> para o participante personalizado de rastreamento.  
  
```csharp  
protected override void Track(TrackingRecord record, TimeSpan timeout)  
{  
    ...             
    WorkflowInstanceRecord workflowInstanceRecord = record as WorkflowInstanceRecord;  
    if (workflowInstanceRecord != null)  
    {  
        Console.WriteLine(String.Format(CultureInfo.InvariantCulture,  
            " Workflow InstanceID: {0} Workflow instance state: {1}",  
            record.InstanceId, workflowInstanceRecord.State));  
    }  
  
    ActivityStateRecord activityStateRecord = record as ActivityStateRecord;  
    if (activityStateRecord != null)  
    {  
        IDictionary<String, object> variables = activityStateRecord.Variables;  
        StringBuilder vars = new StringBuilder();  
  
        if (variables.Count > 0)  
        {  
            vars.AppendLine("\n\tVariables:");  
            foreach (KeyValuePair<string, object> variable in variables)  
            {     
                vars.AppendLine(String.Format(  
                    "\t\tName: {0} Value: {1}", variable.Key, variable.Value));  
            }  
        }  
        Console.WriteLine(String.Format(CultureInfo.InvariantCulture,  
            " :Activity DisplayName: {0} :ActivityInstanceState: {1} {2}",  
                activityStateRecord.Activity.Name, activityStateRecord.State,  
            ((variables.Count > 0) ? vars.ToString() : String.Empty)));  
    }  
  
    CustomTrackingRecord customTrackingRecord = record as CustomTrackingRecord;  
  
    if ((customTrackingRecord != null) && (customTrackingRecord.Data.Count > 0))  
    {  
        ...  
    }  
    Console.WriteLine();  
  
}  
```  
  
 O exemplo de código a seguir adiciona o participante de console para o solicitante de fluxo de trabalho.  
  
```csharp  
ConsoleTrackingParticipant customTrackingParticipant = new ConsoleTrackingParticipant()  
{  
    ...  
    // The tracking profile is set here, refer to Program.CS  
...  
}  
  
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());  
invoker.Extensions.Add(customTrackingParticipant);  
```  
  
### <a name="emitting-custom-tracking-records"></a>Emitindo registros de rastreamento personalizadas  
 Este exemplo também demonstra a capacidade de emitir objetos de <xref:System.Activities.Tracking.CustomTrackingRecord> de uma atividade personalizado de fluxo de trabalho:  
  
-   Os objetos de <xref:System.Activities.Tracking.CustomTrackingRecord> são criados e preenchido com dados definidos pelo usuário que são desejados ser emitidos com o registro.  
  
-   O <xref:System.Activities.Tracking.CustomTrackingRecord> é emitida chamando o método de controle do <xref:System.Activities.ActivityContext>.  
  
 O exemplo a seguir demonstra como emitir objetos de <xref:System.Activities.Tracking.CustomTrackingRecord> dentro de uma atividade personalizado.  
  
```csharp  
// Create the Custom Tracking Record  
CustomTrackingRecord customRecord = new CustomTrackingRecord("OrderIn")  
{  
    Data =   
    {  
        {"OrderId", 200},  
        {"OrderDate", "20 Aug 2001"}  
    }  
};  
  
// Emit custom tracking record  
context.Track(customRecord);  
```  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de CustomTrackingSample.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a>Consulte também  
 [AppFabric que monitora exemplos](https://go.microsoft.com/fwlink/?LinkId=193959)
