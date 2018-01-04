---
title: "Como redimensionar formulários do Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc2e9f81094d16030dbe4595a8132569edab782a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-windows-forms"></a>Como redimensionar formulários do Windows Forms
Você pode especificar o tamanho do seu Windows Forms de várias maneiras. Você pode alterar a altura e a largura do formulário programaticamente, definindo um novo valor para o <xref:System.Windows.Forms.Form.Size%2A> propriedade, ou ajustar o <xref:System.Windows.Forms.Control.Height%2A> ou <xref:System.Windows.Forms.Control.Width%2A> propriedades individualmente. Se você estiver usando [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], poderá alterar o tamanho usando o Designer de Formulários do Windows. Consulte também [Como redimensionar Windows Forms usando o Designer](http://msdn.microsoft.com/library/37k2zkwx\(v=vs.110\)).  
  
### <a name="to-resize-a-form-programmatically"></a>Redimensionar um formulário com programação  
  
-   Definir o tamanho de um formulário em tempo de execução, definindo o <xref:System.Windows.Forms.Form.Size%2A> propriedade do formulário.  
  
     O exemplo de código a seguir mostra o tamanho do formulário definido como 100 x 100 pixels.  
  
    ```vb  
    Form1.Size = New System.Drawing.Size(100, 100)  
    ```  
  
    ```csharp  
    Form1.Size = new System.Drawing.Size(100, 100);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(100, 100);  
    ```  
  
### <a name="to-change-form-width-and-height-programmatically"></a>Alterar a altura e a largura do formulário com programação  
  
-   Após o <xref:System.Windows.Forms.Form.Size%2A> é definida, alterar a altura ou a largura, usando o <xref:System.Windows.Forms.Control.Width%2A> ou <xref:System.Windows.Forms.Control.Height%2A> propriedades.  
  
     O exemplo de código a seguir mostra a largura do formulário definida para 300 pixels da borda esquerda do formulário, enquanto a altura permanece constante.  
  
    ```vb  
    Form1.Width = 300  
    ```  
  
    ```csharp  
    Form1.Width = 300;  
    ```  
  
    ```cpp  
    Form1->Width = 300;  
    ```  
  
     -ou-  
  
     Alterar <xref:System.Drawing.Size.Width%2A> ou <xref:System.Drawing.Size.Height%2A> definindo o <xref:System.Windows.Forms.Form.Size%2A> propriedade.  
  
     No entanto, como mostra o exemplo de código a seguir, essa abordagem é mais complicada do que apenas configuração <xref:System.Windows.Forms.Control.Width%2A> ou <xref:System.Windows.Forms.Control.Height%2A> propriedades.  
  
    ```vb  
    Form1.Size = New Size(300, Form1.Size.Height)  
    ```  
  
    ```csharp  
    Form1.Size = new Size(300, Form1.Size.Height);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(300, Form1->Size.Height);  
    ```  
  
### <a name="to-change-form-size-by-increments-programmatically"></a>Alterar o tamanho do formulário em incrementos com programação  
  
-   Para incrementar o tamanho do formulário, defina o <xref:System.Drawing.Size.Width%2A> e <xref:System.Drawing.Size.Height%2A> propriedades.  
  
     O exemplo de código a seguir mostra a largura do formulário definida para 200 pixels mais larga do que a configuração atual.  
  
    ```vb  
    Form1.Width += 200  
    ```  
  
    ```csharp  
    Form1.Width += 200;  
    ```  
  
    ```cpp  
    Form1->Width += 200;  
    ```  
  
    > [!CAUTION]
    >  Use sempre o <xref:System.Drawing.Size.Height%2A> ou <xref:System.Drawing.Size.Width%2A> propriedade para alterar uma dimensão de um formulário, a menos que você está definindo as dimensões de altura e largura ao mesmo tempo, definindo o <xref:System.Windows.Forms.Form.Size%2A> propriedade para um novo <xref:System.Drawing.Size> estrutura. O <xref:System.Windows.Forms.Form.Size%2A> propriedade retorna um <xref:System.Drawing.Size> estrutura, que é um tipo de valor. Não é possível atribuir um novo valor para a propriedade de um tipo de valor. Portanto, o código a seguir não será compilado.  
  
    ```vb  
    ' NOTE: CODE WILL NOT COMPILE  
    Dim f As New Form()  
    f.Size.Width += 100  
    ```  
  
    ```csharp  
    // NOTE: CODE WILL NOT COMPILE  
    Form f = new Form();  
    f.Size.Width += 100;  
    ```  
  
    ```cpp  
    // NOTE: CODE WILL NOT COMPILE  
    Form^ f = gcnew Form();  
    f->Size->X += 100;  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Guia de introdução ao Windows Forms](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [Aprimorando aplicativos do Windows Forms](../../../docs/framework/winforms/advanced/index.md)
