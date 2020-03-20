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
ms.openlocfilehash: 745d20e0bd4f877f9d4559f9fc7829b56689d35c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185935"
---
# <a name="advanced-text-formatting"></a>Formatação de texto avançada
O Windows Presentation Foundation (WPF) fornece um conjunto robusto de APIs para incluir texto em seu aplicativo. Layout [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] e APIs, <xref:System.Windows.Controls.TextBlock>tais como, fornecem os elementos mais comuns e de uso geral para apresentação de texto. As APIs de <xref:System.Windows.Media.GlyphRunDrawing> <xref:System.Windows.Media.FormattedText>desenho, como e , fornecem um meio para incluir texto formatado em desenhos. No nível mais avançado, o WPF fornece um mecanismo de formatação de texto extensível para controlar todos os aspectos da apresentação de texto, como gerenciamento de armazenamento de texto, gerenciamento de formatação de execução de texto e gerenciamento de objetos incorporados.  
  
 Este tópico fornece uma introdução à formatação de texto WPF. Ele se concentra na implementação do cliente e no uso do mecanismo de formatação de texto WPF.  
  
> [!NOTE]
> Todos os exemplos de código dentro deste documento podem ser encontrados na [Amostra de Formatação de Texto Avançada](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI/TextFormatting).  

<a name="prereq"></a>
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você esteja familiarizado com as APIs de nível mais alto usadas para apresentação de texto. A maioria dos cenários de usuários não exigirá as APIs de formatação de texto avançadas discutidas neste tópico. Para obter uma introdução às diferentes APIs de texto, consulte [Documentos no WPF](documents-in-wpf.md).  
  
