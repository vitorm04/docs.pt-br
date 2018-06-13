---
title: Documentos no WPF
ms.date: 03/30/2017
helpviewer_keywords:
- documents [WPF], packaging
- documents [WPF], text layout
- documents [WPF], XPS
- 'XPS documents [WPF], , '
- documents [WPF], controls
- documents [WPF], types of
- documents [WPF], browser-viewable
ms.assetid: 6e8db7bc-050a-4070-aa72-bb8c46e87ff8
ms.openlocfilehash: ced65795c66ab7c3b7eb6c25b225ec551c3969ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548425"
---
# <a name="documents-in-wpf"></a>Documentos no WPF
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oferece uma ampla gama de recursos de documento que permitem a criação de conteúdo de alta fidelidade, projetado para ser mais facilmente acessado e lido que nas gerações anteriores do [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]. Além das capacidades e da qualidade aprimoradas, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também oferece serviços integrados para exibição, empacotamento e segurança de documentos. Este tópico fornece uma introdução aos tipos de documento e ao empacotamento de documento do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
  
<a name="types_of_documents"></a>   
## <a name="types-of-documents"></a>Tipos de documentos  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] divide os documentos em duas grandes categorias com base em seu uso pretendido. Essas categorias de documentos são chamadas de "documentos estáticos" e "documentos dinâmicos".  
  
 Os documentos estáticos são destinados para aplicações que exigem uma apresentação [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] precisa, independente do hardware de vídeo ou da impressora usada. Os usos típicos de documentos estáticos incluem a editoração eletrônica, o processamento de texto e o layout de formulário, nos quais a aderência ao design original da página é essencial. Como parte de seu layout, um documento estático mantém o posicionamento preciso dos elementos de conteúdo, independente do dispositivo de impressão ou de exibição em uso. Por exemplo, uma página de documento estático exibida em uma tela de 96 dpi parecerá exatamente a mesma quando enviada a uma impressora a laser de 600 dpi ou quando for enviada para uma fotocompositora de 4800 dpi. O layout da página permanece o mesmo em todos os casos, embora a qualidade do documento seja maximizada para as capacidades de cada dispositivo.  
  
 Em comparação, os documentos dinâmicos são projetados para otimizar a exibição e legibilidade e são melhor utilizados quando a facilidade de leitura é o cenário principal de consumo de documento. Em vez de serem configurados para um layout predefinido, os documentos dinâmicos ajustam e refluem seu conteúdo com base em variáveis de tempo de execução como tamanho da janela, resolução do dispositivo e preferências opcionais do usuário. Uma página da Web é um exemplo simples de um documento dinâmico em que o conteúdo da página é formatado dinamicamente para se ajustar à janela atual. Os documentos dinâmicos otimizam a experiência de visualização e de leitura para o usuário, com base no ambiente de tempo de execução. Por exemplo, o mesmo documento dinâmico será dinamicamente reformatado para legibilidade otimizada em uma tela de alta resolução de 19 polegadas ou uma tela pequena de PDA de 2x3 polegadas. Além disso, os documentos dinâmicos têm vários recursos internos, incluindo pesquisa, modos de exibição que otimizam a legibilidade e a capacidade de alterar o tamanho e a aparência das fontes.  Consulte [Visão geral de documento dinâmico](../../../../docs/framework/wpf/advanced/flow-document-overview.md) para ilustrações, exemplos e informações aprofundadas sobre documentos dinâmicos.  
  
