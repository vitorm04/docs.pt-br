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
ms.openlocfilehash: 03d0c5096876305f9a181cc28ff2158066e4d56f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577360"
---
# <a name="advanced-text-formatting"></a>Formatação de texto avançada
O Windows Presentation Foundation (WPF) fornece um conjunto robusto de [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] para incluir o texto em seu aplicativo. Layout e [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], como <xref:System.Windows.Controls.TextBlock>, forneça os mais comuns e elementos de uso geral para apresentação de texto. Desenhando [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], como <xref:System.Windows.Media.GlyphRunDrawing> e <xref:System.Windows.Media.FormattedText>, fornecem um meio para incluir o texto formatado em desenhos. Mais avançado nível, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornece um mecanismo para controlar todos os aspectos da apresentação de texto, como gerenciamento de armazenamento de texto, gerenciamento de formatação de sequência de texto e gerenciamento do objeto inserido de formatação de texto extensível.  
  
 Este tópico fornece uma introdução ao [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] formatação de texto. Ele se concentra na implementação de cliente e o uso do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] mecanismo de formatação de texto.  
  
> [!NOTE]
>  Todos os exemplos de código neste documento podem ser encontrados na [exemplo de formatação de texto avançada](https://go.microsoft.com/fwlink/?LinkID=159965).  
  

  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você esteja familiarizado com o nível mais alto [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] usado para apresentação de texto. A maioria dos cenários de usuário não exigirá a formatação de texto avançada [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] discutidos neste tópico. Para obter uma introdução ao texto diferente [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], consulte [documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>Formatação de texto avançada  
 O layout de texto e [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] controles em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornecem propriedades de formatação que permitem que você inclua facilmente texto formatado em seu aplicativo. Esses controles expõem várias propriedades para lidar com a apresentação do texto, que inclui sua face de tipos, tamanho e cor. Em circunstâncias normais, esses controles podem lidar com a maior parte da apresentação do texto em seu aplicativo. No entanto, alguns cenários avançados exigem o controle do armazenamento de texto, bem como a apresentação de texto. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fornece um mecanismo de formatação de texto extensível para essa finalidade.  
  
 O recursos de formatação de texto avançada encontrados no [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] consistem em um mecanismo, um armazenamento de texto, sequências de texto de formatação e propriedades de formatação de texto. O mecanismo de formatação de texto <xref:System.Windows.Media.TextFormatting.TextFormatter>, cria linhas de texto a ser usado para apresentação. Isso é possível iniciar o processo de formatação de linha e chamando o formatador de texto <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>. O formatador de texto recupera sequências de texto de seu repositório de texto chamando o repositório <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> método. O <xref:System.Windows.Media.TextFormatting.TextRun> objetos, em seguida, são moldados <xref:System.Windows.Media.TextFormatting.TextLine> objetos pelo formatador de texto e dados a seu aplicativo para inspeção ou exibição.  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>Usando o formatador de texto  
 <xref:System.Windows.Media.TextFormatting.TextFormatter> é o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] mecanismo de formatação de texto e fornece serviços para formatação e quebra de linhas de texto. O formatador de texto pode lidar com formatos de caracteres de texto diferentes e estilos de parágrafo e inclui suporte para o layout de texto internacional.  
  
 Ao contrário de um texto tradicional [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)], o <xref:System.Windows.Media.TextFormatting.TextFormatter> interage com um cliente de layout de texto por meio de um conjunto de métodos de retorno de chamada. Requer que o cliente forneça esses métodos em uma implementação da <xref:System.Windows.Media.TextFormatting.TextSource> classe. O diagrama a seguir ilustra a interação de layout de texto entre o aplicativo cliente e <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagrama de cliente de layout de texto e TextFormatter](../../../../docs/framework/wpf/advanced/media/textformatter01.png "TextFormatter01")  
