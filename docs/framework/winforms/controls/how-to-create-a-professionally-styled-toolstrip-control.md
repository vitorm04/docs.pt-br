---
title: 'Como: Criar um controle ToolStrip com estilo profissional'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
ms.openlocfilehash: 4e4e899d583eb87b3ced7161f1fd274c0bcc591c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586560"
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a>Como: Criar um controle ToolStrip com estilo profissional
Você pode dar a seu aplicativo <xref:System.Windows.Forms.ToolStrip> controla uma aparência profissional e o comportamento (aparência) ao escrever sua própria classe que deriva de <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tipo.  
  
 Há suporte abrangente para este recurso no Visual Studio.  
  
 Confira [Passo a passo: Criando um controle ToolStrip com estilo profissional](walkthrough-creating-a-professionally-styled-toolstrip-control.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar <xref:System.Windows.Forms.ToolStrip> controles para criar um controle composto que imita a **painel de navegação** fornecidas pelo Microsoft® Outlook®.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos assemblies System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [Controle ToolStrip](toolstrip-control-windows-forms.md)
- [Como: Fornecer itens de Menu padrão para um formulário](how-to-provide-standard-menu-items-to-a-form.md)
