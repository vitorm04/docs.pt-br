---
title: Como definir a imagem exibida por um controle dos Windows Forms
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
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6d9f4d806b39e6e1272ddbb60befdaf8c76e46b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>Como definir a imagem exibida por um controle dos Windows Forms
Vários controles de formulários do Windows podem exibir imagens. Essas imagens podem ser ícones esclarecer a finalidade do controle, como um ícone de disquete em um botão denotando o **salvar** comando. Como alternativa, os ícones podem ser imagens de plano de fundo para dar o controle a aparência e o comportamento desejado.  
  
### <a name="to-set-the-image-displayed-by-a-control"></a>Para definir a imagem exibida por um controle  
  
1.  Definir o controle `Image` ou `BackgroundImage` propriedade para um objeto do tipo <xref:System.Drawing.Image>. Em geral, você será possível carregar a imagem de um arquivo usando o <xref:System.Drawing.Image.FromFile%2A> método.  
  
     No exemplo de código a seguir, o caminho definido para o local da imagem é o **Minhas imagens** pasta. A maioria dos computadores que executam o sistema operacional Windows incluirá esse diretório. Isso também permite que os usuários com níveis de acesso mínimos do sistema executar o aplicativo com segurança. O exemplo de código a seguir exige que você já tenha um formulário com um <xref:System.Windows.Forms.PictureBox> controle adicionado.  
  
    ```vb  
    ' Replace the image named below  
    ' with an icon of your own choosing.  
    PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.MyPictures) _  
       & "\Image.gif")  
    ```  
  
    ```csharp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.MyPictures)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    pictureBox1->Image = Image::FromFile(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::MyPictures),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Image.FromFile%2A>  
 <xref:System.Drawing.Image>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>
