---
title: Como carregar uma imagem usando o designer (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1dec3c71c0c93ce580925744fe55f05cd2e5f383
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Como carregar uma imagem usando o designer (Windows Forms)
Com o Windows Forms <xref:System.Windows.Forms.PictureBox> controle, você pode carregar e exibir uma imagem em um formulário em tempo de design, definindo a <xref:System.Windows.Forms.PictureBox.Image%2A> propriedade para uma imagem válida. A tabela a seguir mostra os tipos de arquivo disponíveis.  
  
|Tipo|Extensão de nome de arquivo|  
|----------|-------------------------|  
|Bitmap|.bmp|  
|Ícone|.ico|  
|GIF|.gif|  
|Metarquivo|.wmf|  
|JPEG|.jpg|  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-a-picture-at-design-time"></a>Para exibir uma imagem em tempo de design  
  
1.  Desenhar um <xref:System.Windows.Forms.PictureBox> controle em um formulário.  
  
2.  Na janela Propriedades, selecione o <xref:System.Windows.Forms.PictureBox.Image%2A> propriedade e, em seguida, clique no botão de reticências para exibir o **abrir** caixa de diálogo.  
  
3.  Se você estiver procurando por um tipo de arquivo específico (por exemplo, arquivos .gif), selecione-o na caixa **Arquivos do tipo**.  
  
4.  Selecione o arquivo que você deseja exibir.  
  
### <a name="to-clear-the-picture-at-design-time"></a>Para limpar a imagem em tempo de design  
  
1.  Sobre o **propriedades** janela, selecione o <xref:System.Windows.Forms.PictureBox.Image%2A> propriedade e o botão direito do mouse na imagem em miniatura pequena que aparece à esquerda do nome do objeto image. Escolha **Redefinir**.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.PictureBox>  
 [Visão geral do controle PictureBox](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [Como modificar o tamanho ou o posicionamento de uma imagem em tempo de execução](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)  
 [Como definir imagens em tempo de execução](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [Controle PictureBox](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
