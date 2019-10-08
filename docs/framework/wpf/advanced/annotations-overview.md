---
title: Visão geral de anotações
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- highlights [WPF]
- documents [WPF], annotations
- sticky notes [WPF]
ms.assetid: 716bf474-29bd-4c74-84a4-8e0744bdad62
ms.openlocfilehash: dc9c4125f9ac3c44be41efe92b9e495599e5c130
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004038"
---
# <a name="annotations-overview"></a>Visão geral de anotações
Escrever anotações ou comentários em documentos em papel é uma atividade tão comum que quase não valorizamos. Essas anotações ou comentários são "anotações" que adicionamos a um documento para sinalizar informações ou realçar itens de interesse para referência posterior. Embora gravar anotações em documentos impressos seja fácil e um lugar comum, a capacidade de adicionar comentários pessoais aos documentos eletrônicos normalmente é muito limitada, quando sequer está disponível.  
  
 Este tópico examina vários tipos comuns de anotações, anotações e destaques mais específicos e ilustra como a estrutura de anotações da Microsoft facilita esses tipos de anotações em aplicativos por meio do Windows Presentation Foundation (WPF ) controles de exibição de documento.  os controles de exibição de documento [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] que dão suporte a anotações incluem <xref:System.Windows.Controls.FlowDocumentReader> e <xref:System.Windows.Controls.FlowDocumentScrollViewer>, bem como controles derivados de <xref:System.Windows.Controls.Primitives.DocumentViewerBase>, como <xref:System.Windows.Controls.DocumentViewer> e <xref:System.Windows.Controls.FlowDocumentPageViewer>.  

<a name="caf1_type_stickynotes"></a>   
## <a name="sticky-notes"></a>Notas autoadesivas  
 Uma nota autoadesiva típica contém informações gravadas em um pequeno pedaço de papel colorido que é então "colado" a um documento. As notas adesivas digitais fornecem uma funcionalidade semelhante para documentos eletrônicos, mas com a flexibilidade adicional para incluir muitos outros tipos de conteúdo, como texto digitado, notas manuscritas (por exemplo, traços de "tinta" de Tablet PC) ou links da Web.  
  
 A ilustração a seguir mostra alguns exemplos de realce, nota autoadesiva de texto e anotações em nota autoadesivas de tinta.  
  
 ![Anotações em notas autoadesivas de tinta, texto e realce.](./media/caf-stickynote.jpg "CAF_StickyNote")  
  
 O exemplo a seguir mostra o método que você pode usar para habilitar o suporte a anotação em seu aplicativo.  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## <a name="highlights"></a>Destaques  
 As pessoas usam métodos criativos para chamar a atenção para itens de interesse quando marcam um documento em papel, como sublinhar, realçar, circular palavras em uma frase ou desenhar de marcas ou anotações nas margens.  As anotações de realce no Microsoft Annotations Framework fornecem um recurso semelhante para a marcação de informações exibidas em controles de exibição de documento [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 A ilustração a seguir mostra um exemplo de uma anotação de realce.  
  
 ![Realçar anotação](./media/caf-callouts.png "CAF_Callouts")  
  
 Os usuários normalmente criam anotações selecionando primeiro um texto ou um item de interesse e, em seguida, clicando com o botão direito do mouse para exibir uma <xref:System.Windows.Controls.ContextMenu> de opções de anotação.  O exemplo a seguir mostra o [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] que você pode usar para declarar um <xref:System.Windows.Controls.ContextMenu> com comandos roteados que os usuários podem acessar para criar e gerenciar anotações.  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## <a name="data-anchoring"></a>Ancoragem de dados  
 A estrutura de anotações vincula anotações aos dados que o usuário seleciona, não apenas a uma posição na exibição de exibição. Portanto, se a exibição de documento mudar, como quando o usuário rolar ou redimensionar a janela de exibição, a anotação permanecerá com a seleção de dados à qual está vinculada. Por exemplo, o gráfico a seguir ilustra uma anotação que o usuário fez em uma seleção de texto. Quando a exibição do documento muda (rola, é redimensionada, tem a escala ajustada ou se move de outra maneira), a anotação de realce se move com a seleção de dados original.  
  
 ![Ancoragem de dados de anotação](./media/caf-dataanchoring.png "CAF_DataAnchoring")  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## <a name="matching-annotations-with-annotated-objects"></a>Combinando anotações com objetos anotados  
 Você pode combinar anotações com os respectivos objetos anotados. Por exemplo, considere um aplicativo de leitor de documento simples que tenha um painel de comentários. O painel de comentários pode ser uma caixa de listagem que exiba texto de uma lista de anotações ancoradas a um documento. Se o usuário selecionar um item na caixa de listagem, o aplicativo trará para a exibição o parágrafo no documento ao qual o objeto de anotação correspondente está ancorado.  
  
 O exemplo a seguir demonstra como implementar o manipulador de eventos de uma caixa de listagem assim que serve como painel de comentários.  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 Outro cenário de exemplo envolve aplicativos que permitem a troca de anotações e anotações adesivas entre leitores de documentos por email. Esse recurso permite que esses aplicativos levem o leitor para a página que contém a anotação que está sendo trocada.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.Primitives.DocumentViewerBase>
- <xref:System.Windows.Controls.DocumentViewer>
- <xref:System.Windows.Controls.FlowDocumentPageViewer>
- <xref:System.Windows.Controls.FlowDocumentScrollViewer>
- <xref:System.Windows.Controls.FlowDocumentReader>
- <xref:System.Windows.Annotations.IAnchorInfo>
- [Esquema de anotações](annotations-schema.md)
- [Visão geral de ContextMenu](../controls/contextmenu-overview.md)
- [Visão geral de comandos](commanding-overview.md)
- [Visão geral do documento de fluxo](flow-document-overview.md)
- [Como: Adicionar um comando a um MenuItem @ no__t-0
