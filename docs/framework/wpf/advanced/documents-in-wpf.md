---
title: Documentos
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
ms.openlocfilehash: e88604c42b253b48ee605f42f24fe301e339f74b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174674"
---
# <a name="documents-in-wpf"></a>Documentos no WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]oferece uma ampla gama de recursos de documentos que permitem a criação de conteúdo de alta fidelidade que foi projetado para ser mais facilmente acessado e lido do que nas gerações anteriores do Windows. Além das capacidades e da qualidade aprimoradas, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também oferece serviços integrados para exibição, empacotamento e segurança de documentos. Este tópico fornece uma introdução aos tipos de documento e ao empacotamento de documento do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="types_of_documents"></a>
## <a name="types-of-documents"></a>Tipos de documentos  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] divide os documentos em duas grandes categorias com base em seu uso pretendido. Essas categorias de documentos são chamadas de "documentos estáticos" e "documentos dinâmicos".  
  
 Os documentos fixos destinam-se a aplicativos que requerem uma apresentação precisa de "o que você vê é o que você recebe" (WYSIWYG), independente do hardware de exibição ou impressora usado. Os usos típicos de documentos estáticos incluem a editoração eletrônica, o processamento de texto e o layout de formulário, nos quais a aderência ao design original da página é essencial. Como parte de seu layout, um documento estático mantém o posicionamento preciso dos elementos de conteúdo, independente do dispositivo de impressão ou de exibição em uso. Por exemplo, uma página de documento estático exibida em uma tela de 96 dpi parecerá exatamente a mesma quando enviada a uma impressora a laser de 600 dpi ou quando for enviada para uma fotocompositora de 4800 dpi. O layout da página permanece o mesmo em todos os casos, embora a qualidade do documento seja maximizada para as capacidades de cada dispositivo.  
  
 Em comparação, os documentos dinâmicos são projetados para otimizar a exibição e legibilidade e são melhor utilizados quando a facilidade de leitura é o cenário principal de consumo de documento. Em vez de serem configurados para um layout predefinido, os documentos dinâmicos ajustam e refluem seu conteúdo com base em variáveis de tempo de execução como tamanho da janela, resolução do dispositivo e preferências opcionais do usuário. Uma página da Web é um exemplo simples de um documento dinâmico em que o conteúdo da página é formatado dinamicamente para se ajustar à janela atual. Os documentos dinâmicos otimizam a experiência de visualização e de leitura para o usuário, com base no ambiente de runtime. Por exemplo, o mesmo documento dinâmico será dinamicamente reformatado para legibilidade otimizada em uma tela de alta resolução de 19 polegadas ou uma tela pequena de PDA de 2x3 polegadas. Além disso, os documentos dinâmicos têm vários recursos internos, incluindo pesquisa, modos de exibição que otimizam a legibilidade e a capacidade de alterar o tamanho e a aparência das fontes.  Consulte [Visão geral de documento dinâmico](flow-document-overview.md) para ilustrações, exemplos e informações aprofundadas sobre documentos dinâmicos.  
  
