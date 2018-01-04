---
title: "Usando contêineres de elementos gráficos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 244f8e8a280369798daf12f8a61519826f937a4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-graphics-containers"></a>Usando contêineres de elementos gráficos
Um <xref:System.Drawing.Graphics> objeto fornece métodos como <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, e <xref:System.Drawing.Graphics.DrawString%2A> para exibir imagens de vetor, imagens de varredura e texto. Um <xref:System.Drawing.Graphics> objeto também tem várias propriedades que influenciam a qualidade e a orientação dos itens que são desenhadas. Por exemplo, a propriedade de modo de suavização determina se a suavização é aplicada às linhas e curvas e a propriedade de transformação global influencia a posição e a rotação dos itens que são desenhados.  
  
 Um <xref:System.Drawing.Graphics> objeto está associado um dispositivo de vídeo específico. Quando você usa um <xref:System.Drawing.Graphics> objeto ao desenhar em uma janela, o <xref:System.Drawing.Graphics> objeto também é associado essa janela específica.  
  
 Um <xref:System.Drawing.Graphics> objeto pode ser pensado como um contêiner porque ele contém um conjunto de propriedades que influenciam o desenho e está vinculada a informações específicas de dispositivo. Você pode criar um contêiner secundário dentro de uma existente <xref:System.Drawing.Graphics> objeto chamando o <xref:System.Drawing.Graphics.BeginContainer%2A> método que <xref:System.Drawing.Graphics> objeto.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Gerenciando o Estado de um Objeto Gráfico](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)  
 Descreve como gerenciar configurações de qualidade, a área de recorte e transformações de um <xref:System.Drawing.Graphics> objeto.  
  
 [Usando Contêineres de Elementos Gráficos Aninhados](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)  
 Mostra como usar contêineres para controlar o estado do <xref:System.Drawing.Graphics> objeto.