<a name="document_viewer"></a>   
## <a name="document-controls-and-text-layout"></a>Controles de documento e layout de texto  
 O .NET Framework fornece um conjunto de controles pré-compilados que simplificam o uso de documentos fixos, documentos de fluxo e texto geral em seu aplicativo.  Exibição de conteúdo de documento fixo é suportada utilizando o <xref:System.Windows.Controls.DocumentViewer> controle.  Exibição de conteúdo de documento de fluxo é suportada por três controles diferentes: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, e <xref:System.Windows.Controls.FlowDocumentScrollViewer> que mapeiam para diferentes cenários de uso (consulte as seções a seguir).  Outros controles do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornecem layout simplificado para dar suporte a usos de texto geral (consulte [Texto na interface do usuário](#text_in_the_user_interface), abaixo).  
  
### <a name="fixed-document-control---documentviewer"></a>Controle de documento estático – DocumentViewer  
 O <xref:System.Windows.Controls.DocumentViewer> controle é projetado para exibir <xref:System.Windows.Documents.FixedDocument> conteúdo. O <xref:System.Windows.Controls.DocumentViewer> controle fornece uma interface de usuário intuitiva que fornece suporte interno para operações comuns, incluindo a saída de impressão, copiar para área de transferência, zoom e recursos de pesquisa de texto. O controle fornece acesso a páginas de conteúdo por meio de um mecanismo de rolagem familiar. Como todos os [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controles, <xref:System.Windows.Controls.DocumentViewer> suporta estilização completa ou parcial, que permite que o controle seja visualmente integrado em praticamente qualquer aplicativo ou o ambiente.  
  
 <xref:System.Windows.Controls.DocumentViewer> foi projetado para exibir o conteúdo de uma maneira de somente leitura. edição ou modificação de conteúdo não está disponível e não é suportada.  
  
<a name="flow_document"></a>   
### <a name="flow-document-controls"></a>Controles de documento dinâmico  
 **Observação:** para obter informações detalhadas sobre os recursos dos documentos dinâmicos e como criá-los, consulte [Visão geral de documento dinâmico](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
 Exibição de conteúdo de documento de fluxo é suportada por três controles: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, e <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> inclui recursos que permitem ao usuário escolher dinamicamente entre diversos modos de exibição, um página única (uma página no tempo), modo de visualização um duas páginas-em-um-vez (formato de leitura de livro) modo e um modo de exibição (sem parte inferior) de rolagem contínua.  Para obter mais informações sobre esses modos de exibição, consulte <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  Se você não precisa da capacidade dinamicamente alternar entre modos de exibição diferentes, <xref:System.Windows.Controls.FlowDocumentPageViewer> e <xref:System.Windows.Controls.FlowDocumentScrollViewer> oferecem fluxo leves visualizadores de conteúdo que foram corrigidos em um modo de visualização particular.  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer e FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> mostra o conteúdo de página em determinado modo de exibição, enquanto <xref:System.Windows.Controls.FlowDocumentScrollViewer> mostra o conteúdo no modo de rolagem contínua.  Ambos <xref:System.Windows.Controls.FlowDocumentPageViewer> e <xref:System.Windows.Controls.FlowDocumentScrollViewer> são fixos em um modo de visualização particular. Comparar com <xref:System.Windows.Controls.FlowDocumentReader>, que inclui recursos que permitem ao usuário escolher dinamicamente entre diversos modos de visualização (conforme fornecido pelo <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> enumeração), às custas de sendo mais intensivo de <xref:System.Windows.Controls.FlowDocumentPageViewer> ou <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Por padrão, uma barra de rolagem vertical é sempre exibida e uma barra de rolagem horizontal se torna visível se necessário. O padrão [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] para <xref:System.Windows.Controls.FlowDocumentScrollViewer> não inclui uma barra de ferramentas; no entanto, o <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> propriedade pode ser usada para habilitar a barra de ferramentas interna.  
  
<a name="text_in_the_user_interface"></a>   
### <a name="text-in-the-user-interface"></a>Texto na interface do usuário  
 Além de adicionar texto a documentos, o texto também pode ser usado, obviamente, na interface do usuário do aplicativo, como em formulários. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui vários controles para desenhar texto na tela. Cada controle é destinado a um cenário diferente e tem sua própria lista de recursos e limitações. Em geral, o <xref:System.Windows.Controls.TextBlock> elemento deve ser usado ao suporte limitado a texto é necessário, como uma breve frase em um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> pode ser usado quando é necessário suporte mínimo de texto. Para obter mais informações, consulte [Visão geral do TextBlock](../../../../docs/framework/wpf/controls/textblock-overview.md).  
  
<a name="packaging"></a>   
## <a name="document-packaging"></a>Empacotamento de documento  
 O <xref:System.IO.Packaging> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] oferece uma forma eficiente para organizar os dados de aplicativo, o conteúdo do documento e recursos relacionados em um único contêiner que é simples de acessar, portátil e fácil de distribuir. Um arquivo ZIP é um exemplo de um <xref:System.IO.Packaging.Package> tipo capaz de conter vários objetos como uma única unidade. O empacotamento [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] fornecer um padrão <xref:System.IO.Packaging.ZipPackage> implementação criada usando um padrão de Open Packaging Conventions com arquitetura de arquivos XML e ZIP. As [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] de empacotamento do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] simplificam a criação de pacotes e repositório e acesso de objetos dentro deles. Um objeto armazenado em uma <xref:System.IO.Packaging.Package> é conhecido como um <xref:System.IO.Packaging.PackagePart> ("parte"). Os pacotes também podem incluir certificados digitais assinados que podem ser usados para identificar o originador de uma parte e validar que o conteúdo de um pacote não foi modificado.  Pacotes também incluem uma <xref:System.IO.Packaging.PackageRelationship> recurso que permite que informações adicionais a serem adicionados a um pacote ou associada a partes específicas sem modificar de fato o conteúdo de partes existentes.  Os serviços de pacotes também dão suporte ao [!INCLUDE[TLA#tla_rm](../../../../includes/tlasharptla-rm-md.md)].  
  
 A arquitetura de pacote do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] serve como base para várias tecnologias-chave:  
  
-   Conformidade de documentos [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] com o [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)].  
  
-   Formato de documentos Microsoft Office "12" Open XML (.docx).  
  
-   Formatos de armazenamento personalizado para seu próprio projeto de aplicativo.  
  
 Com base em APIs de empacotamento, um <xref:System.Windows.Xps.Packaging.XpsDocument> é projetado especificamente para armazenar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] documentos de conteúdo fixo. Um <xref:System.Windows.Xps.Packaging.XpsDocument> é um documento independente que pode ser aberto em um visualizador, exibido em um <xref:System.Windows.Controls.DocumentViewer> controle, roteada para uma fila de impressão ou saída diretamente para um [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-impressora compatível.  
  
 As seções a seguir fornecem informações adicionais sobre o <xref:System.IO.Packaging.Package> e <xref:System.Windows.Xps.Packaging.XpsDocument> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] fornecido com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="packages"></a>   
### <a name="package-components"></a>Componentes do pacote  
 As APIs de empacotamento do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permitem que os dados de aplicativos e documentos sejam organizados em uma única unidade portátil. Um arquivo ZIP é um dos tipos mais comuns de pacotes e é o tipo de pacote padrão fornecido com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  <xref:System.IO.Packaging.Package> em si é uma classe abstrata da qual <xref:System.IO.Packaging.ZipPackage> é implementado usando uma arquitetura de arquivos XML e ZIP de padrão aberto.  O <xref:System.IO.Packaging.Package.Open%2A> método usa <xref:System.IO.Packaging.ZipPackage> para criar e usar arquivos ZIP por padrão. Um pacote pode conter três tipos básicos de itens:  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Conteúdo, dados, documentos e arquivos de recurso do aplicativo.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|[Certificado X.509] para identificação, autenticação e validação.|  
|<xref:System.IO.Packaging.PackageRelationship>|Informações adicionadas relacionadas ao pacote ou a uma parte específica.|  
  
<a name="PackageParts"></a>   
#### <a name="packageparts"></a>PackageParts  
 Um <xref:System.IO.Packaging.PackagePart> ("parte") é uma classe abstrata que se refere a um objeto armazenado em um <xref:System.IO.Packaging.Package>. Em um arquivo ZIP, as partes do pacote correspondem aos arquivos individuais armazenados no arquivo ZIP.  <xref:System.IO.Packaging.ZipPackagePart> fornece a implementação padrão para objetos serializáveis armazenados em um <xref:System.IO.Packaging.ZipPackage>.  Como em um sistema de arquivos, as partes contidas no pacote são armazenadas em uma organização de diretório hierárquico ou de "estilo de pasta".  Usando o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] APIs de empacotamento, aplicativos podem escrever, armazenar e ler múltiplos <xref:System.IO.Packaging.PackagePart> objetos usando um único contêiner de arquivo ZIP.  
  
