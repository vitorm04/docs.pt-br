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
ms.openlocfilehash: 2090c58369ed3c7bda5df1342291001d9550d48d
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610465"
---
# <a name="printing-overview"></a>Visão geral da impressão
Com o Microsoft .NET Framework, os desenvolvedores de aplicativos usando o Windows Presentation Foundation (WPF) têm um novo conjunto avançado de impressão e imprimir as APIs de gerenciamento do sistema. Com o [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], alguns desses aprimoramentos do sistema de impressão também estão disponíveis para os desenvolvedores que criam aplicativos do [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e desenvolvedores que usam código não gerenciado. No núcleo dessa nova funcionalidade está o novo formato de arquivo [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] e o caminho de impressão [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  
  
 Este tópico contém as seções a seguir.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>Sobre XPS  
 XPS é um formato de documento eletrônico, um formato de arquivo de spool e uma linguagem de descrição de página. É um formato de documento aberto que usa [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)], [!INCLUDE[TLA#tla_opc](../../../../includes/tlasharptla-opc-md.md)] e outros padrões do setor para criar documentos multiplataforma. XPS simplifica o processo pelo qual documentos digitais são criados, compartilhados, impressos, exibidos e arquivados. Para obter informações adicionais sobre XPS, consulte [documentos XPS](/windows/desktop/printdocs/documents).  
  
 Várias técnicas para impressão XPS com base no conteúdo usando [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] são demonstradas [programaticamente imprimir arquivos XPS de](how-to-programmatically-print-xps-files.md). Talvez seja útil consultar esses exemplos durante o exame do conteúdo contido neste tópico. (Os desenvolvedores de código não gerenciado devem consultar a documentação para o [função MXDC_ESCAPE](/windows/desktop/printdocs/mxdc-escape). Os desenvolvedores de formulários do Windows devem usar a API do <xref:System.Drawing.Printing> namespace que não oferece suporte completo [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] caminho de impressão, mas dá suporte a um caminho de impressão híbrido de GDI para XPS. Consulte **Arquitetura de caminho de impressão** abaixo).  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>Caminho de impressão XPS  
 O caminho de impressão de XML Paper Specification (XPS) é um novo [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] recurso que redefine como a impressão é tratada em aplicativos do Windows. Porque [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] pode substituir uma linguagem de apresentação do documento (como RTF), um formato de spooler de impressão (como WMF) e uma linguagem de descrição de página (como PCL ou Postscript); o novo caminho de impressão mantém o formato XPS da publicação do aplicativo para o processamento final no driver de impressão ou dispositivo.  
  
 O caminho de impressão XPS é compilado em cima do modelo de driver a XPS impressora (XPSDrv), que oferece vários benefícios para os desenvolvedores, como [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] impressão, melhor suporte a cores e melhoria significativa do desempenho de impressão. (Para obter mais informações sobre XPSDrv, consulte o [documentação do Windows Driver Kit](/windows-hardware/drivers/).)  
  
 A operação do spooler de impressão para documentos XPS é essencialmente o mesmo nas versões anteriores do Windows. No entanto, ele foi aprimorado para dar suporte o caminho de impressão XPS além existente [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] caminho de impressão. O novo caminho de impressão consome nativamente um arquivo de spool XPS. Embora os drivers de impressora do modo de usuário desenvolvidos para versões anteriores do [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] continuarão a funcionar, um driver de impressora do XPS (XPSDrv) é necessário para usar o caminho de impressão XPS.  
  
 Os benefícios do caminho de impressão XPS são significativos e incluem:  
  
- Suporte à impressão [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)]  
  
- Suporte nativo a perfis de cores avançados, que incluem 32 bits por canal (bpc), CMYK, cores nomeadas, n-inks e suporte nativo à transparência e gradientes.  
  
- Desempenho aprimorado de impressão para o .NET Framework e [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] com base em aplicativos.  
  
- Formato XPS padrão da indústria.  
  
 Para cenários de impressão básicos, uma API simple e intuitiva está disponível com um único ponto de entrada para envio de trabalho, a configuração e a interface do usuário. Para cenários avançados, foi adicionado um suporte extra para a personalização de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] (ou mesmo para nenhuma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]), para a impressão síncrona ou assíncrona e recursos de impressão de lote. As duas opções fornecem suporte de impressão no modo de confiança total ou parcial.  
  
 XPS foi projetado tendo em mente sua extensibilidade. Usando a estrutura de extensibilidade, recursos e capacidades podem ser adicionadas ao XPS de forma modular. Os recursos de extensibilidade incluem:  
  
