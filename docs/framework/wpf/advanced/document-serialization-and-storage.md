---
title: Serialização e armazenamento do documento
ms.date: 03/30/2017
helpviewer_keywords:
- 'serialization of documents [WPF], , '
- documents [WPF], storage
- documents [WPF], serialization
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
ms.openlocfilehash: 7ddd887eefd67a3300795396dac26e855f30989e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254119"
---
# <a name="document-serialization-and-storage"></a>Serialização e armazenamento do documento

O Microsoft .NET Framework fornece um ambiente poderoso para criar e exibir documentos de alta qualidade.  Recursos aprimorados que dão suporte a documentos fixos e documentos de fluxo, controles de exibição avançados, combinados com poderosos recursos gráficos 2D e 3D, levam .NET Framework aplicativos a um novo nível de qualidade e experiência do usuário.  Ser capaz de gerenciar com flexibilidade uma representação de um documento na memória é um recurso-chave de .NET Framework, e ser capaz de salvar e carregar documentos com eficiência de um armazenamento de dados é uma necessidade de quase todos os aplicativos.  O processo de conversão de um documento de uma representação na memória interna em um armazenamento de dados externo é chamado de serialização.  O processo inverso de ler um armazenamento de dados e recriar a instância original na memória é chamado desserialização.

<a name="AboutSerialization"></a>

## <a name="about-document-serialization"></a>Sobre a serialização de documento

Idealmente, o processo de serialização e desserialização de um documento da e de volta para a memória é transparente para o aplicativo.  O aplicativo chama um método de "gravação" do serializador para salvar o documento, enquanto um método de "leitura" do desserializador acessa o armazenamento de dados e recria a instância original em memória.  O formato específico que os dados são armazenados, geralmente, não é uma preocupação do aplicativo, desde que o processo de serializar e desserializar recrie o documento em sua forma original.

Geralmente, os aplicativos fornecem várias opções de serialização que permitem ao usuário salvar documentos em mídias diferentes ou em um formato diferente.  Por exemplo, um aplicativo pode oferecer opções "Salvar como" para armazenar um documento em um arquivo de disco, banco de dados ou serviço Web.  Da mesma forma, diferentes serializadores poderiam armazenar o documento em diferentes formatos, como HTML, RTF, XML, XPS ou em um formato de terceiros.  Para o aplicativo, a serialização define uma interface que isola os detalhes da mídia de armazenamento dentro da implementação de cada serializador específico.  Além dos benefícios de encapsular os detalhes de armazenamento, as APIs <xref:System.Windows.Documents.Serialization> de .NET Framework fornecem vários outros recursos importantes.

### <a name="features-of-net-framework-30-document-serializers"></a>Recursos dos serializadores de documento do .NET Framework 3.0

- O acesso direto aos objetos de documento de alto nível (árvore lógica e elementos visuais) permite um armazenamento eficiente de conteúdo paginado, elementos 2D/3D, imagens, mídia, hiperlinks, anotações e outros conteúdos de suporte.

- Operações síncronas e assíncronas.

- Suporte para serializadores de plug-ins com recursos aprimorados:

  - Acesso de todo o sistema para uso por todos os aplicativos .NET Framework.

  - Descoberta de plug-in de aplicativo simples.

  - Implantação simples, instalação e atualização para plug-ins personalizados de terceiros.

  - Suporte à interface do usuário para opções e configurações personalizadas de tempo de execução.

### <a name="xps-print-path"></a>Caminho de impressão XPS

O caminho de impressão XPS do Microsoft .NET Framework também fornece um mecanismo extensível para a gravação de documentos por meio da saída de impressão.  O XPS serve como um formato de arquivo de documento e é o formato de spool [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)]de impressão nativo para o.  Os documentos XPS podem ser enviados diretamente para impressoras compatíveis com XPS sem a necessidade de conversão em um formato intermediário.  Consulte a [Visão geral sobre impressão](printing-overview.md) para obter informações adicionais sobre as opções de saída de caminho de impressão e recursos.

<a name="PluginSerializers"></a>

## <a name="plug-in-serializers"></a>Plug-ins serializadores

As <xref:System.Windows.Documents.Serialization> APIs fornecem suporte para serializadores de plug-in e serializadores vinculados que são instalados separadamente do aplicativo, associam em tempo de execução e são acessados <xref:System.Windows.Documents.Serialization.SerializerProvider> usando o mecanismo de descoberta.  Os serializadores de plug-in oferecem benefícios aprimorados para facilitar a implantação e o uso em todo o sistema.  Os serializadores vinculados também podem ser implementados em ambientes de confiança parcial, como [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] em que os plug-ins nos serializadores não são acessíveis.  Os serializadores vinculados, que se baseiam em uma implementação <xref:System.Windows.Documents.Serialization.SerializerWriter> derivada da classe, são compilados e vinculados diretamente ao aplicativo.  Os serializadores de plug-in e serializadores vinculados operam por métodos públicos idênticos e eventos, o que torna mais fácil o uso de um ou ambos os tipos de serializadores no mesmo aplicativo.