<a name="section1"></a>
## <a name="advanced-text-formatting"></a>Formatação de texto avançada  
 O layout [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de texto e os controles no WPF fornecem propriedades de formatação que permitem incluir facilmente texto formatado em seu aplicativo. Esses controles expõem várias propriedades para lidar com a apresentação do texto, que inclui sua face de tipos, tamanho e cor. Em circunstâncias normais, esses controles podem lidar com a maior parte da apresentação do texto em seu aplicativo. No entanto, alguns cenários avançados exigem o controle do armazenamento de texto, bem como a apresentação de texto. O WPF fornece um mecanismo de formatação de texto extensível para este fim.  
  
 Os recursos avançados de formatação de texto encontrados no WPF consistem em um mecanismo de formatação de texto, uma loja de texto, executões de texto e propriedades de formatação. O mecanismo de <xref:System.Windows.Media.TextFormatting.TextFormatter>formatação de texto, cria linhas de texto a serem usadas para apresentação. Isso é conseguido ao início do processo de formatação de linhas <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>e chamada de texto formatter's . O texto formatter recupera o texto executado a partir <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> de sua loja de texto, chamando o método da loja. Os <xref:System.Windows.Media.TextFormatting.TextRun> objetos são <xref:System.Windows.Media.TextFormatting.TextLine> então formados em objetos pelo texto formatter e entregues ao seu pedido de inspeção ou exibição.  
  
<a name="section2"></a>
## <a name="using-the-text-formatter"></a>Usando o formatador de texto  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>é o mecanismo de formatação de texto WPF e fornece serviços para formatação e quebra de linhas de texto. O formatador de texto pode lidar com formatos de caracteres de texto diferentes e estilos de parágrafo e inclui suporte para o layout de texto internacional.  
  
 Ao contrário de uma <xref:System.Windows.Media.TextFormatting.TextFormatter> API de texto tradicional, a interação com um cliente de layout de texto através de um conjunto de métodos de retorno de chamada. Exige que o cliente forneça esses métodos <xref:System.Windows.Media.TextFormatting.TextSource> em uma implementação da classe. O diagrama a seguir ilustra a interação <xref:System.Windows.Media.TextFormatting.TextFormatter>do layout de texto entre o aplicativo cliente e .  
  
 ![Diagrama de cliente de layout de texto e TextFormatter](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 O texto formatter é usado para recuperar linhas de texto formatados do armazenamento de texto, que é uma implementação de <xref:System.Windows.Media.TextFormatting.TextSource>. Isso é feito criando primeiro uma instância do <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> texto formatter usando o método. Esse método cria uma instância de formatador de texto e define a altura de linha máxima e os valores de largura. Assim que uma instância do texto formatter é criada, o processo <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> de criação de linhas é iniciado chamando o método. <xref:System.Windows.Media.TextFormatting.TextFormatter>chama de volta para a fonte de texto para recuperar o texto e os parâmetros de formatação para as linhas de texto que formam uma linha.  
  
 No exemplo a seguir, o processo de formatação de um repositório de texto é mostrado. O <xref:System.Windows.Media.TextFormatting.TextFormatter> objeto é usado para recuperar linhas de texto do armazenamento <xref:System.Windows.Media.DrawingContext>de texto e, em seguida, formatar a linha de texto para desenho na .  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>
## <a name="implementing-the-client-text-store"></a>Implementando o repositório de texto do cliente  
 Ao estender o mecanismo de formatação de texto, é necessário implementar e gerenciar todos os aspectos do repositório de texto. Isso não é uma tarefa trivial. O repositório de texto é responsável por acompanhar propriedades de execução de texto, propriedades de parágrafo, objetos incorporados e outros conteúdos semelhantes. Ele também fornece o texto <xref:System.Windows.Media.TextFormatting.TextRun> formatter com objetos <xref:System.Windows.Media.TextFormatting.TextLine> individuais que o texto formatter usa para criar objetos.  
  
 Para lidar com a virtualização da loja de texto, a loja de texto deve ser derivada de <xref:System.Windows.Media.TextFormatting.TextSource>. <xref:System.Windows.Media.TextFormatting.TextSource>define o método que o texto formatter usa para recuperar o texto executado no armazenamento de texto. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>é o método usado pelo texto formatter para recuperar as executas de texto usadas na formatação de linha. A chamada <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> é repetidamente feita pelo texto até que ocorra uma das seguintes condições:  
  
- A <xref:System.Windows.Media.TextFormatting.TextEndOfLine> ou uma subclasse é devolvida.  
  
- A largura acumulada das corridas de texto excede a largura máxima de linha especificada na chamada <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> para criar o texto formatter ou na chamada para o método do texto formatter.  
  
- Uma seqüência de linha nova Unicode, como "CF", "LF" ou "CRLF", é devolvida.  
  
<a name="section4"></a>
## <a name="providing-text-runs"></a>Fornecendo execuções de texto  
 O núcleo do processo de formatação de texto é a interação entre o formatador de texto e o repositório de texto. Sua implementação <xref:System.Windows.Media.TextFormatting.TextSource> fornece o texto <xref:System.Windows.Media.TextFormatting.TextRun> formatter com os objetos e as propriedades com as quais formatar o texto é executado. Essa interação é tratada <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> pelo método, que é chamado pelo texto formatter.  
  
 A tabela a seguir mostra <xref:System.Windows.Media.TextFormatting.TextRun> alguns dos objetos predefinidos.  
  
|Tipo de TextRun|Uso|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|A execução de texto especializado para passar uma representação de glifos de caractere de volta para o formatador de texto.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|A execução de texto especializado usada para fornecer conteúdo no qual a medição, o teste de hit e o desenho são feitos no todo, como um botão ou imagem dentro do texto.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|A execução de texto especializado usada para marcar o final de uma linha.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|A execução de texto especializado usada para marcar o final de um parágrafo.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|A execução de texto especializado é usada para marcar o fim de <xref:System.Windows.Media.TextFormatting.TextModifier> um segmento, como para acabar com o escopo afetado por uma execução anterior.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|A execução de texto especializado usada para marcar um intervalo de caracteres ocultos.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|A execução de texto especializado usada para modificar as propriedades das execuções de texto nesse escopo. O escopo se estende <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> até a próxima <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>execução de texto correspondente, ou a próxima .|  
  
 Qualquer um dos <xref:System.Windows.Media.TextFormatting.TextRun> objetos predefinidos pode ser subclassificado. Isso permite que a fonte de texto forneça ao formatador de texto as execuções de texto que incluem dados personalizados.  
  
 O exemplo a <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> seguir demonstra um método. Esta loja <xref:System.Windows.Media.TextFormatting.TextRun> de texto retorna objetos para o texto formatter para processamento.  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
> Neste exemplo, o repositório de texto fornece as mesmas propriedades de texto para todo o texto. Os armazenamentos avançados de texto precisariam implementar seus próprios gerenciamentos de período para permitir caracteres individuais com propriedades diferentes.  
  
<a name="section5"></a>
## <a name="specifying-formatting-properties"></a>Especificando propriedades de formatação  
 <xref:System.Windows.Media.TextFormatting.TextRun>os objetos são formatados usando propriedades fornecidas pelo armazenamento de texto. Essas propriedades vêm em <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> <xref:System.Windows.Media.TextFormatting.TextRunProperties>dois tipos, e . <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>lidar com propriedades <xref:System.Windows.TextAlignment> inclusivas de parágrafo, tais como e <xref:System.Windows.FlowDirection>. <xref:System.Windows.Media.TextFormatting.TextRunProperties>são propriedades que podem ser diferentes para cada texto executado <xref:System.Windows.Media.Typeface>dentro de um parágrafo, como escova de primeiro plano, e tamanho da fonte. Para implementar os tipos de propriedade de execução de <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> texto <xref:System.Windows.Media.TextFormatting.TextRunProperties> personalizadoe e de texto personalizado, seu aplicativo deve criar classes derivadas e respectivamente.  
  
## <a name="see-also"></a>Confira também

- [Tipografia no WPF](typography-in-wpf.md)
- [Documentos no WPF](documents-in-wpf.md)
