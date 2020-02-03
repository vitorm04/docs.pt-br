---
title: Alterar bordas do formulário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: 2c8eb25b44c7406e4312f432f2d69524346f94d6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739569"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a>Como alterar as bordas de formulários do Windows Forms
Você tem vários estilos de borda para escolher quando estiver determinando a aparência e comportamento dos Windows Forms. Ao alterar a propriedade <xref:System.Windows.Forms.Form.FormBorderStyle%2A>, você pode controlar o comportamento de redimensionamento do formulário. Além disso, definir a <xref:System.Windows.Forms.Form.FormBorderStyle%2A> afeta como a barra de legenda é exibida, bem como quais botões podem aparecer nela. Para obter mais informações, consulte <xref:System.Windows.Forms.FormBorderStyle>.  
  
 Há um suporte abrangente para esta tarefa no Visual Studio.  
  
 Consulte também [Como alterar as bordas dos Windows Forms usando o designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a>Para definir o estilo de borda dos Windows Forms de maneira programática  
  
- Defina a propriedade <xref:System.Windows.Forms.Form.FormBorderStyle%2A> como o estilo desejado. O exemplo de código a seguir define o estilo de borda do formulário `DlgBx1` como <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     Consulte também [Como criar caixas de diálogo em tempo de design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).  
  
     Além disso, se você escolheu um estilo de borda para o formulário que fornece botões opcionais **Minimizar** e **Maximizar**, é possível especificar se deseja que um ou os dois botões sejam funcionais. Esses botões são úteis quando quiser controlar de perto a experiência do usuário. Os botões **Minimizar** e **Maximizar** são habilitados por padrão e sua funcionalidade é manipulada por meio da janela **Propriedades**.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.FormBorderStyle>
- <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>
- [Introdução ao Windows Forms](getting-started-with-windows-forms.md)
