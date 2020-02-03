---
title: Como extrair o ícone associado a um arquivo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: 28769144b0e1c631a31c3c541747a6215f861d0e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742549"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>Como extrair o ícone associado a um arquivo no Windows Forms
Muitos arquivos têm ícones inseridos que fornecem uma representação visual do tipo de arquivo associado. Por exemplo, documentos do Microsoft Word contêm um ícone que os identifica como documentos do Word. Ao exibir os arquivos em um controle de lista ou um controle de tabela, talvez você queira exibir o ícone que representa o tipo de arquivo ao lado de cada nome de arquivo. Você pode fazer isso facilmente usando o método <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A>.  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 O exemplo de código a seguir demonstra como extrair o ícone associado a um arquivo e exibir o nome do arquivo e seu ícone associado em um controle de <xref:System.Windows.Forms.ListView>.  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Para compilar o exemplo:  
  
- Cole o código anterior em um Windows Form e chame o método `ExtractAssociatedIconExample` no construtor do formulário ou <xref:System.Windows.Forms.Form.Load> método de manipulação de eventos.  
  
     Você precisará certificar-se de que seu formulário importa o namespace <xref:System.IO>.  
  
## <a name="see-also"></a>Consulte também

- [Imagens, bitmaps e metarquivos](images-bitmaps-and-metafiles.md)
- [Controle ListView](../controls/listview-control-windows-forms.md)
