---
title: "Serialização e armazenamento do documento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 'serialization of documents [WPF], , '
- documents [WPF], storage
- documents [WPF], serialization
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 34b517366a5f143a86388abff5ae13022bc710c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="document-serialization-and-storage"></a>Serialização e armazenamento do documento
[!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] fornece um ambiente excelente para criar e exibir documentos de alta qualidade.  Os recursos avançados que dão suporte a documentos fixos e documentos de fluxo, controles de exibição avançados, combinados com recursos gráficos 2D e 3D avançados levam os aplicativos [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] a um novo nível de qualidade e experiência do usuário.  Ser capaz de gerenciar com flexibilidade uma representação na memória de um documento é um recurso chave do [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] e ser capaz de salvar e carregar documentos de um armazenamento de dados de forma eficiente é uma necessidade de quase todos os aplicativos.  O processo de conversão de um documento de uma representação na memória interna em um armazenamento de dados externo é chamado de serialização.  O processo inverso de ler um armazenamento de dados e recriar a instância original na memória é chamado desserialização.  
  
 
  
<a name="AboutSerialization"></a>   
## <a name="about-document-serialization"></a>Sobre a serialização de documento  
 Idealmente, o processo de serialização e desserialização de um documento da e de volta para a memória é transparente para o aplicativo.  O aplicativo chama um método de "gravação" do serializador para salvar o documento, enquanto um método de "leitura" do desserializador acessa o armazenamento de dados e recria a instância original em memória.  O formato específico que os dados são armazenados, geralmente, não é uma preocupação do aplicativo, desde que o processo de serializar e desserializar recrie o documento em sua forma original.  
  
 Geralmente, os aplicativos fornecem várias opções de serialização que permitem ao usuário salvar documentos em mídias diferentes ou em um formato diferente.  Por exemplo, um aplicativo pode oferecer opções "Salvar como" para armazenar um documento em um arquivo de disco, banco de dados ou serviço Web.  Da mesma forma, diferentes serializadores poderiam armazenar o documento em diferentes formatos, como HTML, RTF, XML, XPS ou em um formato de terceiros.  Para o aplicativo, a serialização define uma interface que isola os detalhes da mídia de armazenamento dentro da implementação de cada serializador específico.  Além dos benefícios do encapsulamento de detalhes de armazenamento, o [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] <xref:System.Windows.Documents.Serialization> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] fornece vários outros recursos importantes.  
  
### <a name="features-of-net-framework-30-document-serializers"></a>Recursos dos serializadores de documento do .NET Framework 3.0  
  
-   O acesso direto aos objetos de documento de alto nível (árvore lógica e elementos visuais) permite um armazenamento eficiente de conteúdo paginado, elementos 2D/3D, imagens, mídia, hiperlinks, anotações e outros conteúdos de suporte.  
  
-   Operações síncronas e assíncronas.  
  
-   Suporte para serializadores de plug-ins com recursos aprimorados:  
  
    -   Acesso em todo o sistema para uso por todos os aplicativos [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)].  
  
    -   Descoberta de plug-in de aplicativo simples.  
  
    -   Implantação simples, instalação e atualização para plug-ins personalizados de terceiros.  
  
    -   Suporte à interface do usuário para opções e configurações personalizadas de tempo de execução.  
  
