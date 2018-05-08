---
title: Como extrair o ícone associado a um arquivo no Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: 21bce2f630649afb59272362a7f40055855ed512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>Como extrair o ícone associado a um arquivo no Windows Forms
Muitos arquivos têm ícones inseridos que fornecem uma representação visual do tipo de arquivo associado. Por exemplo, documentos do Microsoft Word contêm um ícone que os identifica como documentos do Word. Ao exibir os arquivos em um controle de lista ou um controle de tabela, talvez você queira exibir o ícone que representa o tipo de arquivo ao lado de cada nome de arquivo. Você pode fazer isso facilmente usando o <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> método.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como extrair o ícone associado a um arquivo e exibir o nome do arquivo e o ícone associado um <xref:System.Windows.Forms.ListView> controle.  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Para compilar o exemplo:  
  
-   Cole o código anterior em um formulário do Windows e chame o `ExtractAssociatedIconExample` método de construtor do formulário ou <xref:System.Windows.Forms.Form.Load> método manipulador de eventos.  
  
     Você precisará certificar-se de que o formulário importa o <xref:System.IO> namespace.  
  
## <a name="see-also"></a>Consulte também  
 [Imagens, bitmaps e metarquivos](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Controle ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
