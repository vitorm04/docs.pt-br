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
ms.openlocfilehash: 04ea64f0e6563012a3b272306df6be4575ed7659
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44066757"
---
# <a name="printing-overview"></a>Visão geral da impressão
Com o Microsoft .NET Framework, os desenvolvedores de aplicativos usando o Windows Presentation Foundation (WPF) têm um novo conjunto avançado de gerenciamento de sistema de impressão e imprimir [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]. Com o [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], alguns desses aprimoramentos do sistema de impressão também estão disponíveis para os desenvolvedores que criam aplicativos do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e desenvolvedores que usam código não gerenciado. No núcleo dessa nova funcionalidade está o novo formato de arquivo [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] e o caminho de impressão [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  
  
 Este tópico contém as seções a seguir.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>Sobre XPS  
 O [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] é um formato de documento eletrônico, um formato de arquivo de spool e uma linguagem de descrição de página. É um formato de documento aberto que usa [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)], [!INCLUDE[TLA#tla_opc](../../../../includes/tlasharptla-opc-md.md)] e outros padrões do setor para criar documentos multiplataforma. O [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] simplifica o processo pelo qual os documentos digitais são criados, compartilhados, impressos, exibidos e arquivados. Para obter informações adicionais sobre [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)], consulte o [Site da Web do XPS](https://www.microsoft.com/xps).  
  
 Várias técnicas para impressão de conteúdo com base em [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] usando o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] são demonstradas em [Imprimir arquivos XPS de forma programática](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md). Talvez seja útil consultar esses exemplos durante o exame do conteúdo contido neste tópico. (Os desenvolvedores de código não gerenciado devem consultar a documentação para o [função MXDC_ESCAPE](https://msdn.microsoft.com/library/windows/desktop/dd162739.aspx). Os desenvolvedores de formulários do Windows devem usar o [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] no <xref:System.Drawing.Printing> namespace que não oferece suporte completo [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] caminho de impressão, mas dá suporte a um caminho de impressão híbrido de GDI para XPS. Consulte **Arquitetura de caminho de impressão** abaixo).  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>Caminho de impressão XPS  
 O [!INCLUDE[TLA#tla_metro](../../../../includes/tlasharptla-metro-md.md)] caminho de impressão é um novo [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] recurso que redefine como a impressão é tratada em aplicativos do Windows. Como o [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] pode substituir uma linguagem de apresentação de documento (como RTF), um formato de spooler de impressão (como WMF) e uma linguagem de descrição de página (como PCL ou Postscript), o novo caminho de impressão mantém o formato [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] da publicação do aplicativo até o processamento final no dispositivo ou no driver de impressão.  
  
 O caminho de impressão do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] é construído com base no modelo de driver de impressora [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] (XPSDrv), que oferece vários benefícios para os desenvolvedores, como impressão [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)], melhor suporte a cores e desempenho de impressão significativamente aprimorado. (Para obter mais informações sobre XPSDrv, consulte o [Kit de desenvolvimento de Driver Windows](https://msdn.microsoft.com/library/windows/hardware/ff557573.aspx)).  
  
 A operação do spooler de impressão para [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] documentos é essencialmente o mesmo nas versões anteriores do Windows. No entanto, ela foi aprimorada para dar suporte ao caminho de impressão do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] além do caminho de impressão [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] existente. O novo caminho de impressão consome nativamente um arquivo de spool [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]. Enquanto os drivers de impressora do modo de usuário desenvolvidos para versões anteriores do [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] continuarão a funcionar, um driver de impressora [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] (XPSDrv) será necessário para usar o caminho de impressão [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)].  
  
 Os benefícios do caminho de impressão [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] são significativos e incluem:  
  
-   Suporte à impressão [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)]  
  
-   Suporte nativo a perfis de cores avançados, que incluem 32 bits por canal (bpc), CMYK, cores nomeadas, n-inks e suporte nativo à transparência e gradientes.  
  
-   Desempenho aprimorado de impressão para o .NET Framework e [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] com base em aplicativos.  
  
-   Formato [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] padrão do setor.  
  
 Para cenários de impressão básicos, uma [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] simples e intuitiva está disponível com um único ponto de entrada para interface do usuário, configuração e envio de trabalho. Para cenários avançados, foi adicionado um suporte extra para a personalização de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] (ou mesmo para nenhuma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]), para a impressão síncrona ou assíncrona e recursos de impressão de lote. As duas opções fornecem suporte de impressão no modo de confiança total ou parcial.  
  
 O [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] foi projetado com a ideia de extensibilidade. Usando a estrutura de extensibilidade, recursos e capacidades podem ser adicionados ao [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] de maneira modular. Os recursos de extensibilidade incluem:  
  
-   Esquema de Impressão. O esquema público é atualizado regularmente e permite a rápida extensão de recursos do dispositivo. (Consulte **PrintTicket e PrintCapabilities** abaixo).  
  
