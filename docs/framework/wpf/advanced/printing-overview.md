---
title: Visão geral da impressão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print path [WPF], XPS
- printers [WPF], XPSDrv-based
- printing [WPF]
- PrintQueue class PrintServer class [WPF]
- XML Paper Specification (XPS) file format
- XPS (XML Paper Specification) file format
- XPSDrv-based printers
- GDI print path [WPF]
ms.assetid: 0de8ac41-9aa6-413d-a121-7aa6f41539b1
ms.openlocfilehash: 902d51341850b5245b9fa6410b1954b2ab373bbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187209"
---
# <a name="printing-overview"></a>Visão geral da impressão
Com o Microsoft .NET Framework, os desenvolvedores de aplicativos que usam o Windows Presentation Foundation (WPF) têm um rico novo conjunto de APIs de gerenciamento de sistemas de impressão e impressão. Com o Windows Vista, alguns desses aprimoramentos do sistema de impressão também estão disponíveis para desenvolvedores que criam aplicativos e desenvolvedores do Windows Forms usando código não gerenciado. No centro desta nova funcionalidade está o novo formato de arquivo XML Paper Specification (XPS) e o caminho de impressão XPS.  
  
 Este tópico inclui as seções a seguir.  
  
<a name="introduction_to_XPS"></a>
## <a name="about-xps"></a>Sobre XPS  
 XPS é um formato de documento eletrônico, um formato de arquivo de bobina e uma linguagem de descrição de página. É um formato de documento aberto que usa XML, Open Packaging Conventions (OPC) e outros padrões do setor para criar documentos multiplataforma. O XPS simplifica o processo pelo qual os documentos digitais são criados, compartilhados, impressos, visualizados e arquivados. Para obter informações adicionais sobre o XPS, consulte [Documentos XPS](/windows/desktop/printdocs/documents).  
  
 Várias técnicas para impressão de conteúdo baseado em XPS usando WPF são demonstradas em [Arquivos XPS de impressão programática](how-to-programmatically-print-xps-files.md). Talvez seja útil consultar esses exemplos durante o exame do conteúdo contido neste tópico. (Os desenvolvedores de código não gerenciados devem ver a documentação para a [função MXDC_ESCAPE](/windows/desktop/printdocs/mxdc-escape). Os desenvolvedores do Windows Forms <xref:System.Drawing.Printing> devem usar a API no namespace que não suporta o caminho de impressão XPS completo, mas suporta um caminho de impressão GDI-para-XPS híbrido. Consulte **Arquitetura de caminho de impressão** abaixo).  
  
<a name="XPS_print_path_intro"></a>
## <a name="xps-print-path"></a>Caminho de impressão XPS  
 O caminho de impressão XML Paper Specification (XPS) é um novo recurso do Windows que redefine como a impressão é tratada em aplicativos Windows. Como o XPS pode substituir uma linguagem de apresentação de documentos (como RTF), um formato de spooler de impressão (como WMF) e um idioma de descrição de página (como PCL ou Postscript); o novo caminho de impressão mantém o formato XPS desde a publicação do aplicativo até o processamento final no driver de impressão ou dispositivo.  
  
 O caminho de impressão XPS é construído sobre o modelo de driver de impressora XPS (XPSDrv), que fornece vários benefícios para desenvolvedores, como impressão "o que você vê é o que você recebe" (WYSIWYG), melhor suporte a cores e desempenho de impressão significativamente melhorado. (Para obter mais informações sobre o XPSDrv, consulte a [documentação](/windows-hardware/drivers/)do Kit de Driver do Windows .)  
  
 O funcionamento do spooler de impressão para documentos XPS é essencialmente o mesmo das versões anteriores do Windows. No entanto, ele foi aprimorado para suportar o caminho de impressão XPS, além do caminho de impressão GDI existente. O novo caminho de impressão consome nativamente um arquivo de bobina XPS. Enquanto os drivers de impressora do modo de usuário gravados para versões anteriores do Windows continuarão a funcionar, um driver de impressora XPS (XPSDrv) é necessário para usar o caminho de impressão XPS.  
  
 Os benefícios do caminho de impressão XPS são significativos e incluem:  
  
- Suporte à impressão WYSIWYG  
  
- Suporte nativo a perfis de cores avançados, que incluem 32 bits por canal (bpc), CMYK, cores nomeadas, n-inks e suporte nativo à transparência e gradientes.  
  
- Desempenho de impressão aprimorado para aplicativos baseados em .NET Framework e Win32.  
  
- Formato PADRÃO do setor XPS.  
  
 Para cenários básicos de impressão, uma API simples e intuitiva está disponível com um único ponto de entrada para interface de usuário, configuração e envio de trabalho. Para cenários avançados, foi adicionado um suporte extra para a personalização de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] (ou mesmo para nenhuma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]), para a impressão síncrona ou assíncrona e recursos de impressão de lote. As duas opções fornecem suporte de impressão no modo de confiança total ou parcial.  
  
 A XPS foi projetada com extensibilidade em mente. Usando a estrutura de extensibilidade, recursos e recursos podem ser adicionados ao XPS de forma modular. Os recursos de extensibilidade incluem:  
  