Os serializadores de plug-in ajudam os desenvolvedores de aplicativos fornecendo extensibilidade para novos projetos de armazenamento e formatos de arquivo sem a necessidade de código diretamente para cada formato em potencial no momento de build.  Os serializadores de plug-in também beneficiam os desenvolvedores de terceiros, fornecendo um meio padronizado para implantar, instalar e atualizar plug-ins acessíveis pelo sistema para formatos de arquivo personalizados ou proprietários.

### <a name="using-a-plug-in-serializer"></a>Usando um serializador de plug-in

Os serializadores de plug-in são simples de usar.  A <xref:System.Windows.Documents.Serialization.SerializerProvider> classe enumera um <xref:System.Windows.Documents.Serialization.SerializerDescriptor> objeto para cada plug-in instalado no sistema.  A <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A> Propriedade filtra os plug-ins instalados com base na configuração atual e verifica se o serializador pode ser carregado e usado pelo aplicativo.  O <xref:System.Windows.Documents.Serialization.SerializerDescriptor> também fornece outras propriedades, <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A> como e <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>, que o aplicativo pode usar para solicitar que o usuário selecione um serializador para um formato de saída disponível.  Um serializador de plug-in padrão para XPS é fornecido com .NET Framework e sempre é enumerado.  Depois que o usuário seleciona um formato de saída <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> , o método é usado para <xref:System.Windows.Documents.Serialization.SerializerWriter> criar um para o formato específico.  O elemento de linguagem <xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> o método pode ser chamado para gerar o fluxo de documentos para o armazenamento de dados.

O exemplo a seguir ilustra um aplicativo que usa <xref:System.Windows.Documents.Serialization.SerializerProvider> o método em uma propriedade "PlugInFileFilter".  PlugInFileFilter enumera os plug-ins instalados e cria uma cadeia de caracteres de filtro com as opções de arquivo <xref:Microsoft.Win32.SaveFileDialog>disponíveis para um.

[!code-csharp[DocumentSerialize#DocSerializeFileFilter](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]

Depois que um nome de arquivo de saída tiver sido selecionado pelo usuário, o exemplo a seguir ilustra <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> o uso do método para armazenar um determinado documento em um formato especificado.

[!code-csharp[DocumentSerialize#DocSerializePlugIn](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]

<a name="InstallingPluginSerializers"></a>

### <a name="installing-plug-in-serializers"></a>Instalando serializadores de plug-in

A <xref:System.Windows.Documents.Serialization.SerializerProvider> classe fornece a interface de aplicativo de nível superior para acesso e descoberta do serializador de plug-in.  <xref:System.Windows.Documents.Serialization.SerializerProvider>localiza e fornece ao aplicativo uma lista dos serializadores que estão instalados e acessíveis no sistema.  As especificidades dos serializadores instalados são definidas nas configurações do Registro.  Os serializadores de plug-in podem ser adicionados ao registro usando o <xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A> método; ou se .NET Framework ainda não estiver instalado, o script de instalação de plug-in poderá definir diretamente os valores do registro em si.  O <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A> método pode ser usado para remover um plug-in instalado anteriormente ou as configurações do registro podem ser redefinidas de forma semelhante por um script de desinstalação.

### <a name="creating-a-plug-in-serializer"></a>Criando um serializador de plug-in

Os serializadores de plug-in e os serializadores vinculados usam os mesmos eventos e métodos públicos expostos e, da mesma forma, podem ser projetados para operar de forma síncrona ou assíncrona.  Há três etapas básicas normalmente seguidas para criar um serializador de plug-in:

1. Implementar e depurar o serializador primeiramente como um serializador vinculado.  Criar, inicialmente, o serializador compilado e o vinculado diretamente em um aplicativo de teste fornece acesso completo a pontos de interrupção e outros serviços de depuração úteis para teste.

2. Depois que o serializador é totalmente testado <xref:System.Windows.Documents.Serialization.ISerializerFactory> , uma interface é adicionada para criar um plug-in.  A <xref:System.Windows.Documents.Serialization.ISerializerFactory> interface permite acesso completo a todos os .NET Framework objetos que incluem a árvore lógica <xref:System.Windows.UIElement> , objetos <xref:System.Windows.Documents.IDocumentPaginatorSource>, e <xref:System.Windows.Media.Visual> elementos.  Além <xref:System.Windows.Documents.Serialization.ISerializerFactory> disso, fornece os mesmos métodos síncronos e assíncronos e eventos usados por serializadores vinculados.  Já que documentos grandes podem levar tempo para serem enviados, as operações assíncronas são recomendadas para manter a interação do usuário responsivo e oferecem uma opção "Cancelar" se ocorrer algum problema com o armazenamento de dados.

3. Depois que o serializador de plug-in for criado, um script de instalação será implementado para distribuir e instalar (e desinstalar) o plug-in (veja acima, "[Instalando serializadores de plug-in](#InstallingPluginSerializers)").

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Documents.Serialization>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- [Documentos no WPF](documents-in-wpf.md)
- [Visão Geral da Impressão](printing-overview.md)
- [Especificação de papel XML: visão geral](https://go.microsoft.com/fwlink?LinkID=106246)