<a name="PackageDigitalSignatures"></a>   
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 Para segurança, um <xref:System.IO.Packaging.PackageDigitalSignature> ("assinatura digital") pode ser associada a partes em um pacote. Um <xref:System.IO.Packaging.PackageDigitalSignature> incorpora [509] que fornece dois recursos:  
  
1.  Identifica e autentica o originador da parte.  
  
2.  Valida que a parte não foi modificada.  
  
 A assinatura digital não evita que uma parte seja modificada, mas uma verificação de validação em relação à assinatura digital falhará se a parte tiver sido alterada de alguma maneira. O aplicativo pode adotar a ação adequada, por exemplo, bloquear a abertura da parte ou notificar o usuário que a parte foi modificada e não é segura.  
  
<a name="PackageRelationships"></a>   
#### <a name="packagerelationships"></a>PackageRelationships  
 Um <xref:System.IO.Packaging.PackageRelationship> ("relação") fornece um mecanismo para associar informações adicionais com o pacote ou uma parte no pacote. Um relacionamento é um recurso de nível de pacote que pode associar informações adicionais com uma parte, sem modificar o conteúdo da parte. Inserir novos dados diretamente no conteúdo de uma parte, geralmente, não é algo prático em muitos casos:  
  
-   O tipo real da parte e seu esquema de conteúdo não é conhecido.  
  
