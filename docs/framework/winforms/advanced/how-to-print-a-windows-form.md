---
title: 'Como: imprimir um Windows Form'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
ms.openlocfilehash: cd10e0a43ff37b921dc8e024d7a6a51fafbb0400
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591857"
---
# <a name="how-to-print-a-windows-form"></a>Como: imprimir um Windows Form
Como parte do processo de desenvolvimento, você geralmente desejará imprimir uma cópia do seu Windows Form. O exemplo de código a seguir mostra como imprimir uma cópia do formulário atual, usando o <xref:System.Drawing.Graphics.CopyFromScreen%2A> método.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
- Você não tem permissão para acessar a impressora.  
  
- Não há nenhuma impressora instalada.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Para executar este exemplo de código, você deve ter permissão para acessar a impressora que você usa com o seu computador.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Printing.PrintDocument>
- [Como: Renderizar imagens com o GDI+](how-to-render-images-with-gdi.md)
- [Como: Imprimir elementos gráficos nos Windows Forms](how-to-print-graphics-in-windows-forms.md)