- Esquema de Impressão. O esquema público é atualizado regularmente e permite a rápida extensão de recursos do dispositivo. (Consulte **PrintTicket e PrintCapabilities** abaixo).  
  
- Pipeline de filtro extensível. O pipeline de filtro XPS (XPSDrv) do driver de impressora foi projetado para habilitar a impressão direta e escalável de documentos XPS. Para obter mais informações, consulte [Drivers de impressora XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers). 
  
### <a name="print-path-architecture"></a>Arquitetura de caminho de impressão  
 Quando ambos os [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e XPS, dar suporte a aplicativos do .NET Framework [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e aplicativos de formulários do Windows usar um [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] para XPS conversão para criar XPS formatado conteúdo para o driver de impressora do XPS (XPSDrv). Esses aplicativos não são necessárias para usar o caminho de impressão XPS e pode continuar a usar [!INCLUDE[TLA#tla_emf](../../../../includes/tlasharptla-emf-md.md)] com base em impressão. No entanto, a maioria dos recursos XPS e aprimoramentos só estão disponíveis para aplicativos voltados para o caminho de impressão XPS.  
  
 Para habilitar o uso de impressoras baseadas em XPSDrv por [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e aplicativos do Windows Forms, o driver de impressora do XPS (XPSDrv) dá suporte à conversão de [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] para XPS formato. O modelo do XPSDrv também fornece um conversor para XPS para [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] formato, de modo que [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplicativos podem imprimir [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] documentos. Para [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos, a conversão de XPS para [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] formato é feito automaticamente pelo <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> e <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> métodos do <xref:System.Windows.Xps.XpsDocumentWriter> classe sempre que a fila de impressão de destino da operação de gravação não tem um driver XPSDrv. (Aplicativos Windows Forms não é possível imprimir [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] documentos.)  
  
 A ilustração a seguir ilustra o subsistema de impressão e define as partes fornecidas pela [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]e as partes definidas por fornecedores de hardware e software:  
  
 ![Captura de tela mostra que o sistema de impressão XPS.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Impressão XPS básica  
 O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] define tanto uma [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] básica quanto avançada. Para os aplicativos que não exigem ampla personalização de impressa ou o acesso ao recurso completo XPS básico, definido suporte de impressão está disponível. O suporte básico de impressão é exposto por meio de um controle de caixa de diálogo de impressão que exige configuração mínima e apresenta uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] familiar. Muitos recursos XPS estão disponíveis usando este modelo de impressão simplificado.  
  
#### <a name="printdialog"></a>PrintDialog  
 O <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> controle fornece um único ponto de entrada para [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuração e envio do trabalho XPS. Para obter informações sobre como criar uma instância e usar o controle, consulte [Invocar uma caixa de diálogo de impressão](how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Impressão XPS avançada  
 Para acessar o conjunto completo de recursos do XPS, a API de impressa avançada deve ser usada. Vários API relevantes são descritas mais detalhadamente abaixo. Caminho de impressão para uma lista completa de XPS [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], consulte o <xref:System.Windows.Xps> e <xref:System.Printing> referências de namespace.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket e PrintCapabilities  
 O <xref:System.Printing.PrintTicket> e <xref:System.Printing.PrintCapabilities> classes são a base dos recursos avançados de XPS. Os dois tipos de objetos são estruturas formatadas [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] de recursos orientados a impressão, como ordenações, impressão de dois lados, grampeamento, etc. Essas estruturas são definidas pelo esquema de impressão. Um <xref:System.Printing.PrintTicket> instrui uma impressora sobre como processar um trabalho de impressão. O <xref:System.Printing.PrintCapabilities> classe define os recursos de uma impressora. Ao consultar os recursos de uma impressora, um <xref:System.Printing.PrintTicket> podem ser criados que tira total proveito de uma impressora recursos suportados. Da mesma forma, os recursos sem suporte podem ser evitados.  
  
 O exemplo a seguir demonstra como consultar o <xref:System.Printing.PrintCapabilities> de uma impressora e criar um <xref:System.Printing.PrintTicket> usando código.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer e PrintQueue  
 O <xref:System.Printing.PrintServer> classe representa um servidor de impressão de rede e o <xref:System.Printing.PrintQueue> classe representa uma impressora e a fila de trabalho de saída associados a ele. Juntas, essas [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] permitem o gerenciamento avançado dos trabalhos de impressão de um servidor. Um <xref:System.Printing.PrintServer>, ou uma de suas classes derivadas, é usado para gerenciar um <xref:System.Printing.PrintQueue>. O <xref:System.Printing.PrintQueue.AddJob%2A> método é usado para inserir um novo trabalho de impressão na fila.  
  
 O exemplo a seguir demonstra como criar uma <xref:System.Printing.LocalPrintServer> e acessar seu padrão <xref:System.Printing.PrintQueue> por meio de código.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 Uma <xref:System.Windows.Xps.XpsDocumentWriter>, com seus diversos a <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> e <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> métodos, é usado para gravar documentos XPS para um <xref:System.Printing.PrintQueue>. Por exemplo, o <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> método é usado para produzir um documento XPS e <xref:System.Printing.PrintTicket> forma síncrona. O <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> método é usado para produzir um documento XPS e <xref:System.Printing.PrintTicket> assincronamente.  
  
 O exemplo a seguir demonstra como criar um <xref:System.Windows.Xps.XpsDocumentWriter> usando código.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 O <xref:System.Printing.PrintQueue.AddJob%2A> métodos também fornecem maneiras de imprimir. Consulte [Imprimir arquivos XPS de forma programática](how-to-programmatically-print-xps-files.md). para obter detalhes.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>Caminho de impressão GDI  
 Embora [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos suportam nativamente o caminho de impressão XPS, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] e aplicativos de formulários do Windows também podem tirar proveito de alguns recursos XPS. O driver de impressora do XPS (XPSDrv) pode converter [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] com base em saída para o formato XPS. Para cenários avançados, há suporte para conversão personalizada de conteúdo usando o [conversor de documento de XPS da Microsoft (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-). Da mesma forma, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativos também podem ser importados para o [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] caminho de impressão chamando um dos <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ou <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> métodos do <xref:System.Windows.Xps.XpsDocumentWriter> classe e designando uma impressora não XpsDrv como o destino de fila de impressão.  

Para aplicativos que não exigem a funcionalidade da XPS ou suporte, atual [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] caminho de impressão permanece inalterado.  
  
- Para material de referência adicional sobre o [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] imprimir o caminho e as várias opções de conversão de XPS, consulte [Microsoft XPS documento conversor (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) e [Drivers de impressora XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>Modelo de driver XPSDrv  
 O caminho de impressão XPS melhora a eficiência do spooler usando XPS como o formato de spool de impressão nativo ao imprimir para um XPS-impressora ou driver habilitados. O processo simplificado de spool elimina a necessidade de gerar um arquivo de spool intermediário, como um arquivo de dados [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)], antes que o documento seja colocado no spool. Por meio de um arquivo de spool menores, o caminho de impressão XPS pode reduzir o tráfego de rede e melhorar o desempenho de impressão.  
  
 O [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] é um formato fechado que representa a saída do aplicativo como uma série de chamadas no [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] para serviços de renderização. Ao contrário de [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)], o formato de spool XPS representa o documento real sem exigir mais interpretação quando enviado a um driver de impressora baseada em XPS (XPSDrv). Os drivers podem operar diretamente nos dados no formato. Essa funcionalidade elimina as conversões de espaço de cores e de dados, necessárias quando você usa arquivos [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] e drivers de impressão com base em [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)].  
  
 Arquivo de spool é geralmente reduzidos quando você usa documentos XPS que se destinam a um driver de impressora do XPS (XPSDrv) em comparação com seus [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] equivalentes; no entanto, há exceções:  
  
- Um gráfico vetorial que é muito complexo, multi-camadas ou que foi escrito de forma ineficiente, pode ser maior que uma versão em bitmap do mesmo elemento gráfico.  
  
- Para fins de exibição em tela, os arquivos XPS inserem fontes de dispositivo, bem como fontes baseadas em computador, enquanto que arquivos de spool GDI não inserem fontes de dispositivo. Mas os dois tipos de fontes são subdivididas (veja abaixo) e os drivers de impressora podem remover as fontes de dispositivo antes de transmitir o arquivo para a impressora.  
  
 A redução de tamanho do spool é executada através de vários mecanismos:  
  
- **Subdivisão de fonte**. Somente os caracteres usados dentro do documento real são armazenados no arquivo XPS.  
  
- **Suporte avançado a elementos gráficos**. O suporte nativo às primitivas de transparência e de gradiente evita a rasterização de conteúdo no documento [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  
  
- **Identificação de recursos comuns**. Os recursos que são usados várias vezes (como uma imagem que representa um logotipo corporativo) são tratados como recursos compartilhados e são carregados apenas uma vez.  
  
- **Compactação ZIP**. Todos os documentos XPS usam a compactação ZIP.  
  
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
- [Microsoft XPS Document conversor (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
