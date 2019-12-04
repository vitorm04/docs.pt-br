---
title: 'Como: Crie um modelo personalizado de atividades'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: f910d1367c941dbc319421d402cae8f4194872e5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715247"
---
# <a name="how-to-create-a-custom-activity-template"></a>Como: Crie um modelo personalizado de atividades

Modelos personalizados de atividade são usados para personalizar a configuração de atividades, incluindo atividades compostas personalizados, para que os usuários não tem que criar cada atividade individualmente e configurar suas propriedades e outras configurações manualmente. Esses modelos personalizados podem ser disponibilizados na **caixa de ferramentas** do Windows designer de fluxo de trabalho ou em um designer rehospedado, do qual os usuários podem arrastá-los para a superfície de design pré-configurada. Designer de Fluxo de Trabalho vem com bons exemplos de modelos: o [Designer de modelos SendAndReceiveReply](/visualstudio/workflow-designer/sendandreceivereply-template-designer) e o [Designer de modelos ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer) na categoria [designers de atividade de mensagens](/visualstudio/workflow-designer/messaging-activity-designers) .

 O primeiro procedimento neste tópico descreve como criar um modelo de atividade personalizada para uma atividade de **atraso** e o segundo procedimento descreve brevemente como disponibilizá-lo em um designer de fluxo de trabalho para verificar se o modelo personalizado funciona.

 Modelos personalizados de atividade devem implementar <xref:System.Activities.Presentation.IActivityTemplateFactory>. A interface possui um único método de <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> com que você pode criar e configurar as instâncias da atividade usadas no modelo.

## <a name="to-create-a-template-for-the-delay-activity"></a>Para criar um modelo para atividades de atraso

1. Inicie o Visual Studio 2010.

2. No menu **Arquivo**, aponte para **Novo** e selecione **Projeto**.

     A caixa de diálogo **Novo Projeto** é aberta.

3. No painel **tipos de projeto** , selecione **fluxo de trabalho** nos **projetos C# visuais** ou **Visual Basic** agrupamentos, dependendo da sua preferência de idioma.

4. No painel **modelos** , selecione **biblioteca de atividades**.

5. Na caixa **nome** , digite `DelayActivityTemplate`.

6. Aceite os padrões nas caixas de texto **nome da solução** e **local** e clique em **OK**.

7. Clique com o botão direito do mouse no diretório References do projeto DelayActivityTemplate em **Gerenciador de soluções** e escolha **Adicionar referência** para abrir a caixa de diálogo **Adicionar referência** .

8. Vá para a guia **.net** e selecione **PresentationFramework** na coluna **nome do componente** à esquerda e clique em **OK** para adicionar uma referência ao arquivo PresentationFramework. dll.

9. Repita este procedimento para adicionar referências para System.Activities.Presentation.dll e arquivos de WindowsBase.dll.

10. Clique com o botão direito do mouse no projeto DelayActivityTemplate no **Gerenciador de soluções** e escolha **Adicionar** e **novo item** para abrir a caixa de diálogo **Adicionar novo item** .

11. Selecione o modelo de **classe** , nomeie-o mydelaytemplate e clique em **OK**.

12. Abra o arquivo de MyDelayTemplate.cs e adicione as instruções a seguir.

    ```csharp
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. Implementar <xref:System.Activities.Presentation.IActivityTemplateFactory> com a classe de `MyDelayActivity` com o código a seguir. Isso configura o atraso para ter uma duração de 10 segundos.

    ```csharp
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

14. Selecione **Compilar solução** no menu **Compilar** para gerar o arquivo DelayActivityTemplate. dll.

### <a name="to-make-the-template-available-in-a-workflow-designer"></a>Para fazer o modelo disponível em Designer de Fluxo de Trabalho

1. Clique com o botão direito do mouse na solução DelayActivityTemplate em **Gerenciador de soluções** e escolha **Adicionar** e **novo projeto** para abrir a caixa de diálogo **Adicionar novo projeto** .

2. Selecione o modelo de **aplicativo do console de fluxo de trabalho** , nomeie-o `CustomActivityTemplateApp`e clique em **OK**.

3. Clique com o botão direito do mouse no diretório References do projeto CustomActivityTemplateApp em **Gerenciador de soluções** e escolha **Adicionar referência** para abrir a caixa de diálogo **Adicionar referência** .

4. Vá para a guia **projetos** e selecione **DelayActivityTemplate** na coluna **nome do projeto** à esquerda e clique em **OK** para adicionar uma referência ao arquivo DelayActivityTemplate. dll que você criou no primeiro procedimento.

5. Clique com o botão direito do mouse no projeto CustomActivityTemplateApp no **Gerenciador de soluções** e escolha **Compilar** para compilar o aplicativo.

6. Clique com o botão direito do mouse no projeto CustomActivityTemplateApp em **Gerenciador de soluções** e escolha **definir como projeto de inicialização**.

7. Selecione **Iniciar sem depuração** no menu **depurar** e pressione qualquer tecla para continuar quando solicitado na janela cmd. exe.

8. Abra o arquivo workflow1. XAML e abra a **caixa de ferramentas**.

9. Localize o modelo **MyDelayActivity** na categoria **DelayActivityTemplate** . Arraste-o para a superfície de design. Confirme na janela **Propriedades** que a propriedade `Duration` foi definida como 10 segundos.

## <a name="example"></a>Exemplo
 O arquivo de MyDelayActivity.cs deve conter o código a seguir.

```csharp
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

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [Personalizando a experiência de design de fluxo de trabalho](customizing-the-workflow-design-experience.md)
