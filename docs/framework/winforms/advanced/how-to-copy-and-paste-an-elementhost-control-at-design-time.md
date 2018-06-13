---
title: Como copiar e colar um controle ElementHost em tempo de design
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
ms.openlocfilehash: 1a9938500287b3b44f13f0aa664da85b7fdb4675
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524845"
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a>Como copiar e colar um controle ElementHost em tempo de design
Este procedimento mostra como copiar um controle Windows Presentation Foundation (WPF) em um Windows Form.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-copy-and-paste-an-elementhost-control-at-design-time"></a>Para copiar e colar um controle ElementHost em tempo de design  
  
1.  Adicione um novo WPF <xref:System.Windows.Controls.UserControl> ao seu projeto de formulários do Windows. Use o nome padrão do tipo de controle, `UserControl1.xaml`. Para obter mais informações, consulte [Instruções passo a passo: como criar novo conteúdo WPF nos Windows Forms em tempo de design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  No **propriedades** janela, defina o valor da <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades de `UserControl1` para `200`.  
  
3.  Definir o valor de <xref:System.Windows.Controls.Control.Background%2A> propriedade `Blue`.  
  
4.  Compile o projeto.  
  
5.  Abra `Form1` no Designer de Formulários do Windows.  
  
6.  Da **Caixa de Ferramentas**, arraste uma instância de `UserControl1` para o formulário.  
  
     Uma instância de `UserControl1` está hospedada em um novo <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost1`.  
  
7.  Com `elementHost1` selecionado, pressione CTRL+C para copiá-lo para a área de transferência.  
  
8.  Pressione CTRL + V para colar o controle copiado para o formulário.  
  
     Um novo <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost2` é criado no formulário.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Instruções passo a passo: copiando e colando um controle ElementHost em Windows Forms separados](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 [Migração e interoperabilidade](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Usando Controles do WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Designer do WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
