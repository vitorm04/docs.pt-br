---
title: Multithread em controles dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2b9c0a7b19df62867a4148b60e24b7d3ba9bcce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="multithreading-in-windows-forms-controls"></a>Multithread em controles dos Windows Forms
Em muitos aplicativos, você pode tornar sua interface do usuário mais ágil executando operações demoradas em outro thread. Várias ferramentas estão disponíveis para multithreading os controles de formulários do Windows, incluindo o <xref:System.Threading> namespace, o <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> método e o `BackgroundWorker` componente.  
  
> [!NOTE]
>  O `BackgroundWorker` componente substitui e adiciona a funcionalidade para o <xref:System.Threading> namespace e o <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> método; no entanto, eles são mantidos para compatibilidade com versões anteriores e o uso futuro, se você escolher. Para obter mais informações, consulte [Visão Geral do Componente BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como fazer chamadas thread-safe para controles dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Mostra como fazer chamadas thread-safe para controles dos Windows Forms.  
  
 [Como usar um thread em segundo plano para pesquisar arquivos](../../../../docs/framework/winforms/controls/how-to-use-a-background-thread-to-search-for-files.md)  
 Mostra como usar o <xref:System.Threading> namespace e o <xref:System.Windows.Forms.Control.BeginInvoke%2A> método para pesquisar arquivos de forma assíncrona.  
  
## <a name="reference"></a>Referência  
 <xref:System.ComponentModel.BackgroundWorker>  
 Documenta um componente que encapsula um thread de trabalho para operações assíncronas.  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 Documenta como carregar um som de forma assíncrona.  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 Documenta como carregar uma imagem de forma assíncrona.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Como executar uma operação em segundo plano](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 Mostra como executar uma operação demorada com o <xref:System.ComponentModel.BackgroundWorker> componente.  
  
 [Visão geral do componente BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 Fornece tópicos que descrevem como usar o <xref:System.ComponentModel.BackgroundWorker> componente para operações assíncronas.