- Esquema de Impressão. O esquema público é atualizado regularmente e permite a rápida extensão de recursos do dispositivo. (Consulte **PrintTicket e PrintCapabilities** abaixo).  
  
- Pipeline de filtro extensível. O pipeline de filtro xps driver de impressora (XPSDrv) foi projetado para permitir a impressão direta e escalável de documentos XPS. Para obter mais informações, consulte [os drivers de impressora XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers).
  
### <a name="print-path-architecture"></a>Arquitetura de caminho de impressão  
 Embora os aplicativos Win32 e .NET Framework suportem os aplicativos XPS, os aplicativos Win32 e Windows Forms usam uma conversão GDI para XPS para criar conteúdo formatado XPS para o driver de impressora XPS (XPSDrv). Esses aplicativos não são necessários para usar o caminho de impressão XPS e podem continuar a usar impressão baseada em Emf (Enhanced Metafile). No entanto, a maioria dos recursos e aprimoramentos do XPS só estão disponíveis para aplicativos que visam o caminho de impressão XPS.  
  
 Para habilitar o uso de impressoras baseadas em XPSDrv por aplicativos Win32 e Windows Forms, o driver de impressora XPS (XPSDrv) suporta a conversão de GDI para formato XPS. O modelo XPSDrv também fornece um conversor para o formato XPS para GDI para que os aplicativos Win32 possam imprimir documentos XPS. Para aplicações WPF, a conversão do formato XPS para <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> GDI é <xref:System.Windows.Xps.XpsDocumentWriter> feita automaticamente pelos métodos e métodos da classe sempre que a fila de impressão de destino da operação de gravação não tiver um driver XPSDrv. (Os aplicativos do Windows Forms não podem imprimir documentos XPS.)  
  
 A ilustração a seguir mostra o subsistema de impressão e define as porções fornecidas pela Microsoft e as partes definidas pelos fornecedores de software e hardware:  
  
 ![A captura de tela mostra o sistema de impressão XPS.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Impressão XPS básica  
 O WPF define uma API básica e avançada. Para aqueles aplicativos que não requerem ampla personalização de impressão ou acesso ao conjunto completo de recursos XPS, o suporte básico de impressão está disponível. O suporte básico de impressão é exposto por meio de um controle de caixa de diálogo de impressão que exige configuração mínima e apresenta uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] familiar. Muitos recursos XPS estão disponíveis usando este modelo de impressão simplificado.  
  