-   Mesmo se for conhecido, o esquema de conteúdo poderá não fornecer um meio para acrescentar novas informações.  
  
-   A parte pode ser digitalmente assinada ou criptografada, impedindo qualquer modificação.  
  
 Os relacionamentos de pacotes fornecem um meio detectável de acrescentar e associar informações adicionais com as partes individuais ou com o pacote inteiro. Os relacionamentos de pacotes são usados para duas funções principais:  
  
1.  Definir relações de dependência de uma parte com outra.  
  
2.  Definir relacionamentos de informação que adicionam anotações ou outros dados relacionados à parte.  
  
 A <xref:System.IO.Packaging.PackageRelationship> fornece um meio rápido de definir dependências e outras informações associadas a uma parte do pacote ou ao pacote como um todo.  
  
<a name="Dependency_Relationships"></a>   
##### <a name="dependency-relationships"></a>Relações de dependência  
 As relações de dependência são usadas para descrever as dependências que uma parte cria com outras partes. Por exemplo, um pacote pode conter uma parte HTML que inclui um ou mais marcas de imagem \<img>. As marcas de imagem referem-se a imagens localizadas como outras partes internas ao pacote ou externas ao pacote (tais como acessíveis pela Internet). Criando um <xref:System.IO.Packaging.PackageRelationship> associado com um arquivo HTML torna a descoberta e o acesso a recursos dependentes rápida e fácil. Um aplicativo de navegador ou visualizador pode acessar diretamente os relacionamentos de partes e imediatamente começar a montar os recursos dependentes sem conhecer o esquema ou analisar o documento.  
  
<a name="Information_Relationships"></a>   
##### <a name="information-relationships"></a>Relacionamentos de informações  
 Semelhante a uma observação ou anotação, um <xref:System.IO.Packaging.PackageRelationship> também pode ser usado para armazenar outros tipos de informações a ser associado uma parte sem a necessidade de modificar o conteúdo da parte em si.  
  
<a name="XPS_Documents"></a>   
## <a name="xps-documents"></a>Documentos XPS  
 O documento [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] é um pacote que contém um ou mais documentos estáticos junto com todos os recursos e informações necessárias para a renderização.  O [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] também é o formato de arquivo de spool de impressão nativo do [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  Um <xref:System.Windows.Xps.Packaging.XpsDocument> é armazenado em um dataset ZIP padrão e pode incluir uma combinação de componentes XML e binários, como arquivos de imagem e fontes. Os [PackageRelationships](#PackageRelationships) são usados para definir as dependências entre o conteúdo e os recursos necessários para renderizar completamente o documento.  O <xref:System.Windows.Xps.Packaging.XpsDocument> design fornece uma solução de documento único e de alta fidelidade que dá suporte a vários usos:  
  
-   Leitura, gravação e armazenamento de conteúdo e recursos de documento estático como um arquivo simples, portátil e de fácil distribuição.  
  
-   Exibição de documentos com o aplicativo visualizador [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  
  
-   Geração de documentos no formato de saída do spool de impressão nativo do [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  
  
-   Roteamento de documentos diretamente para uma impressora compatível com [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Documents.FixedDocument>  
 <xref:System.Windows.Documents.FlowDocument>  
 <xref:System.Windows.Xps.Packaging.XpsDocument>  
 <xref:System.IO.Packaging.ZipPackage>  
 <xref:System.IO.Packaging.ZipPackagePart>  
 <xref:System.IO.Packaging.PackageRelationship>  
 <xref:System.Windows.Controls.DocumentViewer>  
 [Texto](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Visão geral do documento de fluxo](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [Visão Geral da Impressão](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Serialização e armazenamento de documentos](../../../../docs/framework/wpf/advanced/document-serialization-and-storage.md)