<a name="document_viewer"></a>
## <a name="document-controls-and-text-layout"></a>Controles de documento e layout de texto  
 O .NET Framework fornece um conjunto de controles pré-construídos que simplificam o uso de documentos fixos, documentos de fluxo e texto geral dentro do seu aplicativo.  A exibição do conteúdo do <xref:System.Windows.Controls.DocumentViewer> documento fixo é suportada usando o controle.  A exibição do conteúdo do documento de <xref:System.Windows.Controls.FlowDocumentReader> <xref:System.Windows.Controls.FlowDocumentPageViewer>fluxo <xref:System.Windows.Controls.FlowDocumentScrollViewer> é suportada por três controles diferentes: , e qual mapeia para diferentes cenários do usuário (ver seções abaixo).  Outros controles do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornecem layout simplificado para dar suporte a usos de texto geral (consulte [Texto na interface do usuário](#text_in_the_user_interface), abaixo).  
  
### <a name="fixed-document-control---documentviewer"></a>Controle de documento estático – DocumentViewer  
 O <xref:System.Windows.Controls.DocumentViewer> controle foi <xref:System.Windows.Documents.FixedDocument> projetado para exibir conteúdo. O <xref:System.Windows.Controls.DocumentViewer> controle fornece uma interface de usuário intuitiva que fornece suporte interno para operações comuns, incluindo saída de impressão, cópia para recursos de área de transferência, zoom e pesquisa de texto. O controle fornece acesso a páginas de conteúdo por meio de um mecanismo de rolagem familiar. Como [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] todos os <xref:System.Windows.Controls.DocumentViewer> controles, suporta reestilização completa ou parcial, o que permite que o controle seja visualmente integrado em praticamente qualquer aplicativo ou ambiente.  
  
 <xref:System.Windows.Controls.DocumentViewer>é projetado para exibir conteúdo de forma apenas leitura; a edição ou modificação do conteúdo não está disponível e não é suportada.  
  
<a name="flow_document"></a>
### <a name="flow-document-controls"></a>Controles de documento dinâmico  

> [!NOTE]
> Para obter informações mais detalhadas sobre os recursos dos documentos de fluxo e como criá-los, consulte [Visão geral do documento de fluxo](flow-document-overview.md).  
  
 A exibição do conteúdo do documento <xref:System.Windows.Controls.FlowDocumentReader>de <xref:System.Windows.Controls.FlowDocumentPageViewer>fluxo <xref:System.Windows.Controls.FlowDocumentScrollViewer>é suportada por três controles: , e .  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader>inclui recursos que permitem ao usuário escolher dinamicamente entre vários modos de visualização, incluindo um modo de visualização de uma página (página de cada vez), um modo de visualização de duas páginas por vez (formato de leitura de livro) e um modo de visualização de rolagem contínua (sem fundo).  Para obter mais informações sobre <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>esses modos de visualização, consulte .  Se você não precisar da capacidade de alternar <xref:System.Windows.Controls.FlowDocumentPageViewer> dinamicamente entre diferentes modos de visualização e <xref:System.Windows.Controls.FlowDocumentScrollViewer> fornecer espectadores de conteúdo de fluxo de peso mais leve que são corrigidos em um modo de visualização específico.  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer e FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>mostra o conteúdo no modo de visualização <xref:System.Windows.Controls.FlowDocumentScrollViewer> de página em tempo, enquanto mostra o conteúdo no modo de rolagem contínua.  Ambos <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentScrollViewer> são fixados a um modo de visualização específico. Compare <xref:System.Windows.Controls.FlowDocumentReader>com , que inclui recursos que permitem ao usuário escolher dinamicamente <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> entre vários modos de visualização <xref:System.Windows.Controls.FlowDocumentPageViewer> (conforme fornecido pela enumeração), ao custo de ser mais intensivo em recursos do que ou <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Por padrão, uma barra de rolagem vertical é sempre exibida e uma barra de rolagem horizontal se torna visível se necessário. O [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] padrão <xref:System.Windows.Controls.FlowDocumentScrollViewer> para não inclui uma barra de ferramentas; no entanto, a <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> propriedade pode ser usada para habilitar uma barra de ferramentas incorporada.  
  
<a name="text_in_the_user_interface"></a>
### <a name="text-in-the-user-interface"></a>Texto na interface do usuário  
 Além de adicionar texto a documentos, o texto também pode ser usado, obviamente, na interface do usuário do aplicativo, como em formulários. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui vários controles para desenhar texto na tela. Cada controle é destinado a um cenário diferente e tem sua própria lista de recursos e limitações. Em geral, <xref:System.Windows.Controls.TextBlock> o elemento deve ser usado quando for necessário suporte [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]de texto limitado, como uma breve frase em um . <xref:System.Windows.Controls.Label>pode ser usado quando o suporte mínimo de texto é necessário. Para obter mais informações, consulte [Visão geral do TextBlock](../controls/textblock-overview.md).  
  
<a name="packaging"></a>
## <a name="document-packaging"></a>Empacotamento de documento  
 As <xref:System.IO.Packaging> APIs fornecem um meio eficiente de organizar dados de aplicativos, conteúdo de documentos e recursos relacionados em um único contêiner simples de acessar, portátil e fácil de distribuir. Um arquivo ZIP é <xref:System.IO.Packaging.Package> um exemplo de um tipo capaz de segurar vários objetos como uma única unidade. As APIs de <xref:System.IO.Packaging.ZipPackage> embalagem fornecem uma implementação padrão projetada usando um padrão Open Packaging Conventions com arquitetura de arquivo XML e ZIP. As [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] APIs de embalagem facilitam a criação de pacotes e a armazenamento e acesso de objetos dentro delas. Um objeto armazenado <xref:System.IO.Packaging.Package> em um <xref:System.IO.Packaging.PackagePart> é referido como um ("parte"). Os pacotes também podem incluir certificados digitais assinados que podem ser usados para identificar o originador de uma parte e validar que o conteúdo de um pacote não foi modificado.  Os pacotes <xref:System.IO.Packaging.PackageRelationship> também incluem um recurso que permite que informações adicionais sejam adicionadas a um pacote ou associadas a partes específicas sem realmente modificar o conteúdo das peças existentes.  Os serviços de pacote também suportam o Microsoft Windows Rights Management (RM).  
  
 A arquitetura de pacote do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] serve como base para várias tecnologias-chave:  
  
- Documentos XPS em conformidade com a Especificação de Papel XML (XPS).  
  
- Formato de documentos Microsoft Office "12" Open XML (.docx).  
  
- Formatos de armazenamento personalizado para seu próprio projeto de aplicativo.  
  
 Com base nas APIs <xref:System.Windows.Xps.Packaging.XpsDocument> de embalagem, uma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é especificamente projetada para armazenar documentos de conteúdo fixo. Um <xref:System.Windows.Xps.Packaging.XpsDocument> é um documento independente que pode ser aberto em <xref:System.Windows.Controls.DocumentViewer> um visualizador, exibido em um controle, encaminhado para um carretel de impressão ou sair diretamente para uma impressora compatível com XPS.  
  
 As seções a seguir <xref:System.IO.Packaging.Package> fornecem <xref:System.Windows.Xps.Packaging.XpsDocument> informações adicionais [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]sobre as APIs fornecidas.  
  
<a name="packages"></a>
### <a name="package-components"></a>Componentes do pacote  
 As APIs de empacotamento do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permitem que os dados de aplicativos e documentos sejam organizados em uma única unidade portátil. Um arquivo ZIP é um dos tipos mais comuns de pacotes e é o tipo de pacote padrão fornecido com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  <xref:System.IO.Packaging.Package>em si é <xref:System.IO.Packaging.ZipPackage> uma classe abstrata da qual é implementada usando uma arquitetura de arquivo XML e ZIP padrão aberta.  O <xref:System.IO.Packaging.Package.Open%2A> método <xref:System.IO.Packaging.ZipPackage> é usado para criar e usar arquivos ZIP por padrão. Um pacote pode conter três tipos básicos de itens:  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Conteúdo, dados, documentos e arquivos de recurso do aplicativo.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|[Certificado X.509] para identificação, autenticação e validação.|  
|<xref:System.IO.Packaging.PackageRelationship>|Informações adicionadas relacionadas ao pacote ou a uma parte específica.|  
  
<a name="PackageParts"></a>
#### <a name="packageparts"></a>PackageParts  
 A <xref:System.IO.Packaging.PackagePart> ("parte") é uma classe abstrata que se <xref:System.IO.Packaging.Package>refere a um objeto armazenado em um . Em um arquivo ZIP, as partes do pacote correspondem aos arquivos individuais armazenados no arquivo ZIP.  <xref:System.IO.Packaging.ZipPackagePart>fornece a implementação padrão para <xref:System.IO.Packaging.ZipPackage>objetos serializáveis armazenados em um .  Como em um sistema de arquivos, as partes contidas no pacote são armazenadas em uma organização de diretório hierárquico ou de "estilo de pasta".  Usando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as APIs de embalagem, os aplicativos <xref:System.IO.Packaging.PackagePart> podem escrever, armazenar e ler vários objetos usando um único recipiente de arquivo ZIP.  
  
<a name="PackageDigitalSignatures"></a>
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 Para segurança, <xref:System.IO.Packaging.PackageDigitalSignature> uma ("assinatura digital") pode ser associada a peças dentro de um pacote. A <xref:System.IO.Packaging.PackageDigitalSignature> incorpora um [509] que fornece duas características:  
  
1. Identifica e autentica o originador da parte.  
  
2. Valida que a parte não foi modificada.  
  
 A assinatura digital não evita que uma parte seja modificada, mas uma verificação de validação em relação à assinatura digital falhará se a parte tiver sido alterada de alguma maneira. O aplicativo pode adotar a ação adequada, por exemplo, bloquear a abertura da parte ou notificar o usuário que a parte foi modificada e não é segura.  
  
<a name="PackageRelationships"></a>
#### <a name="packagerelationships"></a>PackageRelationships  
 A <xref:System.IO.Packaging.PackageRelationship> ("relacionamento") fornece um mecanismo para associar informações adicionais com o pacote ou uma parte dentro do pacote. Um relacionamento é um recurso de nível de pacote que pode associar informações adicionais com uma parte, sem modificar o conteúdo da parte. Inserir novos dados diretamente no conteúdo de uma parte, geralmente, não é algo prático em muitos casos:  
  
- O tipo real da parte e seu esquema de conteúdo não é conhecido.  
  
- Mesmo se for conhecido, o esquema de conteúdo poderá não fornecer um meio para acrescentar novas informações.  
  
- A parte pode ser digitalmente assinada ou criptografada, impedindo qualquer modificação.  
  
 Os relacionamentos de pacotes fornecem um meio detectável de acrescentar e associar informações adicionais com as partes individuais ou com o pacote inteiro. Os relacionamentos de pacotes são usados para duas funções principais:  
  
1. Definir relações de dependência de uma parte com outra.  
  
2. Definir relacionamentos de informação que adicionam anotações ou outros dados relacionados à parte.  
  
 A <xref:System.IO.Packaging.PackageRelationship> fornece um meio rápido e descobrivel para definir dependências e adicionar outras informações associadas a uma parte do pacote ou ao pacote como um todo.  
  
<a name="Dependency_Relationships"></a>
##### <a name="dependency-relationships"></a>Relações de dependência  
 As relações de dependência são usadas para descrever as dependências que uma parte cria com outras partes. Por exemplo, um pacote pode conter uma parte HTML que inclui um ou mais marcas de imagem \<img>. As marcas de imagem referem-se a imagens localizadas como outras partes internas ao pacote ou externas ao pacote (tais como acessíveis pela Internet). Criar <xref:System.IO.Packaging.PackageRelationship> um arquivo associado ao HTML torna a descoberta e o acesso aos recursos dependentes de fácil e fácil acesso. Um aplicativo de navegador ou visualizador pode acessar diretamente os relacionamentos de partes e imediatamente começar a montar os recursos dependentes sem conhecer o esquema ou analisar o documento.  
  
<a name="Information_Relationships"></a>
##### <a name="information-relationships"></a>Relacionamentos de informações  
 Semelhante a uma nota ou <xref:System.IO.Packaging.PackageRelationship> anotação, um também pode ser usado para armazenar outros tipos de informações para ser associado a uma peça sem ter que realmente modificar o conteúdo da peça em si.  
  
<a name="XPS_Documents"></a>
## <a name="xps-documents"></a>Documentos XPS  
 XML Paper Specification (XPS) é um pacote que contém um ou mais documentos fixos, juntamente com todos os recursos e informações necessários para a renderização.  XPS também é o formato nativo de arquivo de bobina de impressão do Windows Vista.  Um <xref:System.Windows.Xps.Packaging.XpsDocument> é armazenado no conjunto de dados ZIP padrão e pode incluir uma combinação de XML e componentes binários, como arquivos de imagem e fonte. Os [PackageRelationships](#PackageRelationships) são usados para definir as dependências entre o conteúdo e os recursos necessários para renderizar completamente o documento.  O <xref:System.Windows.Xps.Packaging.XpsDocument> design fornece uma solução de documento única e de alta fidelidade que suporta vários usos:  
  
- Leitura, gravação e armazenamento de conteúdo e recursos de documento estático como um arquivo simples, portátil e de fácil distribuição.  
  
- Exibindo documentos com o aplicativo XPS Viewer.  
  
- Saída de documentos no formato nativo de saída de bobina de impressão do Windows Vista.  
  
- Roteamento de documentos diretamente para uma impressora compatível com XPS.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Documents.FixedDocument>
- <xref:System.Windows.Documents.FlowDocument>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.IO.Packaging.ZipPackage>
- <xref:System.IO.Packaging.ZipPackagePart>
- <xref:System.IO.Packaging.PackageRelationship>
- <xref:System.Windows.Controls.DocumentViewer>
- [Texto](optimizing-performance-text.md)
- [Visão geral do documento de fluxo](flow-document-overview.md)
- [Visão geral da impressão](printing-overview.md)
- [Serialização e armazenamento de documentos](document-serialization-and-storage.md)
