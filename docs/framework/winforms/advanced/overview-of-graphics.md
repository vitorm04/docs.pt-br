---
title: Visão geral de elementos gráficos
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: f0e2fd9dcf31e5fdce16b5a3b6fd21eab6eab66a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505328"
---
# <a name="overview-of-graphics"></a>Visão geral de elementos gráficos
GDI+ é uma interface de programação de aplicativo (API) que forma o subsistema do sistema operacional Microsoft Windows. GDI+ é responsável por exibir informações nas telas e impressoras. Como o nome sugere, GDI+ é o sucessor do GDI, a Graphics Device Interface incluída em versões anteriores do Windows.  
  
## <a name="managed-class-interface"></a>interface de classe gerenciada  
 A API GDI+ é exposta por meio de um conjunto de classes implantado como código gerenciado. Esse conjunto de classes é chamado de *interface de classe gerenciada* ao GDI+. Os namespaces a seguir compõem a interface da classe gerenciada:  
  
- <xref:System.Drawing>  
  
- <xref:System.Drawing.Drawing2D>  
  
- <xref:System.Drawing.Imaging>  
  
- <xref:System.Drawing.Text>  
  
- <xref:System.Drawing.Printing>  
  
 Com uma Interface gráfica de dispositivo, como o GDI+, você pode exibir informações em uma tela ou impressora sem precisar se preocupar com os detalhes de um dispositivo de vídeo específico. O programador faz chamadas para métodos fornecidos pelas classes de GDI+. Esses métodos, por sua vez, fazem as chamadas apropriadas aos drivers de dispositivo específicos. GDI+ isola o aplicativo do hardware gráfico. É esse isolamento que permite que um programador crie aplicativos independentes de dispositivo.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de elementos gráficos](graphics-overview-windows-forms.md)
