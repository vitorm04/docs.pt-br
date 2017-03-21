---
title: "Ajuda para manipuladores de eventos no código do Visual Basic | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- CheckedListBox1_SelectedIndexChanged
- Calendar1_SelectionChanged
- Form1_Load
- DropDownList1_SelectedIndexChanged
- TextBox1_TextChanged
- ListBox1_SelectedIndexChanged
- TreeView1_AfterSelect
- MaskedTextBox1_MaskInputRejected
- Menu1_MenuItemClick
- TabPage1_Click
- LinkButton1_Click
- CheckBoxList1_SelectedIndexChanged
- ProgressBar1_Click
- ToolStripButton1_Click
- ImageButton1_Click
- RadioButtonList1_SelectedIndexChanged
- PictureBox1_Click
- Label1_Click
- ToolStrip1_ItemClicked
- RichTextBox1_TextChanged
- ListView1_SelectedIndexChanged
- PrintPreviewControl1_Click
- ComboBox1_SelectedIndexChanged
- Button1_Click
- Page_Load
- TrackBar1_Scroll
- WebBrowser1_DocumentCompleted
- TreeView1_SelectedNodeChanged
- CheckBox1_CheckedChanged
- RadioButton1_CheckedChanged
- NotifyIcon1_MouseDown
dev_langs:
- VB
helpviewer_keywords:
- event handlers, getting F1 Help in Visual Basic code
ms.assetid: 2c92decf-844e-4ba4-82c7-f2fc0adc3002
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4a57f5368ba9783f8751b5327fa6e68b94e05111
ms.lasthandoff: 03/13/2017

---
# <a name="help-for-event-handlers-in-visual-basic-code"></a>Ajuda para manipuladores de eventos no código do Visual Basic
Para obter ajuda sobre um determinado manipulador de eventos enquanto estiver no editor de códigos, coloque o cursor o `Handles` cláusula no back-end do procedimento de evento, em seguida, pressione F1. Por exemplo, o `Form1_Load` instrução a seguir, o local correto para colocar o cursor está em `MyBase.Load`:  
  
```  
Private Sub Form1_Load(ByVal sender As System.Object,   
    ByVal e As System.EventArgs) Handles MyBase.Load  
  
End Sub  
```  
  
## <a name="see-also"></a>Consulte também  
 [Eventos](http://msdn.microsoft.com/library/b6f65241-e0ad-4590-a99f-200ce741bb1f)   
 [Visão geral de manipuladores de eventos](http://msdn.microsoft.com/library/228112e1-1711-42ee-8ffa-ff3555bffe66)
