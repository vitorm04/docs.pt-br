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
ms.openlocfilehash: 36704d56b66de977ac7f63fd7e766c925ef9023b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974678"
---
# <a name="documents-in-wpf"></a>Documentos no WPF
o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oferece uma ampla gama de recursos de documentos que permitem a criação de conteúdo de alta fidelidade que foi projetada para ser acessada e lida com mais facilidade do que nas gerações anteriores do Windows. Além das capacidades e da qualidade aprimoradas, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também oferece serviços integrados para exibição, empacotamento e segurança de documentos. Este tópico fornece uma introdução aos tipos de documento e ao empacotamento de documento do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="types_of_documents"></a>   
## <a name="types-of-documents"></a>Tipos de documentos  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] divide os documentos em duas grandes categorias com base em seu uso pretendido. Essas categorias de documentos são chamadas de "documentos estáticos" e "documentos dinâmicos".  
  
 Documentos fixos destinam-se a aplicativos que exigem uma apresentação "o que você vê é o que você obtém" (WYSIWYG), independentemente do hardware de vídeo ou da impressora usado. Os usos típicos de documentos estáticos incluem a editoração eletrônica, o processamento de texto e o layout de formulário, nos quais a aderência ao design original da página é essencial. Como parte de seu layout, um documento estático mantém o posicionamento preciso dos elementos de conteúdo, independente do dispositivo de impressão ou de exibição em uso. Por exemplo, uma página de documento estático exibida em uma tela de 96 dpi parecerá exatamente a mesma quando enviada a uma impressora a laser de 600 dpi ou quando for enviada para uma fotocompositora de 4800 dpi. O layout da página permanece o mesmo em todos os casos, embora a qualidade do documento seja maximizada para as capacidades de cada dispositivo.  
  
 Em comparação, os documentos dinâmicos são projetados para otimizar a exibição e legibilidade e são melhor utilizados quando a facilidade de leitura é o cenário principal de consumo de documento. Em vez de serem configurados para um layout predefinido, os documentos dinâmicos ajustam e refluem seu conteúdo com base em variáveis de tempo de execução como tamanho da janela, resolução do dispositivo e preferências opcionais do usuário. Uma página da Web é um exemplo simples de um documento dinâmico em que o conteúdo da página é formatado dinamicamente para se ajustar à janela atual. Os documentos dinâmicos otimizam a experiência de visualização e de leitura para o usuário, com base no ambiente de runtime. Por exemplo, o mesmo documento dinâmico será dinamicamente reformatado para legibilidade otimizada em uma tela de alta resolução de 19 polegadas ou uma tela pequena de PDA de 2x3 polegadas. Além disso, os documentos dinâmicos têm vários recursos internos, incluindo pesquisa, modos de exibição que otimizam a legibilidade e a capacidade de alterar o tamanho e a aparência das fontes.  Consulte [Visão geral de documento dinâmico](flow-document-overview.md) para ilustrações, exemplos e informações aprofundadas sobre documentos dinâmicos.  
  
