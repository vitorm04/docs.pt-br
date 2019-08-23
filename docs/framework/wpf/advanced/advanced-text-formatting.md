---
title: Formatação de texto avançada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [WPF]
- text [WPF]
- typography [WPF], text formatting
ms.assetid: f0a7986e-f5b2-485c-a27d-f8e922022212
ms.openlocfilehash: 469c62691ff38a8c5a01bec3ddfd7b324bab7eca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969064"
---
# <a name="advanced-text-formatting"></a>Formatação de texto avançada
O Windows Presentation Foundation (WPF) fornece um conjunto robusto de APIs para incluir texto em seu aplicativo. Layout e [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]APIs, <xref:System.Windows.Controls.TextBlock>como, fornecem os elementos de uso mais comuns e gerais para apresentação de texto. As <xref:System.Windows.Media.GlyphRunDrawing> APIs de desenho, como <xref:System.Windows.Media.FormattedText>e, fornecem um meio para incluir texto formatado em desenhos. No nível mais avançado, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] o fornece um mecanismo de formatação de texto extensível para controlar cada aspecto da apresentação de texto, como gerenciamento de armazenamento de texto, gerenciamento de formatação de execução de texto e gerenciamento de objetos incorporados.  
  
 Este tópico fornece uma introdução à [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] formatação de texto. Ele se concentra na implementação do cliente e no uso [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] do mecanismo de formatação de texto.  
  
