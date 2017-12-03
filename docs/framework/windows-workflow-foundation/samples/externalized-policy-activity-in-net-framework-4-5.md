---
title: "Atividade exteriorizada de política no .NET Framework 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92fd6f92-23a1-4adf-b96a-2754ea93ad3e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 468d0ca5f4afa4e84b69f58887672ffcf1a14fa6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="externalized-policy-activity-in-net-framework-45"></a>Atividade exteriorizada de política no .NET Framework 4.5
Este exemplo demonstra como a atividade ExternalizedPolicy4 permite executar existente [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] [!INCLUDE[wf2](../../../../includes/wf2-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objetos no [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] [!INCLUDE[wf2](../../../../includes/wf2-md.md)] (WF 4.5) usando o mecanismo de regras que é enviado em WF 3.5. Usando esta atividade, você pode abrir e executar qualquer WF existente <xref:System.Workflow.Activities.Rules.RuleSet>3,5. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Leia do mecanismo de regras incluídos como parte do Windows Workflow Foundation, WF 3.5 [introdução para o mecanismo de regras do Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkId=166079). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]regras de migração para [!INCLUDE[wf1](../../../../includes/wf1-md.md)] na [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], leia as diretrizes de migração em [orientação de migração](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md).  
  
## <a name="projects-in-this-sample"></a>Projetos nisso exemplo  
  
|Nome do projeto|Descrição|Arquivos de chave|  
|-|-|-|  
|ExternalizedPolicy4|Contém a atividade ExternalizedPolicy4 e o designer de WF 4,5.|**ExternalizedPolicy4.cs**: definição de atividade.<br /><br /> **ExternalizedPolicy4Designer.xaml**: designer personalizado para a atividade de ExternalizedPolicy4. Usar o editor das regras (<xref:System.Workflow.Activities.Rules.Design.RuleSetDialog>) do mecanismo de regras WF 3,5.|  
|ImperativeCodeClientSample|Aplicativo cliente de exemplo que configura e executa um fluxo de trabalho usando um aplicativo ExternalizedPolicy4 usando o código em c obrigatório (nenhum designer usado).|**ApplyDiscount.rules**: arquivo com [!INCLUDE[wf1](../../../../includes/wf1-md.md)] definições de regra.<br /><br /> **Order.CS**: tipo que representa um pedido do cliente. As regras são aplicadas a objetos desse tipo.<br /><br /> **Program.CS**: configura e executa um fluxo de trabalho que tem uma atividade de Policy4 para aplicar as regras definidas no ApplyDiscount.rules para instâncias de objetos de ordem.<br /><br /> App.config: O arquivo de configuração com o caminho do arquivo de regras.|  
|DesignerClientSample|Aplicativo cliente de exemplo que configura e executa um fluxo de trabalho usando um aplicativo ExternalPolicy4 no designer de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .|**Sequence1.XAML**: fluxo de trabalho sequencial que usa uma atividade de Policy4 para executar avaliações de regra.<br /><br /> **Program.CS**: executa uma instância do fluxo de trabalho definido em Sequence1.xaml.|  
  
## <a name="the-externalizedpolicy4-activity"></a>A atividade ExternalizedPolicy4  
 A atividade ExternalizedPolicy4 é <xref:System.Activities.NativeActivity> que permite executar objetos de WF 3,5 <xref:System.Workflow.Activities.Rules.RuleSet> dentro de fluxos de trabalho WF 4,5. O exemplo a seguir é uma definição do modelo simplificada de objeto utilitário da atividade.  
  
```  
public class ExternalizedPolicy4Activity<TResult>: CodeActivity  
{  
    public string RulesFilePath   
  
    public string RuleSetName           
  
    [RequiredArgument]  
    public InArgument<T> TargetObject   
  
    [RequiredArgument]  
    public OutArgument<T> ResultObject   
  
    public OutArgument<ValidationErrorCollection> ValidationErrors   
}  
```  
  
|Propriedade|Descrição|  
|-|-|  
|RuleSetFilePath|Caminho para o arquivo do .NET Framework 3.5 <xref:System.Workflow.Activities.Rules.RuleSet> a ser avaliado quando a atividade é executada.|  
|RuleSetName|Nome de <xref:System.Workflow.Activities.Rules.RuleSet> a ser usado dentro do arquivo de .rules.|  
|TargetObject|O objeto em que <xref:System.Workflow.Activities.Rules.Rule> objetos em <xref:System.Workflow.Activities.Rules.RuleSet> é avaliado contra.|  
|ResultObject|O objeto resultante depois que as regras são aplicadas (por exemplo, regras é aplicado no argumento de entrada e o resultado é armazenado no argumento de resultado.|  
|ValidationError|A lista de erros de validação retornado pelo mecanismo de regras WF 3,5 para validar contra <xref:System.Workflow.Activities.Rules.RuleSet> o objeto alvo antes de execução.|  
  
## <a name="externalizedpolicy4-activity-designer"></a>Designer de atividade ExternalizedPolicy4  
 O designer ExternalizedPolicy4 permite que você configure uma atividade para usar um RuleSet existente sem escrever código. Apenas definir o caminho onde o arquivo de .rules é encontrado e especifica o nome de <xref:System.Workflow.Activities.Rules.RuleSet> que você deseja uso. Também permite que você altere <xref:System.Workflow.Activities.Rules.RuleSet>. Após compilar a solução, pode ser encontrado na caixa de ferramentas na seção Microsoft.Samples.Activities.Rules. O designer permite que você selecione um arquivo de .rules e um <xref:System.Workflow.Activities.Rules.RuleSet>. Quando o **Editar conjunto de regras** botão é clicado, o WF 3.5 <xref:System.Workflow.Activities.Rules.Design.RuleSetDialog> é exibido. Esta caixa de diálogo é o editor hospedado novamente de regras WF 3,5 e é usada para exibir e editar as regras que a atividade ExternalizedPolicy4 executa.  
  
## <a name="policy4-and-externalpolicy4"></a>Policy4 e ExternalPolicy4  
 O [atividade de política no .NET Framework 4.5](../../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) atividade permite criar e executar um conjunto de regras do .NET Framework 3.5 em um fluxo de trabalho do WF 4.5. <xref:System.Workflow.Activities.Rules.RuleSet> é embutido serializado Policy4 na definição da atividade XAML. O exemplo ExternalizedPolicy4 mostra como usar <xref:System.Workflow.Activities.Rules.RuleSet> externo existente (contido em um arquivo de .rules).  
  
## <a name="using-this-sample"></a>Usando este exemplo  
 Qualquer configuração especial é necessária para executar este exemplo. Abra a solução em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], e pressione F5 para executar o aplicativo.  
  
 Este exemplo contém dois aplicativos cliente: ImperativeCodeClientSample e DesignerClientSample. O cliente de ImperativeCodeClientSample mostra como configurar e executar a atividade ExternalizedPolicy4 usando o código obrigatório C#. O DesignerClientSample mostra como configurar e executar a atividade ExternalizedPolicy4 usando o designer.  
  
#### <a name="to-run-the-imperativecodeclientsample-application"></a>Para executar o aplicativo de ImperativeCodeClientSample  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução de Policy4sample.sln.  
  
2.  Em **Solution Explorer**, com o botão direito do **ImperativeCodeClientSample** do projeto e, em seguida, selecione **definir como projeto de inicialização**.  
  
3.  Para executar o projeto, pressione CTRL+F5.  
  
#### <a name="to-run-the-designerclientsample-application"></a>Para executar o aplicativo de DesignerClientSample  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução de Policy4sample.sln.  
  
2.  Em **Solution Explorer**, com o botão direito do **DesignerClientSample** do projeto e, em seguida, selecione **definir como projeto de inicialização**.  
  
3.  Pressione CTRL+SHIFT+B para criar o projeto.  
  
4.  Pressione CTRL+F5 para executar o projeto.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-ExternalizedPolicy4`
