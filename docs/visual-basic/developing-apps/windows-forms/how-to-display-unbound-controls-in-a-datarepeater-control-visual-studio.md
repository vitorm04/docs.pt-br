---
title: "Como: exibir controles não associados em um controle DataRepeater (Visual Studio) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
caps.latest.revision: 8
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
ms.openlocfilehash: 5ced99b26a9a9531332939f2ca77b2725a847977
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a>Como exibir controles não associados em um controle DataRepeater (Visual Studio)
Além de controles associados, você talvez queira adicionar outros controles para um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, como um rótulo estático ou uma imagem que é repetida em cada item a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
> [!NOTE]
>  Você também deve ter pelo menos um controle ligado no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>ou nada será exibido em tempo de execução.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a>Para adicionar controles não associados a um DataRepeater  
  
1.  Arraste um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>de controle do **Visual Basic PowerPacks** guia o **Toolbox** a um controle de formulário ou contêiner.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
2.  Arraste as alças de dimensionamento e a posição para tamanho e posição do controle.  
  
     Você também pode redimensionar e posicionar o controle alterando o **tamanho** e **posição** propriedades na janela Propriedades.  
  
3.  Adicione pelo menos um controle ligado a dados para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Para obter mais informações, consulte [como: exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
4.  Arraste um controle do **Toolbox** para a região de modelo de item do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
     Observe que o controle tem duas regiões retangulares. A região interna é o *modelo de item*; controles adicionados ao modelo serão repetidos em cada item a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle em tempo de execução.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> A região externa é o *visor*, onde os itens serão exibidos; controles que são adicionados a essa região não serão exibidos em tempo de execução.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [Como: exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [Como: criar um formulário mestre/detalhes usando dois controles DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
