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
ms.openlocfilehash: 2c120c6d71cb22bc38909f980b2f6faf2b5c3663
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395211"
---
# <a name="advanced-text-formatting"></a>Formatação de texto avançada
O Windows Presentation Foundation (WPF) fornece um conjunto robusto de APIs para incluir texto em seu aplicativo. As APIs de layout e [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], como <xref:System.Windows.Controls.TextBlock>, fornecem os elementos de uso mais comuns e gerais para a apresentação de texto. As APIs de desenho, como <xref:System.Windows.Media.GlyphRunDrawing> e <xref:System.Windows.Media.FormattedText>, fornecem um meio para incluir texto formatado em desenhos. No nível mais avançado, o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornece um mecanismo de formatação de texto extensível para controlar cada aspecto da apresentação de texto, como gerenciamento de armazenamento de texto, gerenciamento de formatação de execução de texto e gerenciamento de objetos incorporados.  
  
 Este tópico fornece uma introdução à formatação de texto de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Ele se concentra na implementação do cliente e no uso do mecanismo de formatação de texto [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
> [!NOTE]
> Todos os exemplos de código dentro deste documento podem ser encontrados no [exemplo de formatação de texto avançado](https://go.microsoft.com/fwlink/?LinkID=159965).  

<a name="prereq"></a>   
## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}  
 Este tópico pressupõe que você esteja familiarizado com as APIs de nível superior usadas para a apresentação de texto. A maioria dos cenários de usuário não exigirá as APIs avançadas de formatação de texto discutidas neste tópico. Para obter uma introdução às diferentes APIs de texto, consulte [documentos no WPF](documents-in-wpf.md).  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>Formatação de texto avançada  
 O layout de texto e os controles de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] no [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornecem propriedades de formatação que permitem que você inclua facilmente o texto formatado em seu aplicativo. Esses controles expõem várias propriedades para lidar com a apresentação do texto, que inclui sua face de tipos, tamanho e cor. Em circunstâncias normais, esses controles podem lidar com a maior parte da apresentação do texto em seu aplicativo. No entanto, alguns cenários avançados exigem o controle do armazenamento de texto, bem como a apresentação de texto. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornece um mecanismo de formatação de texto extensível para essa finalidade.  
  
 Os recursos avançados de formatação de texto encontrados em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] consistem em um mecanismo de formatação de texto, um armazenamento de texto, execuções de texto e propriedades de formatação. O mecanismo de formatação de texto, <xref:System.Windows.Media.TextFormatting.TextFormatter>, cria linhas de texto a serem usadas para apresentação. Isso é obtido iniciando o processo de formatação de linha e chamando o <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>do formatador de texto. O formatador de texto recupera as execuções de texto do seu armazenamento de texto chamando o método de <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> do repositório. Os objetos <xref:System.Windows.Media.TextFormatting.TextRun> são então formados em objetos <xref:System.Windows.Media.TextFormatting.TextLine> pelo formatador de texto e fornecidos ao seu aplicativo para inspeção ou exibição.  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>Usando o formatador de texto  
 <xref:System.Windows.Media.TextFormatting.TextFormatter> é o mecanismo de formatação de texto [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] e fornece serviços para formatação e quebra de linhas de texto. O formatador de texto pode lidar com formatos de caracteres de texto diferentes e estilos de parágrafo e inclui suporte para o layout de texto internacional.  
  
 Ao contrário de uma API de texto tradicional, a <xref:System.Windows.Media.TextFormatting.TextFormatter> interage com um cliente de layout de texto por meio de um conjunto de métodos de retorno de chamada. Ele requer que o cliente forneça esses métodos em uma implementação da classe <xref:System.Windows.Media.TextFormatting.TextSource>. O diagrama a seguir ilustra a interação de layout de texto entre o aplicativo cliente e <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagrama de cliente de layout de texto e TextFormatter](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 O formatador de texto é usado para recuperar linhas de texto formatadas do armazenamento de texto, que é uma implementação de <xref:System.Windows.Media.TextFormatting.TextSource>. Isso é feito primeiro criando uma instância do formatador de texto usando o método <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A>. Esse método cria uma instância de formatador de texto e define a altura de linha máxima e os valores de largura. Assim que uma instância do formatador de texto é criada, o processo de criação de linha é iniciado chamando o método <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>. <xref:System.Windows.Media.TextFormatting.TextFormatter> chama de volta para a fonte de texto para recuperar os parâmetros de texto e formatação das execuções de texto que formam uma linha.  
  
 No exemplo a seguir, o processo de formatação de um repositório de texto é mostrado. O objeto <xref:System.Windows.Media.TextFormatting.TextFormatter> é usado para recuperar linhas de texto do repositório de texto e formatar a linha de texto para desenhar na <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>Implementando o repositório de texto do cliente  
 Ao estender o mecanismo de formatação de texto, é necessário implementar e gerenciar todos os aspectos do repositório de texto. Isso não é uma tarefa trivial. O repositório de texto é responsável por acompanhar propriedades de execução de texto, propriedades de parágrafo, objetos incorporados e outros conteúdos semelhantes. Ele também fornece o formatador de texto com objetos <xref:System.Windows.Media.TextFormatting.TextRun> individuais que o formatador de texto usa para criar <xref:System.Windows.Media.TextFormatting.TextLine> objetos.  
  
 Para lidar com a virtualização do armazenamento de texto, o armazenamento de texto deve ser derivado de <xref:System.Windows.Media.TextFormatting.TextSource>. <xref:System.Windows.Media.TextFormatting.TextSource> define o método que o formatador de texto usa para recuperar as execuções de texto do armazenamento de texto. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> é o método usado pelo formatador de texto para recuperar as execuções de texto usadas na formatação de linha. A chamada para <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> é feita repetidamente pelo formatador de texto até que ocorra uma das seguintes condições:  
  
- Um <xref:System.Windows.Media.TextFormatting.TextEndOfLine> ou uma subclasse é retornada.  
  
- A largura acumulada de execuções de texto excede a largura de linha máxima especificada na chamada para criar o formatador de texto ou a chamada para o método de <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> do formatador de texto.  
  
- Uma seqüência de nova linha Unicode, como "CF", "LF" ou "CRLF", é retornada.  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>Fornecendo execuções de texto  
 O núcleo do processo de formatação de texto é a interação entre o formatador de texto e o repositório de texto. Sua implementação de <xref:System.Windows.Media.TextFormatting.TextSource> fornece o formatador de texto com os objetos <xref:System.Windows.Media.TextFormatting.TextRun> e as propriedades com as quais formatar as execuções de texto. Essa interação é tratada pelo método <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>, que é chamado pelo formatador de texto.  
  
 A tabela a seguir mostra alguns dos objetos <xref:System.Windows.Media.TextFormatting.TextRun> predefinidos.  
  
|Tipo de TextRun|Uso|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|A execução de texto especializado para passar uma representação de glifos de caractere de volta para o formatador de texto.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|A execução de texto especializado usada para fornecer conteúdo no qual a medição, o teste de hit e o desenho são feitos no todo, como um botão ou imagem dentro do texto.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|A execução de texto especializado usada para marcar o final de uma linha.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|A execução de texto especializado usada para marcar o final de um parágrafo.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|A execução de texto especializada usada para marcar o final de um segmento, como para finalizar o escopo afetado por uma execução de <xref:System.Windows.Media.TextFormatting.TextModifier> anterior.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|A execução de texto especializado usada para marcar um intervalo de caracteres ocultos.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|A execução de texto especializado usada para modificar as propriedades das execuções de texto nesse escopo. O escopo se estende à próxima execução de texto de <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> correspondente ou à próxima <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>.|  
  
 Qualquer um dos objetos de <xref:System.Windows.Media.TextFormatting.TextRun> predefinidos pode ser subclasse. Isso permite que a fonte de texto forneça ao formatador de texto as execuções de texto que incluem dados personalizados.  
  
 O exemplo a seguir demonstra um método <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>. Esse repositório de texto retorna <xref:System.Windows.Media.TextFormatting.TextRun> objetos ao formatador de texto para processamento.  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
> Neste exemplo, o repositório de texto fornece as mesmas propriedades de texto para todo o texto. Os armazenamentos avançados de texto precisariam implementar seus próprios gerenciamentos de período para permitir caracteres individuais com propriedades diferentes.  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>Especificando propriedades de formatação  
 <xref:System.Windows.Media.TextFormatting.TextRun> objetos são formatados usando as propriedades fornecidas pelo armazenamento de texto. Essas propriedades são fornecidas em dois tipos, <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> e <xref:System.Windows.Media.TextFormatting.TextRunProperties>. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> manipular propriedades inclusivas de parágrafo, como <xref:System.Windows.TextAlignment> e <xref:System.Windows.FlowDirection>. <xref:System.Windows.Media.TextFormatting.TextRunProperties> são propriedades que podem ser diferentes para cada execução de texto dentro de um parágrafo, como o pincel de primeiro plano, o <xref:System.Windows.Media.Typeface>e o tamanho da fonte. Para implementar um parágrafo personalizado e tipos de propriedade de execução de texto personalizado, seu aplicativo deve criar classes que derivam de <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> e <xref:System.Windows.Media.TextFormatting.TextRunProperties>, respectivamente.  
  
## <a name="see-also"></a>Consulte também

- [Tipografia no WPF](typography-in-wpf.md)
- [Documentos no WPF](documents-in-wpf.md)
