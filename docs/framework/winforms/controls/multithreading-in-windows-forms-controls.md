---
title: Multithread em controles dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cc7f358a62c8057abb77e1f5a28544bb6c858d98
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703316"
---
# <a name="multithreading-in-windows-forms-controls"></a>Multithread em controles dos Windows Forms
Em muitos aplicativos, você pode tornar sua interface do usuário mais ágil executando operações demoradas em outro thread. Várias ferramentas estão disponíveis para multithreading seus controles de formulários do Windows, incluindo o <xref:System.Threading> namespace, o <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> método e o `BackgroundWorker` componente.  
  
> [!NOTE]
>  O `BackgroundWorker` componente substitui e adiciona funcionalidade para o <xref:System.Threading> namespace e o <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> método; no entanto, eles são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolher. Para obter mais informações, consulte [Visão Geral do Componente BackgroundWorker](backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Fazer chamadas Thread-Safe para controles dos Windows Forms](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Mostra como fazer chamadas thread-safe para controles dos Windows Forms.  
  
 [Como: Usar um Thread em segundo plano para procurar arquivos](how-to-use-a-background-thread-to-search-for-files.md)  
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