> [!NOTE]
> Todos os exemplos de código dentro deste documento podem ser encontrados no [exemplo de formatação de texto avançado](https://go.microsoft.com/fwlink/?LinkID=159965).  

<a name="prereq"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você esteja familiarizado com as APIs de nível superior usadas para a apresentação de texto. A maioria dos cenários de usuário não exigirá as APIs avançadas de formatação de texto discutidas neste tópico. Para obter uma introdução às diferentes APIs de texto, consulte [documentos no WPF](documents-in-wpf.md).  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>Formatação de texto avançada  
 O layout de texto [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] e os [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] controles no fornecem propriedades de formatação que permitem que você inclua facilmente texto formatado em seu aplicativo. Esses controles expõem várias propriedades para lidar com a apresentação do texto, que inclui sua face de tipos, tamanho e cor. Em circunstâncias normais, esses controles podem lidar com a maior parte da apresentação do texto em seu aplicativo. No entanto, alguns cenários avançados exigem o controle do armazenamento de texto, bem como a apresentação de texto. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornece um mecanismo de formatação de texto extensível para essa finalidade.  
  
 Os recursos avançados de formatação de texto [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] encontrados em consistem em um mecanismo de formatação de texto, um armazenamento de texto, execuções de texto e propriedades de formatação. O mecanismo de formatação de <xref:System.Windows.Media.TextFormatting.TextFormatter>texto,, cria linhas de texto a serem usadas para apresentação. Isso é obtido iniciando o processo de formatação de linha e chamando o formatador <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>de texto. O formatador de texto recupera as execuções de texto do seu armazenamento de <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> texto chamando o método do repositório. Os <xref:System.Windows.Media.TextFormatting.TextRun> objetos são então formados <xref:System.Windows.Media.TextFormatting.TextLine> em objetos pelo formatador de texto e fornecidos ao seu aplicativo para inspeção ou exibição.  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>Usando o formatador de texto  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>é o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] mecanismo de formatação de texto e fornece serviços para formatação e quebra de linhas de texto. O formatador de texto pode lidar com formatos de caracteres de texto diferentes e estilos de parágrafo e inclui suporte para o layout de texto internacional.  
  
 Ao contrário de uma API de texto <xref:System.Windows.Media.TextFormatting.TextFormatter> tradicional, o interage com um cliente de layout de texto por meio de um conjunto de métodos de retorno de chamada. Ele requer que o cliente forneça esses métodos em uma implementação da <xref:System.Windows.Media.TextFormatting.TextSource> classe. O diagrama a seguir ilustra a interação de layout de texto entre o <xref:System.Windows.Media.TextFormatting.TextFormatter>aplicativo cliente e o.  
  
 ![Diagrama de cliente de layout de texto e TextFormatter](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 O formatador de texto é usado para recuperar linhas de texto formatadas do armazenamento de texto, que <xref:System.Windows.Media.TextFormatting.TextSource>é uma implementação do. Isso é feito primeiro criando uma instância do formatador de texto usando o <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> método. Esse método cria uma instância de formatador de texto e define a altura de linha máxima e os valores de largura. Assim que uma instância do formatador de texto é criada, o processo de criação de linha é iniciado chamando <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> o método. <xref:System.Windows.Media.TextFormatting.TextFormatter>chama de volta para a fonte de texto para recuperar os parâmetros de texto e formatação das execuções de texto que formam uma linha.  
  
 No exemplo a seguir, o processo de formatação de um repositório de texto é mostrado. O <xref:System.Windows.Media.TextFormatting.TextFormatter> objeto é usado para recuperar linhas de texto do repositório de texto e, em seguida, formatar a linha de <xref:System.Windows.Media.DrawingContext>texto para desenhar no.  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>Implementando o repositório de texto do cliente  
 Ao estender o mecanismo de formatação de texto, é necessário implementar e gerenciar todos os aspectos do repositório de texto. Isso não é uma tarefa trivial. O repositório de texto é responsável por acompanhar propriedades de execução de texto, propriedades de parágrafo, objetos incorporados e outros conteúdos semelhantes. Ele também fornece o formatador de texto <xref:System.Windows.Media.TextFormatting.TextRun> com objetos individuais que o formatador de <xref:System.Windows.Media.TextFormatting.TextLine> texto usa para criar objetos.  
  
 Para lidar com a virtualização do armazenamento de texto, o armazenamento de texto deve <xref:System.Windows.Media.TextFormatting.TextSource>ser derivado de. <xref:System.Windows.Media.TextFormatting.TextSource>define o método que o formatador de texto usa para recuperar as execuções de texto do armazenamento de texto. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>é o método usado pelo formatador de texto para recuperar as execuções de texto usadas na formatação de linha. A chamada para <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> é feita repetidamente pelo formatador de texto até que ocorra uma das seguintes condições:  
  
- Uma <xref:System.Windows.Media.TextFormatting.TextEndOfLine> subclasse ou é retornada.  
  
- A largura acumulada de execuções de texto excede a largura máxima da linha especificada na chamada para criar o formatador de texto ou a chamada para o <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> método do formatador de texto.  
  
- Uma [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] seqüência de nova linha, como "CF", "LF" ou "CRLF", é retornada.  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>Fornecendo execuções de texto  
 O núcleo do processo de formatação de texto é a interação entre o formatador de texto e o repositório de texto. Sua implementação do <xref:System.Windows.Media.TextFormatting.TextSource> fornece o formatador de texto <xref:System.Windows.Media.TextFormatting.TextRun> com os objetos e as propriedades com as quais formatar as execuções de texto. Essa interação é manipulada pelo <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> método, que é chamado pelo formatador de texto.  
  
 A tabela a seguir mostra alguns dos objetos <xref:System.Windows.Media.TextFormatting.TextRun> predefinidos.  
  
|Tipo de TextRun|Uso|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|A execução de texto especializado para passar uma representação de glifos de caractere de volta para o formatador de texto.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|A execução de texto especializado usada para fornecer conteúdo no qual a medição, o teste de hit e o desenho são feitos no todo, como um botão ou imagem dentro do texto.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|A execução de texto especializado usada para marcar o final de uma linha.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|A execução de texto especializado usada para marcar o final de um parágrafo.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|A execução de texto especializada usada para marcar o final de um segmento, como para finalizar o escopo afetado por uma <xref:System.Windows.Media.TextFormatting.TextModifier> execução anterior.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|A execução de texto especializado usada para marcar um intervalo de caracteres ocultos.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|A execução de texto especializado usada para modificar as propriedades das execuções de texto nesse escopo. O escopo se estende à próxima execução <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> de texto correspondente ou ao próximo <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>.|  
  
 Qualquer um dos objetos <xref:System.Windows.Media.TextFormatting.TextRun> predefinidos pode ser subclasse. Isso permite que a fonte de texto forneça ao formatador de texto as execuções de texto que incluem dados personalizados.  
  
 O exemplo a seguir demonstra <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> um método. Esse repositório de texto <xref:System.Windows.Media.TextFormatting.TextRun> retorna objetos para o formatador de texto para processamento.  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
> Neste exemplo, o repositório de texto fornece as mesmas propriedades de texto para todo o texto. Os armazenamentos avançados de texto precisariam implementar seus próprios gerenciamentos de período para permitir caracteres individuais com propriedades diferentes.  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>Especificando propriedades de formatação  
 <xref:System.Windows.Media.TextFormatting.TextRun>os objetos são formatados usando as propriedades fornecidas pelo armazenamento de texto. Essas propriedades vêm em dois tipos, <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> e <xref:System.Windows.Media.TextFormatting.TextRunProperties>. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>manipule Propriedades inclusivas de parágrafo <xref:System.Windows.TextAlignment> , <xref:System.Windows.FlowDirection>como e. <xref:System.Windows.Media.TextFormatting.TextRunProperties>são propriedades que podem ser diferentes para cada execução de texto dentro de um parágrafo, como o pincel <xref:System.Windows.Media.Typeface>de primeiro plano, e o tamanho da fonte. Para implementar um parágrafo personalizado e tipos de propriedade de execução de texto personalizado, seu aplicativo deve criar <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> classes <xref:System.Windows.Media.TextFormatting.TextRunProperties> que derivam de e respectivamente.  
  
## <a name="see-also"></a>Consulte também

- [Tipografia no WPF](typography-in-wpf.md)
- [Documentos no WPF](documents-in-wpf.md)
