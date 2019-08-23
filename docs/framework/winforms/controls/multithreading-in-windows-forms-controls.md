---
title: Multithread em controles dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cf6790172b7445ad154eead5d17f8efddd78ffee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952677"
---
# <a name="multithreading-in-windows-forms-controls"></a>Multithread em controles dos Windows Forms
Em muitos aplicativos, você pode tornar sua interface do usuário mais ágil executando operações demoradas em outro thread. Várias ferramentas estão disponíveis para vários threads de Windows Forms controles, incluindo o <xref:System.Threading> namespace, o <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> método e o `BackgroundWorker` componente.  
  
> [!NOTE]
> O `BackgroundWorker` componente substitui e adiciona funcionalidade <xref:System.Threading> ao namespace e ao <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> método; no entanto, eles são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolher. Para obter mais informações, consulte [Visão Geral do Componente BackgroundWorker](backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Fazer chamadas de thread-safe para Windows Forms controles](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Mostra como fazer chamadas thread-safe para controles dos Windows Forms.  
  
 [Como: Usar um thread em segundo plano para pesquisar arquivos](how-to-use-a-background-thread-to-search-for-files.md)  
 Mostra como usar o <xref:System.Threading> namespace e o <xref:System.Windows.Forms.Control.BeginInvoke%2A> método para pesquisar arquivos de forma assíncrona.  
  
## <a name="reference"></a>Referência  
 <xref:System.ComponentModel.BackgroundWorker>  
 Documenta um componente que encapsula um thread de trabalho para operações assíncronas.  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 Documenta como carregar um som de forma assíncrona.  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 Documenta como carregar uma imagem de forma assíncrona.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Como: Executar uma operação em segundo plano](how-to-run-an-operation-in-the-background.md)  
 Mostra como executar uma operação demorada com o <xref:System.ComponentModel.BackgroundWorker> componente.  
  
 [Visão geral do componente BackgroundWorker](backgroundworker-component-overview.md)  
 Fornece tópicos que descrevem como usar o <xref:System.ComponentModel.BackgroundWorker> componente para operações assíncronas.
