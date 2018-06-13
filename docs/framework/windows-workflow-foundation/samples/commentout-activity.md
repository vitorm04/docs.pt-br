---
title: Atividade de CommentOut
ms.date: 03/30/2017
ms.assetid: 340204c3-f827-45fb-870e-55e2ac457ca5
ms.openlocfilehash: 7847f4e1d77c2927a27be6b83f4016a22e4e3b32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515190"
---
# <a name="commentout-activity"></a>Atividade de CommentOut
Este exemplo demonstra como escrever uma atividade personalizado que remove outras atividades do caminho de execução, comentando efetivamente eles para fora.  
  
## <a name="the-commentout-activity"></a>A atividade de CommentOut  
 Para obter o objetivo, a atividade de CommentOut deriva de classe base de <xref:System.Activities.CodeActivity> e implementa-se um método vazia de <xref:System.Activities.CodeActivity.Execute%2A> .  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 A classe é declarada como mostrado no exemplo a seguir.  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 O atributo de `Designer` especifica a classe que implementa a interface visual de atividade em tempo de design. O `ContentProperty` atributo declara que o `"Body"` propriedade pode ser ignorada na representação XAML de uma instância dessa atividade.  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 Na classe de designer, XAML é usado para criar uma representação visual personalizado de atividade. <xref:System.Activities.Presentation.WorkflowItemPresenter> é uma classe que fornece o editor visual.  
  
 Uma única atividade pode ser levada na superfície de atividade de `CommentOut` . Se você deseja adicionar vários atividades à superfície, arraste uma atividade da sequência aqui primeiro.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra CommentOut.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Crie a solução. CTRL+SHIFT+B pressionando.  
  
3.  Inicie o exemplo sem depuração pressionando CTRL + f5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
