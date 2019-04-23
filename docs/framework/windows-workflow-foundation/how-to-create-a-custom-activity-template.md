---
title: 'Como: criar um modelo personalizado de atividades'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: ee6f249092c5cf8643e3c9bfd15d32e77791d8bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295842"
---
# <a name="how-to-create-a-custom-activity-template"></a>Como: criar um modelo personalizado de atividades

Modelos personalizados de atividade são usados para personalizar a configuração de atividades, incluindo atividades compostas personalizados, para que os usuários não tem que criar cada atividade individualmente e configurar suas propriedades e outras configurações manualmente. Esses modelos personalizados podem ser disponibilizados na **caixa de ferramentas** no [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] ou um designer rehosted, do qual os usuários podem o arrastar para a superfície de design pré-configurado. [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] é fornecido com bons exemplos desses modelos: o [Designer de modelo de SendAndReceiveReply](/visualstudio/workflow-designer/sendandreceivereply-template-designer) e o [Designer de modelo de ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer) no [Designersdeatividadedemensagens](/visualstudio/workflow-designer/messaging-activity-designers) categoria.

 O primeiro procedimento neste tópico descreve como criar um modelo de atividade personalizada para um **atraso** atividade e o segundo procedimento rapidamente descreve como disponibilizá-lo em um [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] para verificar se o modelo personalizado funciona.

 Modelos personalizados de atividade devem implementar <xref:System.Activities.Presentation.IActivityTemplateFactory>. A interface possui um único método de <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> com que você pode criar e configurar as instâncias da atividade usadas no modelo.

## <a name="to-create-a-template-for-the-delay-activity"></a>Para criar um modelo para atividades de atraso

1. Inicie o Visual Studio 2010.

2. No menu **Arquivo**, aponte para **Novo** e selecione **Projeto**.

     A caixa de diálogo **Novo Projeto** é aberta.

3. No **tipos de projeto** painel, selecione **fluxo de trabalho** de qualquer um os **Visual c#** projetos ou **Visual Basic** agrupamentos dependendo da sua preferência de idioma.

4. No **modelos** painel, selecione **biblioteca de atividades**.

5. No **nome** , digite `DelayActivityTemplate`.

6. Aceite os padrões de **local** e **nome da solução** caixas de texto e clique **Okey**.

7. Clique com botão direito no diretório de referências do projeto de DelayActivityTemplate em **Gerenciador de soluções** e escolha **adicionar referência** para abrir o **Add Reference** caixa de diálogo.

8. Vá para o **.NET** e selecione **PresentationFramework** do **nome do componente** coluna à esquerda e clique em **Okey** para adicionar uma referência para o arquivo de PresentationFramework. dll.

9. Repita este procedimento para adicionar referências para System.Activities.Presentation.dll e arquivos de WindowsBase.dll.

10. Clique com botão direito no projeto de DelayActivityTemplate em **Gerenciador de soluções** e escolha **Add** e, em seguida, **Novo Item** para abrir o **Add New Item**caixa de diálogo.

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

14. Selecione **compilar solução** da **Build** menu para gerar o arquivo de Delayactivitytemplate.

### <a name="to-make-the-template-available-in-a-workflow-designer"></a>Para fazer o modelo disponível em Designer de Fluxo de Trabalho

1. Clique com botão direito na solução de DelayActivityTemplate em **Gerenciador de soluções** e escolha **Add** e, em seguida, **novo projeto** para abrir o **adicionar novo projeto** caixa de diálogo.

2. Selecione o **aplicativo de Console do fluxo de trabalho** modelo, nomeie- `CustomActivityTemplateApp`e, em seguida, clique em **Okey**.

3. Clique com botão direito no diretório de referências de projeto de CustomActivityTemplateApp em **Gerenciador de soluções** e escolha **adicionar referência** para abrir o **Add Reference** caixa de diálogo caixa.

4. Vá para o **projetos** e selecione **DelayActivityTemplate** do **nome do projeto** coluna à esquerda e clique em **Okey** para adicionar um referência para o arquivo de Delayactivitytemplate que você criou no primeiro procedimento.

5. Clique com botão direito no projeto de CustomActivityTemplateApp em **Gerenciador de soluções** e escolha **Build** para compilar o aplicativo.

6. Clique com botão direito no projeto de CustomActivityTemplateApp em **Gerenciador de soluções** e escolha **definir como projeto de inicialização**.

7. Selecione **Start Without Debugging** da **depurar** menu e pressione qualquer tecla para continuar quando solicitado da janela cmd.exe.

8. Abra o arquivo de Workflow1.xaml e abra o **caixa de ferramentas**.

9. Localize o **MyDelayActivity** modelo na **DelayActivityTemplate** categoria. Arraste-o para a superfície de design. Confirmar a **propriedades** janela que o `Duration` propriedade foi definida como 10 segundos.

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

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [Personalizando a experiência de design de fluxo de trabalho](customizing-the-workflow-design-experience.md)