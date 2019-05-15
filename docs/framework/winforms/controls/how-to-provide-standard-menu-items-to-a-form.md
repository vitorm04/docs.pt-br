---
title: 'Como: Fornecer itens de menu padrão para um formulário'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- menu items [Windows Forms], standard
- ToolStrip control [Windows Forms]
ms.assetid: 75db9126-e70c-4e81-921d-b83c0a4a9f50
ms.openlocfilehash: a95476ff3d182bf2a56e6527c9ee83c8c56af246
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583630"
---
# <a name="how-to-provide-standard-menu-items-to-a-form"></a>Como: Fornecer itens de menu padrão para um formulário
Você pode fornecer um menu padrão para os formulários com o <xref:System.Windows.Forms.MenuStrip> controle.  
  
 Há suporte abrangente para este recurso no Visual Studio.  
  
 Consulte também [passo a passo: Fornecendo itens de Menu padrão para um formulário](walkthrough-providing-standard-menu-items-to-a-form.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar um <xref:System.Windows.Forms.MenuStrip> controle para criar um formulário com um menu padrão. Seleções de item de menu são exibidas em um <xref:System.Windows.Forms.StatusStrip> controle.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [Controle MenuStrip](menustrip-control-windows-forms.md)
