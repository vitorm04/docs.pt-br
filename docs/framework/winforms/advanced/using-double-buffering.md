---
title: Usando buffers duplos
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
ms.openlocfilehash: 5b22336221c7bdda3c9dd7adf23308a2b0bad450
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169914"
---
# <a name="using-double-buffering"></a>Usando buffers duplos
Você pode usar gráficos em buffer duplo para reduzir a cintilação em seus aplicativos que contêm operações de pintura complexas. O .NET Framework contém suporte interno para buffer duplo ou você pode gerenciar e renderizar elementos gráficos manualmente.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Elementos Gráficos em Buffer Duplo](double-buffered-graphics.md)  
 Apresenta duplas buffer conceito e contornos de suporte do .NET Framework.  
  
 [Como: Reduzir a cintilação em elementos gráficos com buffers duplos para formulários e controles](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 Demonstra como usar o padrão buffer suporte no .NET Framework duplo.  
  
 [Como: Gerenciar elementos gráficos em buffer manualmente](how-to-manually-manage-buffered-graphics.md)  
 Mostra como gerenciar o buffer duplo em aplicativos.  
  
 [Como: Renderizar elementos gráficos em buffer manualmente](how-to-manually-render-buffered-graphics.md)  
 Demonstra como renderizar elementos gráficos em buffer duplo.  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.Control.SetStyle%2A> Método de controle que permite que o buffer duplo.  
  
 <xref:System.Drawing.BufferedGraphicsContext> Fornece métodos para criação de buffers gráficos.  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 Fornece acesso ao contexto de elementos gráficos em buffer para um domínio de aplicativo.
