---
title: Inicialização de elementos de objeto que não estejam em uma árvore de objetos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- logical tree [WPF]
- visual tree [WPF]
- elements [WPF], initializing
- initializing elements [WPF]
ms.assetid: 7b8dfc9b-46ac-4ce8-b7bb-035734d688b7
ms.openlocfilehash: 6f3c8611b83977431038573eb1c5c880acbefdc4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108960"
---
# <a name="initialization-for-object-elements-not-in-an-object-tree"></a>Inicialização de elementos de objeto que não estejam em uma árvore de objetos
Alguns aspectos da inicialização de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] são deixados para processos que normalmente dependem de aquele elemento estar conectado à árvore lógica ou à árvore visual. Este tópico descreve as etapas que podem ser necessárias para inicializar um elemento que não está conectado a nenhuma árvore.  

## <a name="elements-and-the-logical-tree"></a>Elementos e a árvore lógica  
 Quando você cria uma instância de uma classe [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] no código, deve estar ciente de que diversos aspectos da inicialização do objeto para uma classe [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] deliberadamente não fazem parte do código executado ao chamar o construtor da classe. Especialmente para uma classe de controle, a maior parte da representação visual do controle não é definida pelo construtor. Em vez disso, a representação visual é definida pelo modelo do controle. O modelo pode vir de uma variedade de fontes, mas geralmente é obtido de estilos de tema. Os modelos são efetivamente de associação tardia; o modelo necessário não é anexado ao controle em questão até que o controle esteja pronto para o layout. E o controle não está pronto para o layout até seja anexado a uma árvore lógica que se conecte a uma superfície de renderização na raiz. É esse elemento de nível raiz que inicia a renderização de todos os seus elementos filho, conforme definido na árvore lógica.  
  
 A árvore visual também participa deste processo. Elementos que fazem parte da árvore visual por meio de modelos também não são totalmente instanciados até que sejam conectados.  
  
 As consequências deste comportamento são que certas operações que dependem das características visuais concluídas de um elemento exigem etapas adicionais. Um exemplo é se você está tentando obter as características visuais de uma classe construída, mas ainda não anexada a uma árvore. Por exemplo, se você deseja chamar <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> em um <xref:System.Windows.Media.Imaging.RenderTargetBitmap> e o visual que você está passando é um elemento não conectado a uma árvore, esse elemento não estará visualmente completo até que passos de inicialização adicionais sejam concluídos.  
  
### <a name="using-begininit-and-endinit-to-initialize-the-element"></a>Utilizando BeginInit e EndInit para inicializar o elemento  
 Diversas classes no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementar o <xref:System.ComponentModel.ISupportInitialize> interface. Você usa o <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> e <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> métodos da interface para denotar uma região no seu código que contém as etapas de inicialização (como configurar valores de propriedade que afetam a renderização). Depois de <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> é chamado na sequência, o sistema de layout pode processar o elemento e começar a procurar um estilo implícito.  
  
 Se o elemento estiver configurando propriedades de um <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> derivado de classe, você poderá chamar as versões de classes <xref:System.Windows.FrameworkElement.BeginInit%2A> e <xref:System.Windows.FrameworkElement.EndInit%2A> em vez de realizar a conversão em <xref:System.ComponentModel.ISupportInitialize>.  
  
### <a name="sample-code"></a>Código de exemplo  
 O exemplo a seguir é o código de exemplo para um aplicativo de console que usa renderização [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] e <xref:System.Windows.Markup.XamlReader.Load%28System.IO.Stream%29?displayProperty=nameWithType> de um flexível [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo para ilustrar o posicionamento adequado dos <xref:System.Windows.FrameworkElement.BeginInit%2A> e <xref:System.Windows.FrameworkElement.EndInit%2A> em torno de outras [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] chamadas que ajustar as propriedades que afetam a renderização.  
  
 O exemplo ilustra apenas a função principal. As funções `Rasterize` e `Save` (não mostradas) são funções utilitárias que cuidam do processamento de imagens e E/S.  
  
 [!code-csharp[InitializeElements#Main](~/samples/snippets/csharp/VS_Snippets_Wpf/InitializeElements/CSharp/initializeelements.cs#main)]
 [!code-vb[InitializeElements#Main](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InitializeElements/VisualBasic/initializeelements.vb#main)]  
  
## <a name="see-also"></a>Consulte também

- [Árvores no WPF](trees-in-wpf.md)
- [Visão geral de renderização de gráficos do WPF](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [Visão geral de XAML (WPF)](xaml-overview-wpf.md)
