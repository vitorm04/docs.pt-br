---
title: Como alterar as bordas de formulários do Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: e04234b4f2f18738567c3f9846d8ae0c94780fcb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43535875"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a>Como alterar as bordas de formulários do Windows Forms
Você tem vários estilos de borda para escolher quando estiver determinando a aparência e comportamento dos Windows Forms. Alterando o <xref:System.Windows.Forms.Form.FormBorderStyle%2A> propriedade, você pode controlar o comportamento de redimensionamento do formulário. Além disso, definindo o <xref:System.Windows.Forms.Form.FormBorderStyle%2A> afeta como a barra de legenda é exibida, bem como quais botões podem aparecer nela. Para obter mais informações, consulte <xref:System.Windows.Forms.FormBorderStyle>.  
  
 Há um suporte abrangente para esta tarefa no Visual Studio.  
  
 Consulte também [Como alterar as bordas dos Windows Forms usando o designer](https://msdn.microsoft.com/library/yettzh3e\(v=vs.110\)).  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a>Para definir o estilo de borda dos Windows Forms de maneira programática  
  
-   Defina o <xref:System.Windows.Forms.Form.FormBorderStyle%2A> propriedade para o estilo desejado. O exemplo de código a seguir define o estilo de borda do formulário `DlgBx1` para <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.  
  
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
  
     Consulte também [Como criar caixas de diálogo em tempo de design](https://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\)).  
  
     Além disso, se você escolheu um estilo de borda para o formulário que fornece botões opcionais **Minimizar** e **Maximizar**, é possível especificar se deseja que um ou os dois botões sejam funcionais. Esses botões são úteis quando quiser controlar de perto a experiência do usuário. Os botões **Minimizar** e **Maximizar** são habilitados por padrão e sua funcionalidade é manipulada por meio da janela **Propriedades**.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.FormBorderStyle>  
 <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>  
 [Guia de introdução ao Windows Forms](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
