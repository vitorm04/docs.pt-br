---
title: Atividade de política no .NET Framework 4.5
ms.date: 03/30/2017
ms.assetid: 8e375e0c-d7c1-4d69-88ab-36d52db0aa7e
ms.openlocfilehash: 9d8983f2f1d3f75beffeacfff4b673f6c23c4204
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44048062"
---
# <a name="policy-activity-in-net-framework-45"></a>Atividade de política no .NET Framework 4.5
A atividade Policy4 permite que o Windows Workflow Foundation no [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3,5) <xref:System.Workflow.Activities.Rules.RuleSet> objetos para serem usados no Windows Workflow Foundation no [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (4,5 WCF) diretamente usando o mecanismo de regras que é enviado em WF 3,5. Usando esta atividade, você pode criar e executar um WF 3,5 <xref:System.Workflow.Activities.Rules.RuleSet>. Para obter mais informações sobre o mecanismo de regras WF 3,5 incluído como parte do Windows Workflow Foundation, leia a introdução ao mecanismo de regras do Windows Workflow Foundation. Para obter mais informações sobre migração regras WF na [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], leia [orientação de migração](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-Policy4`  
  
## <a name="projects-in-this-sample"></a>Projetos nisso exemplo  
  
|Nome do projeto|Descrição|Arquivos de chave|  
|------------------|-----------------|----------------|  
|Policy4|Contém a atividade Policy4 e o designer de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .|**Policy4.CS**: definição de atividade Policy4.<br /><br /> **{1&gt;policydesigner.XAML&lt;1**: designer personalizado para atividades Policy4. Ele usa o editor de regras ([classe de RuleSetDialog](https://go.microsoft.com/fwlink/?LinkId=150378)) de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] mecanismo de regras.|  
|ImperativeCodeClientSample|Aplicativo cliente de exemplo que configura e executa um fluxo de trabalho usando um aplicativo Policy4 usando o código em c obrigatório (nenhum designer de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] usado).|**ApplyDiscount**: arquivo com [!INCLUDE[wf1](../../../../includes/wf1-md.md)] definições de regra.<br /><br /> **{1&gt;Order.CS&lt;1**: tipo que representa um pedido de cliente. As regras são aplicadas a objetos desse tipo.<br /><br /> **Program.CS**: configura e executa um fluxo de trabalho que tem uma atividade Policy4 para aplicar as regras definidas em ApplyDiscount instâncias de objetos pedido.<br /><br /> **App. config**: arquivo de configuração com o caminho do arquivo de regras.|  
|DesignerClientSample|Aplicativo cliente de exemplo que configura e executa um fluxo de trabalho usando um aplicativo Policy4 no designer de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .|**Sequence1.XAML**: fluxo de trabalho sequencial que usa uma atividade Policy4 para executar avaliações de regra.<br /><br /> `Program.cs`: Executa uma instância de fluxo de trabalho definido em Sequence1.xaml.|  
  
## <a name="the-policy4-activity"></a>A atividade Policy4  
 A atividade Policy4 é uma classe que deriva de <xref:System.Activities.NativeActivity%601> que permite que fluxos de trabalho para executar [!INCLUDE[wf1](../../../../includes/wf1-md.md)] RuleSets. O exemplo de código é uma definição simplificada de OM utilitário da atividade.  
  
```csharp  
public class Policy4Activity<TResult>: NativeActivity<TResult>  
{  
    public RuleSet RuleSet  
  
    [IsRequired]  
    public InArgument Input  
  
    public OutArgument<ValidationErrorCollection> ValidationErrors  
}  
```  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|RuleSet|O WF [classe de RuleSet](https://go.microsoft.com/fwlink/?LinkId=150379) do .NET Framework 3.5 é avaliado quando a atividade é executada.|  
|TargetObject|O objeto em que as regras a [classe de RuleSet](https://go.microsoft.com/fwlink/?LinkId=150379) são avaliadas.|  
|ValidationError|A lista de erros de validação retornado pelo [!INCLUDE[wf1](../../../../includes/wf1-md.md)] mecanismo de regra para o .NET Framework 3.5 para validar a [classe de RuleSet](https://go.microsoft.com/fwlink/?LinkId=150379) contra o objeto de destino antes da execução.|  
  
## <a name="policy4-activity-designer"></a>Designer de atividade Policy4  
 O designer adiciona Policy4 o recurso configurar uma atividade Policy4 sem a necessidade de escrever código. Após compilar a solução, ele pode ser encontrado na caixa de ferramentas na seção **Rules**.  
  
 O designer de WF permite que você configure um objeto alvo e um RuleSet. Quando o **edição RuleSet** botão é clicado, o WF [classe de RuleSetDialog](https://go.microsoft.com/fwlink/?LinkId=150378) para [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] é exibida. Esta caixa de diálogo é o editor hospedado novamente regras de [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] . Use o editor para criar e editar as regras que a atividade Policy4 executa.  
  
## <a name="using-this-sample"></a>Usando este exemplo  
 Qualquer configuração especial é necessária para executar este exemplo. Abra apenas a solução no Visual Studio, e pressione F5 para executar o aplicativo.  
  
 Este exemplo contém dois aplicativos cliente: ImperativeCodeClientSample e DesignerClientSample. Mostra de cliente de ImperativeCodeClientSample como configurar e executar a atividade Policy40 usando o código obrigatório C#. Mostra como configurar de DesignerClientSample e executar a atividade Policy4 usando o designer.  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>Para executar o aplicativo cliente de ImperativeCodeClientSample  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução de Policy4Sample.sln.  
  
2.  Na **Gerenciador de soluções**, clique com botão direito do **ImperativeCodeClientSample** do projeto e, em seguida, selecione **definir como projeto de inicialização**.  
  
3.  Para executar o projeto, pressione CTRL+F5.  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a>Para executar o aplicativo cliente de ImperativeCodeClientSample  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução de Policy4Sample.sln.  
  
2.  Na **Gerenciador de soluções**, clique com botão direito do **DesignerClientSample** projeto.  
  
    -   Selecione **definir como projeto de inicialização**.  
  
3.  Para compilar o projeto, pressione CTRL+SHIFT+B.  
  
4.  Para executar o projeto, pressione CTRL+F5.