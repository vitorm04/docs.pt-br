---
title: Visão geral de elementos gráficos
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: a95086645771de61cfc859e34b225992bc16eac9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641316"
---
# <a name="overview-of-graphics"></a>Visão geral de elementos gráficos
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] é uma interface de programação de aplicativo (API) que forma o subsistema do sistema operacional Microsoft Windows. O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] é responsável por exibir informações nas telas e impressoras. Como o nome sugere, o [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] é o sucessor do [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], a Graphics Device Interface incluída em versões anteriores do Windows.  
  
## <a name="managed-class-interface"></a>interface de classe gerenciada  
 A API [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] é exposta por meio de um conjunto de classes implantado como código gerenciado. Esse conjunto de classes é chamado de *interface de classe gerenciada* para [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Os namespaces a seguir compõem a interface da classe gerenciada:  
  
- <xref:System.Drawing>  
  
- <xref:System.Drawing.Drawing2D>  
  
- <xref:System.Drawing.Imaging>  
  
- <xref:System.Drawing.Text>  
  
- <xref:System.Drawing.Printing>  
  
 Com uma Graphics Device Interface, como [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], você pode exibir informações em uma tela ou impressora sem precisar se preocupar com os detalhes de um dispositivo de vídeo específico. O programador faz chamadas para métodos fornecidos pelas classes [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Esses métodos, por sua vez, fazem as chamadas apropriadas aos drivers de dispositivo específicos. O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] isola o aplicativo do hardware de elementos gráficos. É esse isolamento que permite que um programador crie aplicativos independentes de dispositivo.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de elementos gráficos](graphics-overview-windows-forms.md)
