---
title: Como listar os codificadores instalados
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
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image encoders [Windows Forms], listing
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 70f913acb2620b5c01e1aec1f1eb98b041b82a59
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-list-installed-encoders"></a>Como listar os codificadores instalados
Pode ser que você deseja listar os codificadores de imagem disponíveis em um computador, para determinar se o seu aplicativo pode salvar em um formato de arquivo de imagem específico. O <xref:System.Drawing.Imaging.ImageCodecInfo> classe fornece a <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> métodos estáticos para que você possa determinar qual imagem codificadores estão disponíveis. <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A>Retorna uma matriz de <xref:System.Drawing.Imaging.ImageCodecInfo> objetos.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir gera a lista de codificadores instalados e seus valores de propriedade.  
  
 [!code-csharp[UsingImageEncodersDecoders#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um aplicativo Windows Forms.  
  
-   Um <xref:System.Windows.Forms.PaintEventArgs>, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também  
 [Como Listar os Decodificadores Instalados](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 [Usando Codificadores e Decodificadores de Imagem no GDI+ Gerenciado](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