<a name="document_viewer"></a>   
## <a name="document-controls-and-text-layout"></a>Controles de documento e layout de texto  
 O .NET Framework fornece um conjunto de controles pré-criados que simplificam o uso de documentos fixos, documentos de fluxo e texto geral em seu aplicativo.  Há suporte para a exibição de conteúdo de documento fixo usando o controle de <xref:System.Windows.Controls.DocumentViewer>.  A exibição do conteúdo do documento de fluxo tem suporte em três controles diferentes: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>e <xref:System.Windows.Controls.FlowDocumentScrollViewer> que são mapeados para cenários de usuário diferentes (consulte as seções abaixo).  Outros controles do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornecem layout simplificado para dar suporte a usos de texto geral (consulte [Texto na interface do usuário](#text_in_the_user_interface), abaixo).  
  
### <a name="fixed-document-control---documentviewer"></a>Controle de documento estático – DocumentViewer  
 O controle <xref:System.Windows.Controls.DocumentViewer> foi projetado para exibir <xref:System.Windows.Documents.FixedDocument> conteúdo. O controle de <xref:System.Windows.Controls.DocumentViewer> fornece uma interface de usuário intuitiva que fornece suporte interno para operações comuns, incluindo saída de impressão, cópia para área de transferência, zoom e recursos de pesquisa de texto. O controle fornece acesso a páginas de conteúdo por meio de um mecanismo de rolagem familiar. Como todos os controles de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], o <xref:System.Windows.Controls.DocumentViewer> dá suporte a reestilização completa ou parcial, o que permite que o controle seja integrado visualmente a praticamente qualquer aplicativo ou ambiente.  
  
 <xref:System.Windows.Controls.DocumentViewer> é projetado para exibir conteúdo de forma somente leitura; a edição ou modificação de conteúdo não está disponível e não tem suporte.  
  
<a name="flow_document"></a>   
### <a name="flow-document-controls"></a>Controles de documento dinâmico  

> [!NOTE]
> Para obter informações mais detalhadas sobre os recursos de documentos de fluxo e como criá-los, consulte [visão geral do documento de fluxo](flow-document-overview.md).  
  
 A exibição do conteúdo do documento de fluxo tem suporte em três controles: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>e <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 o <xref:System.Windows.Controls.FlowDocumentReader> inclui recursos que permitem que o usuário escolha dinamicamente entre vários modos de exibição, incluindo um modo de exibição de página única (página por vez), um modo de exibição de duas páginas por vez (formato de leitura de livros) e uma rolagem contínua (sem fim) modo de exibição.  Para obter mais informações sobre esses modos de exibição, consulte <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  Se você não precisar da capacidade de alternar dinamicamente entre modos de exibição diferentes, <xref:System.Windows.Controls.FlowDocumentPageViewer> e <xref:System.Windows.Controls.FlowDocumentScrollViewer> fornecer visualizadores de conteúdo de fluxo mais leves que são corrigidos em um modo de exibição específico.  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer e FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> mostra o conteúdo no modo de exibição de página por vez, enquanto <xref:System.Windows.Controls.FlowDocumentScrollViewer> mostra o conteúdo no modo de rolagem contínua.  Os <xref:System.Windows.Controls.FlowDocumentPageViewer> e <xref:System.Windows.Controls.FlowDocumentScrollViewer> são corrigidos em um modo de exibição específico. Compare com <xref:System.Windows.Controls.FlowDocumentReader>, que inclui recursos que permitem que o usuário escolha dinamicamente entre vários modos de exibição (conforme fornecido pela enumeração <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>), com o custo de ser mais intensivo em recursos do que <xref:System.Windows.Controls.FlowDocumentPageViewer> ou <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Por padrão, uma barra de rolagem vertical é sempre exibida e uma barra de rolagem horizontal se torna visível se necessário. O [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] padrão para <xref:System.Windows.Controls.FlowDocumentScrollViewer> não inclui uma barra de ferramentas; no entanto, a propriedade <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> pode ser usada para habilitar uma barra de ferramentas interna.  
  
<a name="text_in_the_user_interface"></a>   
### <a name="text-in-the-user-interface"></a>Texto na interface do usuário  
 Além de adicionar texto a documentos, o texto também pode ser usado, obviamente, na interface do usuário do aplicativo, como em formulários. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui vários controles para desenhar texto na tela. Cada controle é destinado a um cenário diferente e tem sua própria lista de recursos e limitações. Em geral, o elemento <xref:System.Windows.Controls.TextBlock> deve ser usado quando o suporte a texto limitado é necessário, como uma breve frase em uma [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> pode ser usado quando o suporte a texto mínimo é necessário. Para obter mais informações, consulte [Visão geral do TextBlock](../controls/textblock-overview.md).  
  
<a name="packaging"></a>   
## <a name="document-packaging"></a>Empacotamento de documento  
 As APIs de <xref:System.IO.Packaging> fornecem um meio eficiente para organizar dados de aplicativos, conteúdo de documentos e recursos relacionados em um único contêiner que é simples de acessar, portáteis e fácil de distribuir. Um arquivo ZIP é um exemplo de um tipo de <xref:System.IO.Packaging.Package> capaz de conter vários objetos como uma única unidade. As APIs de empacotamento fornecem uma implementação padrão de <xref:System.IO.Packaging.ZipPackage> projetada usando um padrão de Open Packaging Conventions com a arquitetura de arquivo ZIP e XML. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] APIs de empacotamento simplificam a criação de pacotes e a armazenar e acessar objetos dentro deles. Um objeto armazenado em um <xref:System.IO.Packaging.Package> é conhecido como um <xref:System.IO.Packaging.PackagePart> ("parte"). Os pacotes também podem incluir certificados digitais assinados que podem ser usados para identificar o originador de uma parte e validar que o conteúdo de um pacote não foi modificado.  Os pacotes também incluem um recurso <xref:System.IO.Packaging.PackageRelationship> que permite que informações adicionais sejam adicionadas a um pacote ou associadas a partes específicas sem modificar realmente o conteúdo das partes existentes.  Os serviços de pacote também dão suporte ao Microsoft Windows Rights Management (RM).  
  
 A arquitetura de pacote do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] serve como base para várias tecnologias-chave:  
  