-   Pipeline de filtro extensível. O pipeline de filtro do driver de impressão do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] (XPSDrv) foi projetado para permitir a impressão direta e escalável de documentos [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]. (Pesquise por "XPSDrv" na [Windows Driver Kit](https://msdn.microsoft.com/library/windows/hardware/ff557573.aspx).)  
  
### <a name="print-path-architecture"></a>Arquitetura de caminho de impressão  
 Quando ambos os [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e dar suporte a aplicativos do .NET Framework [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)], [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e usam aplicativos de formulários do Windows uma [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] para [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] conversão para criar [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] conteúdo para o formatado[!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]driver de impressora (XPSDrv). Esses aplicativos não são obrigados a usar o caminho de impressão [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] e podem continuar a usar a impressão baseada em [!INCLUDE[TLA#tla_emf](../../../../includes/tlasharptla-emf-md.md)]. No entanto, a maioria dos recursos e aprimoramentos do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] só estão disponíveis para aplicativos que se destinam ao caminho de impressão [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)].  
  
 Para habilitar o uso de impressoras baseadas em XPSDrv por [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e aplicativos do Windows Forms, o [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] driver de impressora (XPSDrv) dá suporte à conversão de [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] para [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] formato. O modelo do XPSDrv também fornece um conversor de formato [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] em [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] para que aplicativos [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] possam imprimir documentos [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]. Para [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos, a conversão de [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ao [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] formato é feito automaticamente pelo <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> e <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> métodos do <xref:System.Windows.Xps.XpsDocumentWriter> sempre que a fila de impressão de destino da operação de gravação não tem de classe um driver XPSDrv. (Aplicativos Windows Forms não é possível imprimir [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] documentos.)  
  
 A ilustração a seguir demonstra o subsistema de impressão e define as partes fornecidas pela [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] e as partes definidas por fornecedores de software e hardware.  
  
 ![O sistema de impressão XPS](../../../../docs/framework/wpf/advanced/media/xpsprint.PNG "XPSPrint")  
  
### <a name="basic-xps-printing"></a>Impressão XPS básica  
 O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] define tanto uma [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] básica quanto avançada. Para os aplicativos que não exigem ampla personalização de impressão ou acesso a todo o conjunto de recursos de [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)], o suporte básico de impressão está disponível. O suporte básico de impressão é exposto por meio de um controle de caixa de diálogo de impressão que exige configuração mínima e apresenta uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] familiar. Muitos recursos [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] estão disponíveis por meio desse modelo de impressão simplificado.  
  
#### <a name="printdialog"></a>PrintDialog  
 O <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> controle fornece um único ponto de entrada para [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuração, e [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] envio de trabalho. Para obter informações sobre como criar uma instância e usar o controle, consulte [Invocar uma caixa de diálogo de impressão](../../../../docs/framework/wpf/advanced/how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Impressão XPS avançada  
 Para acessar o conjunto completo de recursos [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)], a [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] de impressão avançada deve ser usada. Várias [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] relevantes são descritas em mais detalhes abaixo. Para obter uma lista completa dos [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] caminho de impressão [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], consulte o <xref:System.Windows.Xps> e <xref:System.Printing> referências de namespace.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket e PrintCapabilities  
 O <xref:System.Printing.PrintTicket> e <xref:System.Printing.PrintCapabilities> classes são a base da avançada [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] recursos. Os dois tipos de objetos são estruturas formatadas [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] de recursos orientados a impressão, como agrupamentos, impressão de dois lados, grampeamento, etc. Essas estruturas são definidas pelo esquema de impressão. Um <xref:System.Printing.PrintTicket> instrui uma impressora sobre como processar um trabalho de impressão. O <xref:System.Printing.PrintCapabilities> classe define os recursos de uma impressora. Ao consultar os recursos de uma impressora, um <xref:System.Printing.PrintTicket> podem ser criados que tira total proveito de uma impressora recursos suportados. Da mesma forma, os recursos sem suporte podem ser evitados.  
  
 O exemplo a seguir demonstra como consultar o <xref:System.Printing.PrintCapabilities> de uma impressora e criar um <xref:System.Printing.PrintTicket> usando código.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](../../../../samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer e PrintQueue  
 O <xref:System.Printing.PrintServer> classe representa um servidor de impressão de rede e o <xref:System.Printing.PrintQueue> classe representa uma impressora e a fila de trabalho de saída associados a ele. Juntas, essas [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] permitem o gerenciamento avançado dos trabalhos de impressão de um servidor. Um <xref:System.Printing.PrintServer>, ou uma de suas classes derivadas, é usado para gerenciar um <xref:System.Printing.PrintQueue>. O <xref:System.Printing.PrintQueue.AddJob%2A> método é usado para inserir um novo trabalho de impressão na fila.  
  
 O exemplo a seguir demonstra como criar uma <xref:System.Printing.LocalPrintServer> e acessar seu padrão <xref:System.Printing.PrintQueue> por meio de código.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 Uma <xref:System.Windows.Xps.XpsDocumentWriter>, com seus diversos a <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> e <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> métodos, é usado para gravar [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] documentos para um <xref:System.Printing.PrintQueue>. Por exemplo, o <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> método é usado para saída de um [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] documento e <xref:System.Printing.PrintTicket> forma síncrona. O <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> método é usado para saída de um [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] documento e <xref:System.Printing.PrintTicket> assincronamente.  
  
 O exemplo a seguir demonstra como criar um <xref:System.Windows.Xps.XpsDocumentWriter> usando código.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 O <xref:System.Printing.PrintQueue.AddJob%2A> métodos também fornecem maneiras de imprimir. Consulte [Imprimir arquivos XPS de forma programática](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md). para obter detalhes.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>Caminho de impressão GDI  
 Enquanto [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos suportam nativamente o [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] caminho de impressão [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e aplicativos de formulários do Windows também podem tirar proveito de alguns [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] recursos. O driver de impressora [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] (XPSDrv) pode converter saída baseada em [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] em formato [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]. Para cenários avançados, há suporte para conversão personalizada de conteúdo usando o [conversor de documento de XPS da Microsoft (MXDC)](https://msdn.microsoft.com/library/windows/desktop/ff686803.aspx). Da mesma forma, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos também podem ser importados para o [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] caminho de impressão chamando um dos <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ou <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> métodos do <xref:System.Windows.Xps.XpsDocumentWriter> classe e designando uma impressora não XpsDrv como o destino de fila de impressão.  

Para aplicativos que não exigem a funcionalidade ou suporte [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)], o caminho de impressão [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] atual permanece inalterado.  
  
-   Para material de referência adicional sobre o [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] imprimir o caminho e as várias [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] opções de conversão, consulte [Microsoft XPS documento conversor (MXDC)](https://msdn.microsoft.com/library/windows/desktop/ff686803.aspx) e "XPSDrv" no [Windows Driver Kit](https://msdn.microsoft.com/library/windows/hardware/ff557573.aspx).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>Modelo de driver XPSDrv  
 O caminho de impressão [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] melhora a eficiência do spooler usando [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] como o formato de spool de impressão nativo ao imprimir em uma impressora ou driver habilitados para [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]. O processo simplificado de spool elimina a necessidade de gerar um arquivo de spool intermediário, como um arquivo de dados [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)], antes que o documento seja colocado no spool. Por meio de arquivos de spool menores, o caminho de impressão [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] pode reduzir o tráfego de rede e melhorar o desempenho de impressão.  
  
 O [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] é um formato fechado que representa a saída do aplicativo como uma série de chamadas no [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] para serviços de renderização. Ao contrário do [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)], o formato de spool [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] representa o documento real sem a exigência de interpretação adicional quando enviado a um driver de impressora baseado em [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] (XPSDrv). Os drivers podem operar diretamente nos dados no formato. Essa funcionalidade elimina as conversões de espaço de cores e de dados, necessárias quando você usa arquivos [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] e drivers de impressão com base em [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)].  
  
 Os tamanhos de arquivo de spool são geralmente reduzidos quando você usa documentos [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] que se destinam a um driver de impressora [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] (XPSDrv) em comparação com seus equivalentes [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)]. No entanto, há exceções:  
  
-   Um gráfico vetorial que é muito complexo, multi-camadas ou que foi escrito de forma ineficiente, pode ser maior que uma versão em bitmap do mesmo elemento gráfico.  
  
-   Para fins de exibição em tela, os arquivos XPS inserem fontes de dispositivo, bem como fontes baseadas em computador, enquanto que arquivos de spool GDI não inserem fontes de dispositivo. Mas os dois tipos de fontes são subdivididas (veja abaixo) e os drivers de impressora podem remover as fontes de dispositivo antes de transmitir o arquivo para a impressora.  
  
 A redução de tamanho do spool é executada através de vários mecanismos:  
  
-   **Subdivisão de fonte**. Somente os caracteres usados dentro do documento real são armazenados no arquivo [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)].  
  
-   **Suporte avançado a elementos gráficos**. O suporte nativo às primitivas de transparência e de gradiente evita a rasterização de conteúdo no documento [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  
  
-   **Identificação de recursos comuns**. Os recursos que são usados várias vezes (como uma imagem que representa um logotipo corporativo) são tratados como recursos compartilhados e são carregados apenas uma vez.  
  
-   **Compactação ZIP**. Todos os documentos [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] usam a compactação ZIP.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.PrintDialog>  
 <xref:System.Windows.Xps.XpsDocumentWriter>  
 <xref:System.Windows.Xps.Packaging.XpsDocument>  
 <xref:System.Printing.PrintTicket>  
 <xref:System.Printing.PrintCapabilities>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.PrintQueue>  
 [Tópicos de instruções](../../../../docs/framework/wpf/advanced/printing-how-to-topics.md)  
 [Documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [XPS](https://www.microsoft.com/xps)  
 [Serialização e armazenamento de documentos](../../../../docs/framework/wpf/advanced/document-serialization-and-storage.md)  
 [Microsoft XPS Document conversor (MXDC)](https://msdn.microsoft.com/library/windows/desktop/ff686803.aspx)
