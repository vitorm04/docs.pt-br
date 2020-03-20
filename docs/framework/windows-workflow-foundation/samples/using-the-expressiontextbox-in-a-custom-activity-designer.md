---
title: Usando o ExpressionTextBox em um designer personalizado de atividades
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: 6d3df9e18c7239f0e4695509d80edfd02e9a9d6f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182763"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Usando o ExpressionTextBox em um designer personalizado de atividades
Este exemplo mostra como usar <xref:System.Activities.Presentation.View.ExpressionTextBox> em um designer personalizado de atividade. A atividade personalizado, `MultiAssign`, atribui dois valores de cadeia de caracteres a duas variáveis de cadeia de caracteres. Alguns controles de <xref:System.Activities.Presentation.View.ExpressionTextBox> associação a <xref:System.Activities.InArgument>s e associar a qualquer <xref:System.Activities.OutArgument>S.

## <a name="sample-details"></a>Detalhes de exemplo
 `ArgumentToExpressionConverter` é o conversor de tipo usado para associar expressões para argumentos. `ConverterParameter` deve ser definido como `In` ou a `Out` como apropriado. Não há suporte para `InOut`.

 O `UseLocationExpression` atributo `OutArgument`é usado em s para especificar que a expressão deve ser uma expressão de valor L ("valor esquerdo" ou "valor de localização"). Na maioria dos casos, uma expressão de L- valor é um identificador válido Visual Basic usado para indicar que `OutArgument` que está sendo retornado é uma variável ou um nome de argumento.

 O atributo de `MaxLines` é definido como um nesse exemplo e `MinLines` não está definido. Isso indica que <xref:System.Activities.Presentation.View.ExpressionTextBox> é um tamanho fixo de uma linha independentemente da quantidade de texto digitado pelo usuário. Para permitir que <xref:System.Activities.Presentation.View.ExpressionTextBox> venha a entrada do usuário apta, defina `MaxLines` maior do que `MinLines`.

 Um ExpressionTextBox só pode ser associado para argumentos, e não pode ser associado para propriedades de CLR.

#### <a name="to-use-this-sample"></a>Para usar este exemplo

1. Usando o Visual Studio 2010, abra o arquivo ExpressionTextBoxSample.sln.

2. Para criar a solução, pressione CTRL+SHIFT+B.

#### <a name="to-run-this-sample"></a>Para executar este exemplo

1. Adicione um novo aplicativo de console do fluxo de trabalho à solução.

2. Adicione uma referência ao projeto **ExpressionTextBoxSample** do novo projeto Workflow Console Application.

3. Compile a solução.

4. Arraste a atividade **MultiAssign** da caixa de ferramentas e solte-a no fluxo de trabalho.

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Confira também

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [Desenvolvendo aplicativos com o Designer de Fluxo de Trabalho](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