Interação entre o aplicativo e o TextFormatter  
  
 O formatador de texto é usado para recuperar linhas de texto formatado do armazenamento de texto, que é uma implementação de <xref:System.Windows.Media.TextFormatting.TextSource>. Isso é feito criando primeiro uma instância do formatador de texto usando o <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> método. Esse método cria uma instância de formatador de texto e define a altura de linha máxima e os valores de largura. Assim que uma instância do formatador de texto é criada, o processo de criação de linha é iniciado ao chamar o <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> método. <xref:System.Windows.Media.TextFormatting.TextFormatter> chama de volta para a fonte de texto para recuperar o texto e os parâmetros de formatação para execuções de texto que formam uma linha.  
  
 No exemplo a seguir, o processo de formatação de um repositório de texto é mostrado. O <xref:System.Windows.Media.TextFormatting.TextFormatter> objeto é usado para recuperar linhas de texto do repositório de texto e, em seguida, formate a linha de texto para o desenho no <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[TextFormatterExample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>Implementando o repositório de texto do cliente  
 Ao estender o mecanismo de formatação de texto, é necessário implementar e gerenciar todos os aspectos do repositório de texto. Isso não é uma tarefa trivial. O repositório de texto é responsável por acompanhar propriedades de execução de texto, propriedades de parágrafo, objetos incorporados e outros conteúdos semelhantes. Ele também fornece o formatador de texto com o indivíduo <xref:System.Windows.Media.TextFormatting.TextRun> objetos que o formatador de texto usa para criar <xref:System.Windows.Media.TextFormatting.TextLine> objetos.  
  
 Para lidar com a virtualização do armazenamento de texto, o repositório de texto deve ser derivado de <xref:System.Windows.Media.TextFormatting.TextSource>. <xref:System.Windows.Media.TextFormatting.TextSource> Define o método que o formatador de texto usa para recuperar as execuções de texto do armazenamento de texto. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> é o método usado pelo formatador de texto para recuperar texto executa usado na formatação de linha. A chamada para <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> é feita repetidamente com o formatador de texto até que uma das seguintes condições ocorra:  
  
-   Um <xref:System.Windows.Media.TextFormatting.TextEndOfLine> ou uma subclasse é retornada.  
  
-   A largura acumulada das execuções de texto excede a largura máxima da linha especificada na chamada para criar o formatador de texto ou a chamada para o formatador de texto <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> método.  
  
-   Um [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] sequência de nova linha, como "CF", "LF" ou "CRLF", será retornada.  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>Fornecendo execuções de texto  
 O núcleo do processo de formatação de texto é a interação entre o formatador de texto e o repositório de texto. Sua implementação de <xref:System.Windows.Media.TextFormatting.TextSource> fornece o formatador de texto com o <xref:System.Windows.Media.TextFormatting.TextRun> objetos e as propriedades com o qual formatar o texto é executado. Essa interação é tratada pelo <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> método, que é chamado pelo formatador de texto.  
  
 A tabela a seguir mostra alguns dos predefinido <xref:System.Windows.Media.TextFormatting.TextRun> objetos.  
  
|Tipo de TextRun|Uso|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|A execução de texto especializado para passar uma representação de glifos de caractere de volta para o formatador de texto.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|A execução de texto especializado usada para fornecer conteúdo no qual a medição, o teste de hit e o desenho são feitos no todo, como um botão ou imagem dentro do texto.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|A execução de texto especializado usada para marcar o final de uma linha.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|A execução de texto especializado usada para marcar o final de um parágrafo.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|O execução de texto especializado usada para marcar o final de um segmento, como para encerrar o escopo afetado por uma anterior <xref:System.Windows.Media.TextFormatting.TextModifier> executar.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|A execução de texto especializado usada para marcar um intervalo de caracteres ocultos.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|A execução de texto especializado usada para modificar as propriedades das execuções de texto nesse escopo. O escopo se estende para a próxima correspondência <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> sequência de texto ou o próximo <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>.|  
  
 Qualquer um dos predefinido <xref:System.Windows.Media.TextFormatting.TextRun> objetos podem ser uma subclasse. Isso permite que a fonte de texto forneça ao formatador de texto as execuções de texto que incluem dados personalizados.  
  
 O exemplo a seguir demonstra um <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> método. Esse repositório de texto retorna <xref:System.Windows.Media.TextFormatting.TextRun> objetos para o formatador de texto para processamento.  
  
 [!code-csharp[TextFormatterExample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
>  Neste exemplo, o repositório de texto fornece as mesmas propriedades de texto para todo o texto. Os armazenamentos avançados de texto precisariam implementar seus próprios gerenciamentos de período para permitir caracteres individuais com propriedades diferentes.  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>Especificando propriedades de formatação  
 <xref:System.Windows.Media.TextFormatting.TextRun> objetos são formatados usando propriedades fornecidas pelo repositório de texto. Essas propriedades são fornecidas em dois tipos <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> e <xref:System.Windows.Media.TextFormatting.TextRunProperties>. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> lidar com propriedades inclusivas do parágrafo, como <xref:System.Windows.TextAlignment> e <xref:System.Windows.FlowDirection>. <xref:System.Windows.Media.TextFormatting.TextRunProperties> são propriedades que podem ser diferentes para cada execução dentro de um parágrafo, como o pincel de primeiro plano, de texto <xref:System.Windows.Media.Typeface>e o tamanho da fonte. Para implementar o parágrafo personalizado e os tipos de propriedade de execução de texto personalizado, seu aplicativo deve criar classes que derivam de <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> e <xref:System.Windows.Media.TextFormatting.TextRunProperties> , respectivamente.  
  
## <a name="see-also"></a>Consulte também
- [Tipografia no WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)
- [Documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