- Documentos XPS em conformidade com o XML Paper Specification (XPS).  
  
- Formato de documentos Microsoft Office "12" Open XML (.docx).  
  
- Formatos de armazenamento personalizado para seu próprio projeto de aplicativo.  
  
 Com base nas APIs de empacotamento, um <xref:System.Windows.Xps.Packaging.XpsDocument> é especificamente projetado para armazenar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] documentos de conteúdo fixo. Um <xref:System.Windows.Xps.Packaging.XpsDocument> é um documento independente que pode ser aberto em um visualizador, exibido em um controle de <xref:System.Windows.Controls.DocumentViewer>, roteado para um spool de impressão ou saída diretamente para uma impressora compatível com XPS.  
  
 As seções a seguir fornecem informações adicionais sobre as APIs de <xref:System.IO.Packaging.Package> e <xref:System.Windows.Xps.Packaging.XpsDocument> fornecidas com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="packages"></a>   
### <a name="package-components"></a>Componentes do pacote  
 As APIs de empacotamento do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permitem que os dados de aplicativos e documentos sejam organizados em uma única unidade portátil. Um arquivo ZIP é um dos tipos mais comuns de pacotes e é o tipo de pacote padrão fornecido com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  <xref:System.IO.Packaging.Package> em si é uma classe abstrata da qual <xref:System.IO.Packaging.ZipPackage> é implementado usando uma arquitetura de arquivo XML e ZIP padrão aberta.  O método <xref:System.IO.Packaging.Package.Open%2A> usa <xref:System.IO.Packaging.ZipPackage> para criar e usar arquivos ZIP por padrão. Um pacote pode conter três tipos básicos de itens:  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Conteúdo, dados, documentos e arquivos de recurso do aplicativo.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|[Certificado X.509] para identificação, autenticação e validação.|  
|<xref:System.IO.Packaging.PackageRelationship>|Informações adicionadas relacionadas ao pacote ou a uma parte específica.|  
  
<a name="PackageParts"></a>   
#### <a name="packageparts"></a>PackageParts  
 Uma <xref:System.IO.Packaging.PackagePart> ("parte") é uma classe abstrata que se refere a um objeto armazenado em um <xref:System.IO.Packaging.Package>. Em um arquivo ZIP, as partes do pacote correspondem aos arquivos individuais armazenados no arquivo ZIP.  <xref:System.IO.Packaging.ZipPackagePart> fornece a implementação padrão para objetos serializáveis armazenados em um <xref:System.IO.Packaging.ZipPackage>.  Como em um sistema de arquivos, as partes contidas no pacote são armazenadas em uma organização de diretório hierárquico ou de "estilo de pasta".  Usando as APIs de empacotamento [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], os aplicativos podem gravar, armazenar e ler vários objetos <xref:System.IO.Packaging.PackagePart> usando um único contêiner de arquivo ZIP.  
  
<a name="PackageDigitalSignatures"></a>   
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 Para segurança, uma <xref:System.IO.Packaging.PackageDigitalSignature> ("assinatura digital") pode ser associada a partes dentro de um pacote. Uma <xref:System.IO.Packaging.PackageDigitalSignature> incorpora um [509] que fornece dois recursos:  
  
1. Identifica e autentica o originador da parte.  
  
2. Valida que a parte não foi modificada.  
  
 A assinatura digital não evita que uma parte seja modificada, mas uma verificação de validação em relação à assinatura digital falhará se a parte tiver sido alterada de alguma maneira. O aplicativo pode adotar a ação adequada, por exemplo, bloquear a abertura da parte ou notificar o usuário que a parte foi modificada e não é segura.  
  