#### <a name="printdialog"></a>PrintDialog  
 O <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> controle fornece um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]único ponto de entrada para, configuração e envio de trabalho XPS. Para obter informações sobre como criar uma instância e usar o controle, consulte [Invocar uma caixa de diálogo de impressão](how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Impressão XPS avançada  
 Para acessar o conjunto completo de recursos XPS, a API de impressão avançada deve ser usada. Várias API relevantes são descritas em maior detalhe abaixo. Para obter uma lista completa de APIs <xref:System.Windows.Xps> <xref:System.Printing> de caminho de impressão XPS, consulte as referências e namespace.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket e PrintCapabilities  
 As <xref:System.Printing.PrintTicket> <xref:System.Printing.PrintCapabilities> aulas são a base dos recursos avançados do XPS. Ambos os tipos de objetos são estruturas formatados xml de características orientadas à impressão, como colagem, impressão de dois lados, grampeamento, etc. Essas estruturas são definidas pelo esquema de impressão. A <xref:System.Printing.PrintTicket> instrui uma impressora como processar um trabalho de impressão. A <xref:System.Printing.PrintCapabilities> classe define as capacidades de uma impressora. Ao consultar os recursos de uma <xref:System.Printing.PrintTicket> impressora, pode ser criada uma que aproveita ao máximo os recursos suportados por uma impressora. Da mesma forma, os recursos sem suporte podem ser evitados.  
  
 O exemplo a seguir demonstra <xref:System.Printing.PrintCapabilities> como consultar a <xref:System.Printing.PrintTicket> impressora e criar um código de uso.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer e PrintQueue  
 A <xref:System.Printing.PrintServer> classe representa um servidor <xref:System.Printing.PrintQueue> de impressão de rede e a classe representa uma impressora e a fila de trabalho de saída associada a ele. Juntas, essas APIs permitem o gerenciamento avançado dos trabalhos de impressão de um servidor. A <xref:System.Printing.PrintServer>, ou uma de suas classes derivadas, é usado para gerenciar um <xref:System.Printing.PrintQueue>. O <xref:System.Printing.PrintQueue.AddJob%2A> método é usado para inserir um novo trabalho de impressão na fila.  
  
 O exemplo a seguir <xref:System.Printing.LocalPrintServer> demonstra como <xref:System.Printing.PrintQueue> criar um e acessar seu padrão usando código.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 Um <xref:System.Windows.Xps.XpsDocumentWriter>, com <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> seus <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> muitos métodos e métodos, <xref:System.Printing.PrintQueue>é usado para escrever documentos XPS para um . Por exemplo, <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> o método é usado para <xref:System.Printing.PrintTicket> produzir um documento XPS e sincronizadamente. O <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> método é usado para produzir <xref:System.Printing.PrintTicket> um documento XPS e assíncronamente.  
  
 O exemplo a seguir <xref:System.Windows.Xps.XpsDocumentWriter> demonstra como criar um código de uso.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 Os <xref:System.Printing.PrintQueue.AddJob%2A> métodos também fornecem formas de imprimir. Consulte [Imprimir arquivos XPS de forma programática](how-to-programmatically-print-xps-files.md). para obter detalhes.  
  
<a name="GDI_Print_Path_intro"></a>
## <a name="gdi-print-path"></a>Caminho de impressão GDI  
 Embora os aplicativos WPF suportem nativamente o caminho de impressão XPS, os aplicativos Win32 e Windows Forms também podem tirar proveito de alguns recursos do XPS. O driver de impressora XPS (XPSDrv) pode converter a saída baseada em GDI para o formato XPS. Para cenários avançados, a conversão personalizada de conteúdo é suportada usando o [Microsoft XPS Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-). Da mesma forma, os aplicativos WPF também podem sair para <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> o caminho <xref:System.Windows.Xps.XpsDocumentWriter> de impressão GDI chamando um dos ou métodos da classe e designando uma impressora não-XpsDrv como a fila de impressão de destino.  

Para aplicativos que não requerem funcionalidade ou suporte xps, o caminho de impressão GDI atual permanece inalterado.  
  
- Para obter material de referência adicional sobre o caminho de impressão GDI e as várias opções de conversão XPS, consulte [Microsoft XPS Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) e [XPSDrv Printer Drivers](/windows-hardware/drivers/print/xpsdrv-printer-drivers).  
  
<a name="XPS_Driver_Model_intro"></a>
## <a name="xpsdrv-driver-model"></a>Modelo de driver XPSDrv  
 O caminho de impressão XPS melhora a eficiência do spooler usando o XPS como o formato nativo do carretel de impressão ao imprimir em uma impressora ou driver habilitado para XPS. O processo de spooling simplificado elimina a necessidade de gerar um arquivo de bobina intermediário, como um arquivo de dados EMF, antes que o documento seja bobinado. Através de tamanhos menores de arquivos de bobina, o caminho de impressão XPS pode reduzir o tráfego de rede e melhorar o desempenho de impressão.  
  
 Emf é um formato fechado que representa a saída de aplicativos como uma série de chamadas para o GDI para prestação de serviços. Ao contrário do EMF, o formato de carretel XPS representa o documento real sem exigir mais interpretação quando da saída para um driver de impressora baseado em XPS (XPSDrv). Os drivers podem operar diretamente nos dados no formato. Esse recurso elimina as conversões de espaço de dados e cores necessárias quando você usa arquivos EMF e drivers de impressão baseados em GDI.  
  
 Os tamanhos dos arquivos de spool geralmente são reduzidos quando você usa documentos XPS que visam um driver de impressora XPS (XPSDrv) em comparação com seus equivalentes EMF; no entanto, há exceções:  
  
- Um gráfico vetorial que é muito complexo, multi-camadas ou que foi escrito de forma ineficiente, pode ser maior que uma versão em bitmap do mesmo elemento gráfico.  
  
- Para fins de exibição em tela, os arquivos XPS inserem fontes de dispositivo, bem como fontes baseadas em computador, enquanto que arquivos de spool GDI não inserem fontes de dispositivo. Mas os dois tipos de fontes são subdivididas (veja abaixo) e os drivers de impressora podem remover as fontes de dispositivo antes de transmitir o arquivo para a impressora.  
  
 A redução de tamanho do spool é executada através de vários mecanismos:  
  
- **Subdivisão de fonte**. Apenas os caracteres usados no documento real são armazenados no arquivo XPS.  
  
- **Suporte avançado a elementos gráficos**. O suporte nativo à transparência e aos primitivos gradientes evita a rasterização de conteúdo no Documento XPS.  
  
- **Identificação de recursos comuns**. Os recursos que são usados várias vezes (como uma imagem que representa um logotipo corporativo) são tratados como recursos compartilhados e são carregados apenas uma vez.  
  
- **Compactação ZIP**. Todos os documentos XPS usam compactação ZIP.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.PrintDialog>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.PrintQueue>
- [Tópicos de como fazer](printing-how-to-topics.md)
- [Documentos no WPF](documents-in-wpf.md)
- [Documentos XPS](/windows/desktop/printdocs/documents)
- [Serialização e armazenamento de documentos](document-serialization-and-storage.md)
- [Conversor de documentos Microsoft XPS (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
