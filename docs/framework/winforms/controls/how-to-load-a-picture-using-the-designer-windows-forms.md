---
title: 'Como: Carregar uma imagem usando o designer (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 1d95d5baafa42c7dea40933ba837b684d90b7b2b
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972368"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Como: Carregar uma imagem usando o designer (Windows Forms)

Com o controle <xref:System.Windows.Forms.PictureBox> de Windows Forms, você pode carregar e exibir uma imagem em um formulário em tempo de design, <xref:System.Windows.Forms.PictureBox.Image%2A> definindo a propriedade como uma imagem válida. A tabela a seguir mostra os tipos de arquivo disponíveis.

|Tipo|Extensão de nome de arquivo|
|----------|-------------------------|
|Bitmap|.bmp|
|Ícone|.ico|
|GIF|.gif|
|Metarquivo|.wmf|
|JPEG|.jpg|

> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="to-display-a-picture-at-design-time"></a>Para exibir uma imagem em tempo de design

1. Desenhe um <xref:System.Windows.Forms.PictureBox> controle em um formulário.

2. Na janela Propriedades, selecione a <xref:System.Windows.Forms.PictureBox.Image%2A> Propriedade e clique no botão de reticências para exibir a caixa de diálogo **abrir** .

3. Se você estiver procurando por um tipo de arquivo específico (por exemplo, arquivos .gif), selecione-o na caixa **Arquivos do tipo**.

4. Selecione o arquivo que você deseja exibir.

## <a name="to-clear-the-picture-at-design-time"></a>Para limpar a imagem em tempo de design

1. Na janela **Propriedades** , selecione a <xref:System.Windows.Forms.PictureBox.Image%2A> Propriedade e clique com o botão direito do mouse na imagem em miniatura pequena que aparece à esquerda do nome do objeto de imagem. Escolha **Redefinir**.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.PictureBox>
- [Visão geral do controle PictureBox](picturebox-control-overview-windows-forms.md)
- [Como: Modificar o tamanho ou o posicionamento de uma imagem em tempo de execução](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [Como: Definir imagens em tempo de execução](how-to-set-pictures-at-run-time-windows-forms.md)
- [Controle PictureBox](picturebox-control-windows-forms.md)
