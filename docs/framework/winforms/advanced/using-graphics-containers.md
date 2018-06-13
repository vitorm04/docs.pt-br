---
title: Usando contêineres de elementos gráficos
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
ms.openlocfilehash: 8755a95434d3fed06a55cfca0f71d86e5521cb39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525015"
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
