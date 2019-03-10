---
title: Visão geral do controle RichTextBox (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
ms.openlocfilehash: ded2c9bb0e5b3320de700ce6126710314ed9e4f2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720232"
---
# <a name="richtextbox-control-overview-windows-forms"></a>Visão geral do controle RichTextBox (Windows Forms)
O controle <xref:System.Windows.Forms.RichTextBox> dos Windows Forms é usado para exibir, inserir e manipular texto com formatação. O <xref:System.Windows.Forms.RichTextBox> controle faz tudo o que o <xref:System.Windows.Forms.TextBox> controle faz, mas ele também pode exibir fontes, cores e links; carregar texto e imagens inseridas de um arquivo; e localizar caracteres especificados. O controle <xref:System.Windows.Forms.RichTextBox> normalmente é usado para fornecer manipulação de texto e exibir recursos semelhantes aos aplicativos de processamento de texto como o Microsoft Word. Como o <xref:System.Windows.Forms.TextBox> controle, o <xref:System.Windows.Forms.RichTextBox> controle pode exibir barras de rolagem, mas ao contrário de <xref:System.Windows.Forms.TextBox> controle, sua configuração padrão é exibir barras de rolagem horizontais e verticais conforme necessário, e tem configurações de barra de rolagem adicionais.  
  
## <a name="working-with-the-richtextbox-control"></a>Trabalhando com o controle RichTextBox  
 Assim como acontece com o <xref:System.Windows.Forms.TextBox> controle, o texto exibido é definido pelo <xref:System.Windows.Forms.RichTextBox.Text%2A> propriedade. O <xref:System.Windows.Forms.RichTextBox> controle possui várias propriedades para formatar o texto. Para obter detalhes sobre essas propriedades, consulte [como: Definir atributos de fonte para o Windows Forms controle RichTextBox](how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md) e [como: Definir recuos, recuos deslocados e parágrafos com marcadores com o controle RichTextBox dos Windows Forms](set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md). Para manipular arquivos, o <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> e <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> métodos podem exibir e gravar vários formatos de arquivo, incluindo texto sem formatação, texto sem formatação Unicode e Rich Text Format (RTF). Os formatos de arquivo possíveis são listados em <xref:System.Windows.Forms.RichTextBoxStreamType>. Você pode usar o <xref:System.Windows.Forms.RichTextBox.Find%2A> método para localizar as cadeias de caracteres de texto ou caracteres específicos.  
  
 Você também pode usar um <xref:System.Windows.Forms.RichTextBox> controle de links no estilo Web definindo o <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> propriedade a ser `true` e escrever código para manipular o <xref:System.Windows.Forms.RichTextBox.LinkClicked> eventos. Para obter mais informações, confira [Como: Exibir Links em estilo da Web com o Windows Forms controle RichTextBox](how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md). Você pode impedir que o usuário manipular parte ou todo o texto no controle definindo a <xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A> propriedade para `true`.  
  
 Você pode desfazer e refazer a maioria das operações de edição em um <xref:System.Windows.Forms.RichTextBox> controle chamando o <xref:System.Windows.Forms.TextBoxBase.Undo%2A> e <xref:System.Windows.Forms.RichTextBox.Redo%2A> métodos. O <xref:System.Windows.Forms.RichTextBox.CanRedo%2A> método permite que você determine se a última operação que o usuário desfez pode ser reaplicada ao controle.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.RichTextBox>
- [Controle RichTextBox](richtextbox-control-windows-forms.md)
- [Visão geral do controle TextBox](textbox-control-overview-windows-forms.md)
