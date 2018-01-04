---
title: 'Como: Crie um modelo personalizado de atividades'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 772ad2a7ea56001bf3ecba089e62d6bc0f59e5ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-activity-template"></a>Como: Crie um modelo personalizado de atividades
Modelos personalizados de atividade são usados para personalizar a configuração de atividades, incluindo atividades compostas personalizados, para que os usuários não tem que criar cada atividade individualmente e configurar suas propriedades e outras configurações manualmente. Esses modelos personalizados podem ser disponibilizados no **caixa de ferramentas** no [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] ou de um designer de rehosted, do qual os usuários podem arrastá-los na superfície de design pré-configurado. [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]acompanha Bons exemplos de tais modelos: o [Designer de modelo de SendAndReceiveReply](/visualstudio/workflow-designer/sendandreceivereply-template-designer) e [Designer de modelo de ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer) no [Designersdeatividadedemensagens](/visualstudio/workflow-designer/messaging-activity-designers) categoria.  
  
 O primeiro procedimento neste tópico descreve como criar um modelo de atividade personalizada para um **atraso** atividade e o segundo procedimento descreve brevemente como disponibilizá-lo em um [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] para verificar se o modelo personalizado funciona.  
  
 Modelos personalizados de atividade devem implementar <xref:System.Activities.Presentation.IActivityTemplateFactory>. A interface possui um único método de <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> com que você pode criar e configurar as instâncias da atividade usadas no modelo.  
  
### <a name="to-create-a-template-for-the-delay-activity"></a>Para criar um modelo para atividades de atraso  
  
1.  Inicie o [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Sobre o **arquivo** , aponte para **novo**e, em seguida, selecione **projeto**.  
  
     A caixa de diálogo **Novo Projeto** é aberta.  
  
3.  No **tipos de projeto** painel, selecione **fluxo de trabalho** do **Visual C#** projetos ou **Visual Basic** agrupamentos dependendo de sua preferência de idioma.  
  
4.  No **modelos** painel, selecione **biblioteca de atividades**.  
  
5.  No **nome** , digite `DelayActivityTemplate`.  
  
6.  Aceite os padrões no **local** e **nome da solução** caixas de texto e clique **Okey**.  
  
7.  Clique o diretório de referências do projeto em DelayActivityTemplate **Solution Explorer** e escolha **adicionar referência** para abrir o **adicionar referência** caixa de diálogo.  
  
8.  Vá para o **.NET** guia e selecione **PresentationFramework** do **nome do componente** coluna à esquerda e clique em **Okey** para adicionar uma referência para o arquivo PresentationFramework. dll.  
  
9. Repita este procedimento para adicionar referências para System.Activities.Presentation.dll e arquivos de WindowsBase.dll.  
  
10. Com o botão direito no projeto DelayActivityTemplate no **Solution Explorer** e escolha **adicionar** e **Novo Item** para abrir o **Adicionar Novo Item**caixa de diálogo.  
  
11. Selecione o **classe** modelo, nomeie-o MyDelayTemplate e, em seguida, clique em **Okey**.  
  
12. Abra o arquivo de MyDelayTemplate.cs e adicione as instruções a seguir.  
  
    ```  
    //Namespaces added  
    using System.Activities;  
    using System.Activities.Statements;  
    using System.Activities.Presentation;  
    using System.Windows;  
    ```  
  
13. Implementar <xref:System.Activities.Presentation.IActivityTemplateFactory> com a classe de `MyDelayActivity` com o código a seguir. Isso configura o atraso para ter uma duração de 10 segundos.  
  
    ```  
    public sealed class MyDelayActivity : IActivityTemplateFactory  
    {  
        public Activity Create(System.Windows.DependencyObject target)  
        {  
            return new System.Activities.Statements.Delay  
            {  
                DisplayName = "DelayActivityTemplate",  
                Duration = new TimeSpan(0, 0, 10)  
  
            };  
        }  
    }  
    ```  
  
14. Selecione **compilar solução** do **criar** menu para gerar o arquivo DelayActivityTemplate.dll.  
  
### <a name="to-make-the-template-available-in-a-workflow-designer"></a>Para fazer o modelo disponível em Designer de Fluxo de Trabalho  
  
1.  Clique com botão direito da solução de DelayActivityTemplate **Gerenciador de soluções** e escolha **adicionar** e, em seguida, **novo projeto** para abrir o **adicionar novo projeto** caixa de diálogo.  
  
2.  Selecione o **aplicativo de Console do fluxo de trabalho** modelo, nomeie-o `CustomActivityTemplateApp`e, em seguida, clique em **Okey**.  
  
3.  Clique o diretório de referências do projeto em CustomActivityTemplateApp **Solution Explorer** e escolha **adicionar referência** para abrir o **adicionar referência** caixa de diálogo caixa.  
  
4.  Vá para o **projetos** guia e selecione **DelayActivityTemplate** do **nome do projeto** coluna à esquerda e clique em **Okey** para adicionar um fazer referência ao arquivo DelayActivityTemplate.dll que você criou no primeiro procedimento.  
  
5.  Clique com botão direito no projeto CustomActivityTemplateApp no **Solution Explorer** e escolha **Build** para compilar o aplicativo.  
  
6.  Clique com botão direito no projeto CustomActivityTemplateApp no **Solution Explorer** e escolha **definir como projeto de inicialização**.  
  
7.  Selecione **Start Without Debugging** do **depurar** menu e pressione qualquer tecla para continuar quando solicitado na janela de cmd.exe.  
  
8.  Abra o arquivo Workflow1.xaml e o **caixa de ferramentas**.  
  
9. Localize o **MyDelayActivity** modelo o **DelayActivityTemplate** categoria. Arraste-o para a superfície de design. Confirme no **propriedades** janela que o `Duration` propriedade foi definida como 10 segundos.  
  
## <a name="example"></a>Exemplo  
 O arquivo de MyDelayActivity.cs deve conter o código a seguir.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
//Namespaces added  
using System.Activities;  
using System.Activities.Statements;  
using System.Activities.Presentation;  
using System.Windows;  
  
namespace DelayActivityTemplate  
{  
    public sealed class MyDelayActivity : IActivityTemplateFactory  
    {  
        public Activity Create(System.Windows.DependencyObject target)  
        {  
            return new System.Activities.Statements.Delay  
            {  
                DisplayName = "DelayActivityTemplate",  
                Duration = new TimeSpan(0, 0, 10)  
  
            };  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Activities.Presentation.IActivityTemplateFactory>  
 [Personalizando a experiência de design de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)