<a name="PackageRelationships"></a>   
#### <a name="packagerelationships"></a>PackageRelationships  
 Uma <xref:System.IO.Packaging.PackageRelationship> ("relationship") fornece um mecanismo para associar informações adicionais ao pacote ou a uma parte dentro do pacote. Um relacionamento é um recurso de nível de pacote que pode associar informações adicionais com uma parte, sem modificar o conteúdo da parte. Inserir novos dados diretamente no conteúdo de uma parte, geralmente, não é algo prático em muitos casos:  
  
- O tipo real da parte e seu esquema de conteúdo não é conhecido.  
  
- Mesmo se for conhecido, o esquema de conteúdo poderá não fornecer um meio para acrescentar novas informações.  
  
- A parte pode ser digitalmente assinada ou criptografada, impedindo qualquer modificação.  
  
 Os relacionamentos de pacotes fornecem um meio detectável de acrescentar e associar informações adicionais com as partes individuais ou com o pacote inteiro. Os relacionamentos de pacotes são usados para duas funções principais:  
  
1. Definir relações de dependência de uma parte com outra.  
  
2. Definir relacionamentos de informação que adicionam anotações ou outros dados relacionados à parte.  
  
 Uma <xref:System.IO.Packaging.PackageRelationship> fornece um meio rápido e detectável para definir dependências e adicionar outras informações associadas a uma parte do pacote ou ao pacote como um todo.  
  
<a name="Dependency_Relationships"></a>   
##### <a name="dependency-relationships"></a>Relações de dependência  
 As relações de dependência são usadas para descrever as dependências que uma parte cria com outras partes. Por exemplo, um pacote pode conter uma parte HTML que inclui um ou mais marcas de imagem \<img>. As marcas de imagem referem-se a imagens localizadas como outras partes internas ao pacote ou externas ao pacote (tais como acessíveis pela Internet). Criar um <xref:System.IO.Packaging.PackageRelationship> associado ao arquivo HTML torna rápida e fácil a descoberta e o acesso aos recursos dependentes. Um aplicativo de navegador ou visualizador pode acessar diretamente os relacionamentos de partes e imediatamente começar a montar os recursos dependentes sem conhecer o esquema ou analisar o documento.  
  
<a name="Information_Relationships"></a>   
##### <a name="information-relationships"></a>Relacionamentos de informações  
 Semelhante a uma anotação ou anotação, uma <xref:System.IO.Packaging.PackageRelationship> também pode ser usada para armazenar outros tipos de informações a serem associadas a uma parte sem precisar modificar o próprio conteúdo da parte.  
  
<a name="XPS_Documents"></a>   
## <a name="xps-documents"></a>Documentos XPS  
 O documento XPS (XML Paper Specification) é um pacote que contém um ou mais documentos fixos, juntamente com todos os recursos e as informações necessárias para a renderização.  XPS também é o formato de arquivo de spool de impressão nativo do Windows Vista.  Um <xref:System.Windows.Xps.Packaging.XpsDocument> é armazenado no conjunto de caracteres ZIP padrão e pode incluir uma combinação de componentes XML e binários, como arquivos de imagem e de fonte. Os [PackageRelationships](#PackageRelationships) são usados para definir as dependências entre o conteúdo e os recursos necessários para renderizar completamente o documento.  O design de <xref:System.Windows.Xps.Packaging.XpsDocument> fornece uma solução de documento única e de alta fidelidade que dá suporte a vários usos:  
  
- Leitura, gravação e armazenamento de conteúdo e recursos de documento estático como um arquivo simples, portátil e de fácil distribuição.  
  
- Exibindo documentos com o aplicativo Visualizador XPS.  
  
- Gerando documentos no formato de saída do spool de impressão nativo do Windows Vista.  
  
- Roteamento de documentos diretamente para uma impressora compatível com XPS.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Documents.FixedDocument>
- <xref:System.Windows.Documents.FlowDocument>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.IO.Packaging.ZipPackage>
- <xref:System.IO.Packaging.ZipPackagePart>
- <xref:System.IO.Packaging.PackageRelationship>
- <xref:System.Windows.Controls.DocumentViewer>
- [Texto](optimizing-performance-text.md)
- [Visão geral do documento de fluxo](flow-document-overview.md)
- [Visão Geral da Impressão](printing-overview.md)
- [Serialização e armazenamento de documentos](document-serialization-and-storage.md)
