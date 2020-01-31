---
title: Multithreading em controles
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: 79832e12a10f02c909d2a28270594bcb4ea68656
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742135"
---
# <a name="multithreading-in-windows-forms-controls"></a>Multithread em controles dos Windows Forms
Em muitos aplicativos, você pode tornar sua interface do usuário mais ágil executando operações demoradas em outro thread. Várias ferramentas estão disponíveis para vários threads de Windows Forms controles, incluindo o namespace <xref:System.Threading>, o método <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> e o componente `BackgroundWorker`.  
  
> [!NOTE]
> O componente `BackgroundWorker` substitui e adiciona funcionalidade ao namespace <xref:System.Threading> e ao método <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>; no entanto, eles são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolher. Para saber mais, veja [Visão geral do componente BackgroundWorker](backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como fazer chamadas thread-safe para controles dos Windows Forms](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Mostra como fazer chamadas thread-safe para controles dos Windows Forms.  
  
 [Como usar um thread em segundo plano para pesquisar arquivos](how-to-use-a-background-thread-to-search-for-files.md)  
 Mostra como usar o namespace <xref:System.Threading> e o método <xref:System.Windows.Forms.Control.BeginInvoke%2A> para pesquisar arquivos de forma assíncrona.  
  
## <a name="reference"></a>Referência  
 <xref:System.ComponentModel.BackgroundWorker>  
 Documenta um componente que encapsula um thread de trabalho para operações assíncronas.  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 Documenta como carregar um som de forma assíncrona.  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 Documenta como carregar uma imagem de forma assíncrona.  
  
## <a name="related-sections"></a>Seções Relacionadas  
 [Como executar uma operação em segundo plano](how-to-run-an-operation-in-the-background.md)  
 Mostra como executar uma operação demorada com o componente <xref:System.ComponentModel.BackgroundWorker>.  
  
 [Visão geral do componente BackgroundWorker](backgroundworker-component-overview.md)  
 Fornece tópicos que descrevem como usar o componente de <xref:System.ComponentModel.BackgroundWorker> para operações assíncronas.
