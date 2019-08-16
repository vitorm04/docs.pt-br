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
ms.openlocfilehash: be82b64581ee178b463950d4b8cdae1f98949161
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545309"
---
# <a name="printing-overview"></a>Visão geral da impressão
Com o Microsoft .NET Framework, os desenvolvedores de aplicativos que usam o Windows Presentation Foundation (WPF) têm um novo conjunto avançado de APIs de gerenciamento do sistema de impressão e impressão. Com o [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], alguns desses aprimoramentos do sistema de impressão também estão disponíveis para os desenvolvedores que criam aplicativos do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e desenvolvedores que usam código não gerenciado. No núcleo dessa nova funcionalidade está o novo formato de arquivo [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] e o caminho de impressão [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  
  
 Este tópico contém as seções a seguir.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>Sobre XPS  
 XPS é um formato de documento eletrônico, um formato de arquivo de spool e uma linguagem de descrição de página. É um formato de documento aberto que usa [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]o, o OPC (Open Packaging Conventions) e outros padrões do setor para criar documentos de plataforma cruzada. O XPS simplifica o processo pelo qual documentos digitais são criados, compartilhados, impressos, exibidos e arquivados. Para obter informações adicionais sobre o XPS, consulte [XPS Documents](/windows/desktop/printdocs/documents).  
  
 Várias técnicas para imprimir conteúdo baseado em XPS usando [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] o são demonstradas em [arquivos XPS de impressão](how-to-programmatically-print-xps-files.md)programaticamente. Talvez seja útil consultar esses exemplos durante o exame do conteúdo contido neste tópico. (Os desenvolvedores de código não gerenciado devem ver a documentação para a [função MXDC_ESCAPE](/windows/desktop/printdocs/mxdc-escape). Windows Forms os desenvolvedores devem usar a API no <xref:System.Drawing.Printing> namespace que não dá suporte ao caminho [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] de impressão completo, mas dá suporte a um caminho de impressão híbrido-para-XPS híbrida. Consulte **Arquitetura de caminho de impressão** abaixo).  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>Caminho de impressão XPS  
 O caminho de impressão do XML Paper Specification (XPS) é [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] um novo recurso que redefine como a impressão é tratada em aplicativos do Windows. Como [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] o pode substituir uma linguagem de apresentação de documento (como RTF), um formato de spooler de impressão (como WMF) e uma linguagem de descrição de página (como PCL ou PostScript); o novo caminho de impressão mantém o formato XPS da publicação do aplicativo para o processamento final no driver ou dispositivo de impressão.  
  
 O caminho de impressão XPS é criado sobre o modelo de driver de impressora XPS (XPSDrv), que fornece vários benefícios para [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] os desenvolvedores, como impressão, suporte a cores aprimorados e desempenho de impressão aprimorado significativamente. (Para obter mais informações sobre XPSDrv, consulte a [documentação do kit de driver do Windows](/windows-hardware/drivers/).)  
  
 A operação do spooler de impressão para documentos XPS é essencialmente a mesma das versões anteriores do Windows. No entanto, ele foi aprimorado para dar suporte ao caminho de impressão XPS além do caminho de impressão GDI existente. O novo caminho de impressão consome nativamente um arquivo de spool XPS. Embora os drivers de impressora de modo de usuário escritos para [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] versões anteriores do continuem a funcionar, um driver de impressora XPS (XPSDrv) é necessário para usar o caminho de impressão XPS.  
  
 Os benefícios do caminho de impressão XPS são significativos e incluem:  
  
- Suporte à impressão [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)]  
  
- Suporte nativo a perfis de cores avançados, que incluem 32 bits por canal (bpc), CMYK, cores nomeadas, n-inks e suporte nativo à transparência e gradientes.  
  
- Melhor desempenho de impressão para aplicativos .NET Framework [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] e baseados em.  
  
- Formato XPS padrão do setor.  
  
 Para cenários de impressão básicos, uma API simples e intuitiva está disponível com um único ponto de entrada para a interface do usuário, configuração e envio de trabalhos. Para cenários avançados, foi adicionado um suporte extra para a personalização de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] (ou mesmo para nenhuma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]), para a impressão síncrona ou assíncrona e recursos de impressão de lote. As duas opções fornecem suporte de impressão no modo de confiança total ou parcial.  
  
 O XPS foi projetado tendo em mente a extensibilidade. Usando a estrutura de extensibilidade, recursos e funcionalidades podem ser adicionados ao XPS de maneira modular. Os recursos de extensibilidade incluem:  
  
- Esquema de Impressão. O esquema público é atualizado regularmente e permite a rápida extensão de recursos do dispositivo. (Consulte **PrintTicket e PrintCapabilities** abaixo).  
  
