---
title: Visão geral do controle RichTextBox
ms.date: 03/30/2017
f1_keywords:
- RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
ms.openlocfilehash: 0d40967d97622b23e9dcb07e861f190327e6baba
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742400"
---
# <a name="richtextbox-control-overview-windows-forms"></a>Visão geral do controle RichTextBox (Windows Forms)
O controle <xref:System.Windows.Forms.RichTextBox> dos Windows Forms é usado para exibir, inserir e manipular texto com formatação. O controle de <xref:System.Windows.Forms.RichTextBox> faz tudo o que o controle de <xref:System.Windows.Forms.TextBox> faz, mas também pode exibir fontes, cores e links; carregar texto e imagens inseridas de um arquivo; e localizar os caracteres especificados. O controle <xref:System.Windows.Forms.RichTextBox> normalmente é usado para fornecer manipulação de texto e exibir recursos semelhantes aos aplicativos de processamento de texto como o Microsoft Word. Como o controle de <xref:System.Windows.Forms.TextBox>, o controle de <xref:System.Windows.Forms.RichTextBox> pode exibir barras de rolagem; Mas, ao contrário do controle de <xref:System.Windows.Forms.TextBox>, sua configuração padrão é exibir barras de rolagem horizontal e vertical conforme necessário e ter configurações de barra de rolagem adicionais.  
  
## <a name="working-with-the-richtextbox-control"></a>Trabalhando com o controle RichTextBox  
 Assim como com o controle de <xref:System.Windows.Forms.TextBox>, o texto exibido é definido pela propriedade <xref:System.Windows.Forms.RichTextBox.Text%2A>. O controle <xref:System.Windows.Forms.RichTextBox> tem várias propriedades para formatar texto. Para obter detalhes sobre essas propriedades, consulte [Como definir atributos de fonte para o controle RichTextBox do Windows Forms](how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md) e [Como definir recuos, recuos deslocados e parágrafos com marcadores com o controle RichTextBox do Windows Forms](set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md). Para manipular arquivos, os métodos <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> e <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> podem exibir e gravar vários formatos de arquivo, incluindo texto sem formatação, texto sem formatação Unicode e RTF (Rich Text Format). Os formatos de arquivo possíveis são listados em <xref:System.Windows.Forms.RichTextBoxStreamType>. Você pode usar o método de <xref:System.Windows.Forms.RichTextBox.Find%2A> para localizar cadeias de caracteres de texto ou específicos.  
  
 Você também pode usar um controle de <xref:System.Windows.Forms.RichTextBox> para links de estilo da Web definindo a propriedade <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> como `true` e escrevendo código para manipular o evento de <xref:System.Windows.Forms.RichTextBox.LinkClicked>. Para obter mais informações, consulte [Como exibir links em estilo da Web com o controle RichTextBox do Windows Forms](how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md). Você pode impedir que o usuário manipule parte ou todo o texto no controle definindo a propriedade <xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A> como `true`.  
  
 Você pode desfazer e refazer a maioria das operações de edição em um controle de <xref:System.Windows.Forms.RichTextBox> chamando os métodos <xref:System.Windows.Forms.TextBoxBase.Undo%2A> e <xref:System.Windows.Forms.RichTextBox.Redo%2A>. O método <xref:System.Windows.Forms.RichTextBox.CanRedo%2A> permite que você determine se a última operação que o usuário desfez pode ser reaplicada ao controle.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.RichTextBox>
- [Controle RichTextBox](richtextbox-control-windows-forms.md)
- [Visão geral do controle TextBox](textbox-control-overview-windows-forms.md)
