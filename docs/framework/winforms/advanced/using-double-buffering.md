---
title: Usando buffers duplos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b5ad51e27c3d31ece1d11831c953023bedba3a97
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="using-double-buffering"></a>Usando buffers duplos
Você pode usar elementos gráficos em buffer duplo para reduzir a cintilação em seus aplicativos que contêm operações complexas de pintura. O .NET Framework contém suporte interno para o buffer duplo ou você pode gerenciar e processar imagens manualmente.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Elementos Gráficos em Buffer Duplo](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 Apresenta duplo buffer conceito e contornos do suporte do .NET Framework.  
  
 [Como Reduzir a Cintilação em Elementos Gráficos com Buffers Duplos em Formulários e Controles](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 Demonstra como usar o padrão duplas buffer suporte no .NET Framework.  
  
 [Como Gerenciar Elementos Gráficos em Buffer Manualmente](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 Mostra como gerenciar o buffer duplo em aplicativos.  
  
 [Como Renderizar Elementos Gráficos em Buffer Manualmente](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 Demonstra como renderizar elementos gráficos em buffer duplo.  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.Control.SetStyle%2A> ,  
 Método de controle que permite que o buffer duplo.  
  
 <xref:System.Drawing.BufferedGraphicsContext> ,  
 Fornece métodos para a criação de buffers de gráficos.  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 Fornece acesso ao contexto de elementos gráficos em buffer para um domínio de aplicativo.