- Pipeline de filtro extensível. O pipeline de filtro do driver de impressora XPS (XPSDrv) foi projetado para permitir a impressão direta e escalonável de documentos XPS. Para obter mais informações, consulte [XPSDrv Printer drivers](/windows-hardware/drivers/print/xpsdrv-printer-drivers). 
  
### <a name="print-path-architecture"></a>Arquitetura de caminho de impressão  
 Embora o [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e o .NET Framework aplicativos ofereçam [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] suporte a XPS e Windows Forms aplicativos usam uma conversão de GDI para XPS a fim de criar conteúdo formatado em XPS para o driver de impressora XPS (XPSDrv). Esses aplicativos não são obrigados a usar o caminho de impressão XPS e podem continuar a usar a impressão baseada em metarquivos avançados (EMF). No entanto, a maioria dos recursos e aprimoramentos do XPS só está disponível para aplicativos direcionados ao caminho de impressão XPS.  
  
 Para habilitar o uso de impressoras baseadas em XPSDrv por [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e Windows Forms aplicativos, o driver de impressora XPS (XPSDrv) dá suporte à conversão do formato GDI para XPS. O modelo XPSDrv também fornece um conversor para o formato XPS para GDI para [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] que os aplicativos [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] possam imprimir documentos. Para [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos, a <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> conversão do formato XPS para GDI é feita automaticamente pelos métodos <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> e da <xref:System.Windows.Xps.XpsDocumentWriter> classe sempre que a fila de impressão de destino da operação de gravação não tiver um driver XPSDrv. (Windows Forms aplicativos não podem [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] imprimir documentos.)  
  
 A ilustração a seguir descreve o subsistema de impressão e define as partes fornecidas [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]pelo e as partes definidas por fornecedores de software e hardware:  
  
 ![Captura de tela mostra o sistema de impressão XPS.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Impressão XPS básica  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]define uma API básica e avançada. Para os aplicativos que não exigem ampla personalização de impressão ou acesso ao conjunto completo de recursos XPS, o suporte a impressão básica está disponível. O suporte básico de impressão é exposto por meio de um controle de caixa de diálogo de impressão que exige configuração mínima e apresenta uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] familiar. Muitos recursos do XPS estão disponíveis usando esse modelo de impressão simplificado.  
  
#### <a name="printdialog"></a>PrintDialog  
 O <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> controle fornece um único ponto de entrada [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]para o, configuração e envio de trabalho XPS. Para obter informações sobre como criar uma instância e usar o controle, consulte [Invocar uma caixa de diálogo de impressão](how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Impressão XPS avançada  
 Para acessar o conjunto completo de recursos do XPS, a API de impressão avançada deve ser usada. Várias APIs relevantes são descritas mais detalhadamente abaixo. Para obter uma lista completa de APIs de caminho de impressão XPS <xref:System.Windows.Xps> , <xref:System.Printing> consulte as referências de namespace e.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket e PrintCapabilities  
 As <xref:System.Printing.PrintTicket> classes <xref:System.Printing.PrintCapabilities> e são a base dos recursos XPS avançados. Os dois tipos de objetos são estruturas formatadas [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] de recursos orientados a impressão, como ordenações, impressão de dois lados, grampeamento, etc. Essas estruturas são definidas pelo esquema de impressão. Um <xref:System.Printing.PrintTicket> instrui uma impressora a processar um trabalho de impressão. A <xref:System.Printing.PrintCapabilities> classe define os recursos de uma impressora. Ao consultar os recursos de uma impressora, é possível <xref:System.Printing.PrintTicket> criar um que aproveita totalmente os recursos com suporte de uma impressora. Da mesma forma, os recursos sem suporte podem ser evitados.  
  
 O exemplo a seguir demonstra como consultar o <xref:System.Printing.PrintCapabilities> de uma impressora e criar um <xref:System.Printing.PrintTicket> usando código.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer e PrintQueue  
 A <xref:System.Printing.PrintServer> classe representa um servidor de impressão de rede <xref:System.Printing.PrintQueue> e a classe representa uma impressora e a fila de trabalhos de saída associada a ela. Juntas, essas APIs permitem o gerenciamento avançado de trabalhos de impressão de um servidor. Uma <xref:System.Printing.PrintServer>, ou uma de suas classes derivadas, é usada para gerenciar um <xref:System.Printing.PrintQueue>. O <xref:System.Printing.PrintQueue.AddJob%2A> método é usado para inserir um novo trabalho de impressão na fila.  
  
 O exemplo a seguir demonstra como criar um <xref:System.Printing.LocalPrintServer> e acessar seu padrão <xref:System.Printing.PrintQueue> usando código.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 Um <xref:System.Windows.Xps.XpsDocumentWriter>, com seus <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> muitos métodos e <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> , é usado para gravar documentos XPS em um <xref:System.Printing.PrintQueue>. Por exemplo, o <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> método é usado para gerar um documento XPS e <xref:System.Printing.PrintTicket> de forma síncrona. O <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> método é usado para gerar um documento XPS e <xref:System.Printing.PrintTicket> assincronamente.  
  
 O exemplo a seguir demonstra como criar um <xref:System.Windows.Xps.XpsDocumentWriter> código de uso.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 Os <xref:System.Printing.PrintQueue.AddJob%2A> métodos também fornecem maneiras de imprimir. Consulte [Imprimir arquivos XPS de forma programática](how-to-programmatically-print-xps-files.md). para obter detalhes.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>Caminho de impressão GDI  
 Embora [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] os aplicativos ofereçam suporte nativo ao caminho de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] impressão XPS, e os aplicativos Windows Forms também podem aproveitar alguns recursos do XPS. O driver de impressora XPS (XPSDrv) pode converter a saída baseada em GDI para o formato XPS. Para cenários avançados, há suporte para a conversão personalizada de conteúdo usando o [Microsoft XPS Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-). Da mesma [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] forma, os aplicativos também podem gerar saída para o caminho de impressão GDI <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> chamando <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> um dos métodos <xref:System.Windows.Xps.XpsDocumentWriter> ou da classe e designando uma impressora não XPSDrv como a fila de impressão de destino.  

Para aplicativos que não exigem suporte ou funcionalidade XPS, o caminho de impressão GDI atual permanece inalterado.  
  
- Para obter material de referência adicional sobre o caminho de impressão GDI e as várias opções de conversão de XPS, consulte [Microsoft XPS Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) e [drivers de impressora XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>Modelo de driver XPSDrv  
 O caminho de impressão XPS melhora a eficiência do spooler usando XPS como o formato de spool de impressão nativo ao imprimir em uma impressora ou driver habilitado para XPS. O processo de spool simplificado elimina a necessidade de gerar um arquivo de spool intermediário, como um arquivo de dados EMF, antes de o documento ser colocado em spool. Por meio de tamanhos de arquivo de spool menores, o caminho de impressão XPS pode reduzir o tráfego de rede e melhorar o desempenho de impressão.  
  
 EMF é um formato fechado que representa a saída do aplicativo como uma série de chamadas em GDI para serviços de renderização. Diferentemente do EMF, o formato de spool XPS representa o documento real sem a necessidade de mais interpretação quando a saída para um driver de impressora baseado em XPS (XPSDrv). Os drivers podem operar diretamente nos dados no formato. Esse recurso elimina as conversões de dados e de espaço de cores necessárias ao usar arquivos EMF e drivers de impressão baseados em GDI.  
  
 Os tamanhos de arquivo de spool geralmente são reduzidos quando você usa documentos XPS destinados a um driver de impressora XPS (XPSDrv) em comparação com seus equivalentes EMF; no entanto, há exceções:  
  
- Um gráfico vetorial que é muito complexo, multi-camadas ou que foi escrito de forma ineficiente, pode ser maior que uma versão em bitmap do mesmo elemento gráfico.  
  
- Para fins de exibição em tela, os arquivos XPS inserem fontes de dispositivo, bem como fontes baseadas em computador, enquanto que arquivos de spool GDI não inserem fontes de dispositivo. Mas os dois tipos de fontes são subdivididas (veja abaixo) e os drivers de impressora podem remover as fontes de dispositivo antes de transmitir o arquivo para a impressora.  
  
 A redução de tamanho do spool é executada através de vários mecanismos:  
  
- **Subdivisão de fonte**. Somente os caracteres usados no documento real são armazenados no arquivo XPS.  
  
- **Suporte avançado a elementos gráficos**. O suporte nativo às primitivas de transparência e de gradiente evita a rasterização de conteúdo no documento [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  
  
- **Identificação de recursos comuns**. Os recursos que são usados várias vezes (como uma imagem que representa um logotipo corporativo) são tratados como recursos compartilhados e são carregados apenas uma vez.  
  
- **Compactação ZIP**. Todos os documentos XPS usam compactação ZIP.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.PrintDialog>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.PrintQueue>
- [Tópicos de instruções](printing-how-to-topics.md)
- [Documentos no WPF](documents-in-wpf.md)
- [Documentos XPS](/windows/desktop/printdocs/documents)
- [Serialização e armazenamento de documentos](document-serialization-and-storage.md)
- [Conversor de documento XPS da Microsoft (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
