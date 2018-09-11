---
title: 'Instruções passo a passo: copiando e colando um controle ElementHost nos Windows Forms separados'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
ms.openlocfilehash: 55b426fbe95bac269183a649ecd839175a8cbdda
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44337675"
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a>Instruções passo a passo: copiando e colando um controle ElementHost nos Windows Forms separados
Este passo a passo mostra como copiar um controle WPF (Windows Presentation Foundation) de um formulário do Windows para outro.  
  
 Nesta instrução passo a passo, as seguintes tarefas serão executadas:  
  
-   Crie o projeto.  
  
-   Copie um controle WPF.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar o projeto dos Windows Forms.  
  
> [!NOTE]
>  Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
-   Crie um novo projeto de Aplicativo dos Windows Forms no Visual Basic ou Visual C# chamado `CopyElementHost`.  
  
## <a name="copying-a-wpf-control"></a>Copiando um controle WPF  
 Depois de adicionar um controle WPF ao projeto, você pode copiar para outros formulários no projeto.  
  
#### <a name="to-copy-a-wpf-control"></a>Para copiar um controle WPF  
  
1.  Adicione um novo WPF <xref:System.Windows.Controls.UserControl> projeto à solução. Use o nome padrão do tipo de controle, `UserControl1.xaml`. Para obter mais informações, consulte [Instruções passo a passo: como criar novo conteúdo WPF nos Windows Forms em tempo de design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  Compile o projeto.  
  
3.  Abra `Form1` no Designer de Formulários do Windows.  
  
4.  Da **Caixa de Ferramentas**, arraste uma instância de `UserControl1` para o formulário.  
  
     Uma instância do `UserControl1` é hospedado em uma nova <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost1`.  
  
5.  Com `elementHost1` selecionado, pressione CTRL+C para copiá-lo para a área de transferência.  
  
6.  Adicione um novo formulário do Windows ao projeto. Use o nome padrão do tipo de formulário, `Form2`.  
  
7.  Com `Form2` aberto no Designer de Formulários do Windows, pressione CTRL+V para colar uma cópia do `elementHost1` no formulário.  
  
     O controle copiado também é chamado `elementHost1`, porque ele é um campo particular da classe `Form2`. Não há nenhuma colisão de nome com o `elementHost1` na classe `Form1`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Migração e interoperabilidade](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Usando Controles do WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Criar o XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
