---
title: Como carregar uma imagem usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 12b90d561a18fcffaafb9c45b7fa6be6dd060215
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736333"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Como carregar uma imagem usando o designer (Windows Forms)

Com o controle de <xref:System.Windows.Forms.PictureBox> de Windows Forms, você pode carregar e exibir uma imagem em um formulário em tempo de design, definindo a propriedade <xref:System.Windows.Forms.PictureBox.Image%2A> como uma imagem válida. A tabela a seguir mostra os tipos de arquivo disponíveis.

|Tipo|Extensão de nome de arquivo|
|---|---|
|Bitmap|.bmp|
|ícone|.ico|
|GIF|.gif|
|Metarquivo|.wmf|
|JPEG|.jpg|

## <a name="to-display-a-picture-at-design-time"></a>Para exibir uma imagem em tempo de design

1. Desenhe um controle de <xref:System.Windows.Forms.PictureBox> em um formulário.

2. Na janela **Propriedades** , selecione a propriedade <xref:System.Windows.Forms.PictureBox.Image%2A> e, em seguida, selecione o botão de reticências para exibir a caixa de diálogo **abrir** .

3. Se você estiver procurando um tipo de arquivo específico (por exemplo, arquivos. gif), selecione-o na caixa **arquivos do tipo** .

4. Selecione o arquivo que você deseja exibir.

## <a name="to-clear-the-picture-at-design-time"></a>Para limpar a imagem em tempo de design

1. Na janela **Propriedades** , selecione a propriedade <xref:System.Windows.Forms.PictureBox.Image%2A>. Clique com o botão direito do mouse na pequena imagem em miniatura que aparece à esquerda do nome do objeto de imagem e escolha **Redefinir**.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.PictureBox>
- [Visão geral do controle PictureBox](picturebox-control-overview-windows-forms.md)
- [Como modificar o tamanho ou o posicionamento de uma imagem em tempo de execução](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [Como definir imagens em tempo de execução](how-to-set-pictures-at-run-time-windows-forms.md)
- [Controle PictureBox](picturebox-control-windows-forms.md)