### <a name="xps-print-path"></a>Caminho de impressão XPS  
 O caminho de impressão [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] também fornece um mecanismo extensível para gravar documentos por meio da saída de impressão.  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] serve como formato de arquivo de documento e é o formato de spool de impressão nativo para [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  Os documentos [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] podem ser enviados diretamente para impressoras compatíveis com [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] sem a necessidade de conversão para um formato intermediário.  Consulte a [Visão geral sobre impressão](../../../../docs/framework/wpf/advanced/printing-overview.md) para obter informações adicionais sobre as opções de saída de caminho de impressão e recursos.  
  
<a name="PluginSerializers"></a>   
## <a name="plug-in-serializers"></a>Plug-ins serializadores  
 O <xref:System.Windows.Documents.Serialization> APIs oferecem suporte para plug-ins serializadores e serializadores que são instalados separadamente do aplicativo, associados em tempo de execução e são acessados usando o <xref:System.Windows.Documents.Serialization.SerializerProvider> mecanismo de descoberta.  Os serializadores de plug-in oferecem benefícios aprimorados para facilitar a implantação e o uso em todo o sistema.  Os serializadores vinculados também podem ser implementados em ambientes de confiança parcial, como [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] em que os plug-ins nos serializadores não são acessíveis.  Serializadores, que se baseiam em uma implementação derivada do <xref:System.Windows.Documents.Serialization.SerializerWriter> de classe, que são compilados e ligados diretamente ao aplicativo.  Os serializadores de plug-in e serializadores vinculados operam por métodos públicos idênticos e eventos, o que torna mais fácil o uso de um ou ambos os tipos de serializadores no mesmo aplicativo.  
  
 Os serializadores de plug-in ajudam os desenvolvedores de aplicativos fornecendo extensibilidade para novos projetos de armazenamento e formatos de arquivo sem a necessidade de código diretamente para cada formato em potencial no momento de build.  Os serializadores de plug-in também beneficiam os desenvolvedores de terceiros, fornecendo um meio padronizado para implantar, instalar e atualizar plug-ins acessíveis pelo sistema para formatos de arquivo personalizados ou proprietários.  
  
### <a name="using-a-plug-in-serializer"></a>Usando um serializador de plug-in  
 Os serializadores de plug-in são simples de usar.  O <xref:System.Windows.Documents.Serialization.SerializerProvider> classe enumera um <xref:System.Windows.Documents.Serialization.SerializerDescriptor> do objeto para cada plug-in instalado no sistema.  O <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A> propriedade filtra os plug-ins instalados com base na configuração atual e verifica se o serializador pode ser carregado e usado pelo aplicativo.  O <xref:System.Windows.Documents.Serialization.SerializerDescriptor> também oferece outras propriedades, como <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A> e <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>, que o aplicativo pode usar para solicitar que o usuário selecione um serializador para um formato de saída disponível.  Um serializador de plug-in padrão para [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] é fornecido com [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] e é sempre enumerado.  Depois que o usuário seleciona um formato de saída, o <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> método é usado para criar um <xref:System.Windows.Documents.Serialization.SerializerWriter> para o formato específico.  O <xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> , em seguida, pode ser chamado para o fluxo de documento para o repositório de dados de saída do método.  
  
 O exemplo a seguir ilustra um aplicativo que usa o <xref:System.Windows.Documents.Serialization.SerializerProvider> método em uma propriedade "PlugInFileFilter".  PlugInFileFilter enumera os plug-ins instalados e cria uma cadeia de caracteres de filtro com as opções de arquivo disponíveis para um <xref:Microsoft.Win32.SaveFileDialog>.  
  
 [!code-csharp[DocumentSerialize#DocSerializeFileFilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]  
  
 Depois que um nome de arquivo de saída foi selecionado pelo usuário, o exemplo a seguir ilustra o uso do <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> método para armazenar um determinado documento em um formato especificado.  
  
 [!code-csharp[DocumentSerialize#DocSerializePlugIn](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]  
  
<a name="InstallingPluginSerializers"></a>   
### <a name="installing-plug-in-serializers"></a>Instalando serializadores de plug-in  
 O <xref:System.Windows.Documents.Serialization.SerializerProvider> classe fornece a interface de aplicativo de nível superior para a descoberta do serializador de plug-in e acesso.  <xref:System.Windows.Documents.Serialization.SerializerProvider>Localiza e fornece uma lista dos serializadores que estão instalados e acessíveis no sistema de aplicativo.  As especificidades dos serializadores instalados são definidas nas configurações do Registro.  Plug-ins serializadores podem ser adicionados ao registro usando o <xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A> método; ou se [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] ainda não estiver instalado, a instalação do plug-in script pode diretamente o registro do conjunto de valores em si.  O <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A> método pode ser usado para remover um instalado anteriormente plug-in, ou as configurações do Registro podem ser redefinidas da mesma forma por um script de desinstalação.  
  
### <a name="creating-a-plug-in-serializer"></a>Criando um serializador de plug-in  
 Os serializadores de plug-in e os serializadores vinculados usam os mesmos eventos e métodos públicos expostos e, da mesma forma, podem ser projetados para operar de forma síncrona ou assíncrona.  Há três etapas básicas normalmente seguidas para criar um serializador de plug-in:  
  
1.  Implementar e depurar o serializador primeiramente como um serializador vinculado.  Criar, inicialmente, o serializador compilado e o vinculado diretamente em um aplicativo de teste fornece acesso completo a pontos de interrupção e outros serviços de depuração úteis para teste.  
  
2.  Depois que o serializador foi totalmente testado, um <xref:System.Windows.Documents.Serialization.ISerializerFactory> interface é adicionada ao criar um plug-in.  O <xref:System.Windows.Documents.Serialization.ISerializerFactory> interface permite acesso completo a todos os [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] objetos que inclui a árvore lógica, <xref:System.Windows.UIElement> objetos, <xref:System.Windows.Documents.IDocumentPaginatorSource>, e <xref:System.Windows.Media.Visual> elementos.  Além disso <xref:System.Windows.Documents.Serialization.ISerializerFactory> fornece os mesmos métodos síncronos e assíncronos e utilizados por serializadores de eventos.  Já que documentos grandes podem levar tempo para serem enviados, as operações assíncronas são recomendadas para manter a interação do usuário responsivo e oferecem uma opção "Cancelar" se ocorrer algum problema com o armazenamento de dados.  
  
3.  Depois que o serializador de plug-in for criado, um script de instalação será implementado para distribuir e instalar (e desinstalar) o plug-in (veja acima, "[Instalando serializadores de plug-in](#InstallingPluginSerializers)").  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Documents.Serialization>  
 <xref:System.Windows.Xps.XpsDocumentWriter>  
 <xref:System.Windows.Xps.Packaging.XpsDocument>  
 [Documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Visão Geral da Impressão](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [XML Paper Specification: visão geral](http://go.microsoft.com/fwlink?LinkID=106246)
