---
title: Serviços XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
ms.openlocfilehash: c99e44c7d373d050113687753d4f18eca27e0de5
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457404"
---
# <a name="xaml-services"></a>Serviços XAML
Este tópico descreve os recursos de um conjunto de tecnologia serviços conhecidos como XAML do .NET Framework. A maioria dos serviços e APIs descritas estão localizados no assembly System. XAML, que é um assembly introduzido com o conjunto do .NET Framework 4 assemblies do .NET core. Os serviços incluem leitores e gravadores, classes de esquema e o suporte de esquema, fábricas, atribuição de classes, suporte intrínseco de linguagem XAML e outros recursos da linguagem XAML.  
  
## <a name="about-this-documentation"></a>Sobre esta documentação  
 Documentação conceitual para serviços de XAML do .NET Framework pressupõe que você tenha experiência anterior com a linguagem XAML e como ele pode se aplicar a uma estrutura específica, por exemplo [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ou Windows Workflow Foundation, ou um recurso de tecnologia específica área, por exemplo de personalização da compilação recursos em <xref:Microsoft.Build.Framework.XamlTypes>. Esta documentação não tenta explicar os conceitos básicos do XAML como uma linguagem de marcação, terminologia de sintaxe XAML ou outro material introdutório. Em vez disso, essa documentação se concentra em especificamente usando os serviços de XAML do .NET Framework que estão habilitados na biblioteca do assembly System. XAML. A maioria dessas APIs é para cenários de integração de linguagem XAML e extensibilidade. Isso pode incluir qualquer um dos seguintes:  
  
- Estendendo os recursos da base leitores XAML ou gravadores XAML (processando o fluxo do nó XAML diretamente; derivar seu próprio leitor XAML ou o gravador XAML).  
  
- Definindo tipos personalizados utilizável de XAML que não têm dependências de estrutura específica e atribuir os tipos para transmitir seu XAML tipo características do sistema para serviços de XAML do .NET Framework.  
  
- Hospedando os leitores XAML ou gravadores XAML como um componente de um aplicativo, como um designer visual ou um editor interativo para fontes de marcação XAML.  
  
- Gravando conversores de valor XAML (extensões de marcação; conversores de tipo para tipos personalizados).  
  
- Definindo um contexto de esquema XAML personalizado (usando técnicas de carregamento de assemblies alternativas para fontes do tipo de backup; usando técnicas de pesquisa de tipos conhecidos em vez de sempre refletindo assemblies; usando os conceitos de assembly carregado que não usam o CLR `AppDomain` e seu modelo de segurança associadas).  
  
- Estendendo o sistema de tipo base do XAML.  
  
- Usando o `Lookup` ou `Invoker` técnicas para influenciar o XAML de tipo de sistema e como o tipo de pendências são avaliadas.  
  
 Se você estiver procurando por material introdutório em XAML como uma linguagem, você pode tentar [visão geral de XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md). Esse tópico discute XAML para um público que há de novo para [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] e também ao uso de marcação XAML e recursos de linguagem XAML. Outro documento útil é o material introdutório a [especificação da linguagem XAML](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>Serviços XAML do .NET framework e System. XAML na arquitetura do .NET  
 Nas versões anteriores do Microsoft .NET Framework, o suporte para recursos de linguagem XAML foi implementada por estruturas criado no Microsoft .NET Framework ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Windows Workflow Foundation e Windows Communication Foundation (WCF)) e, portanto, variadas em seu comportamento e a API usada, dependendo de qual estrutura específica que você estava usando. Isso incluiu o XAML analisador e seu objeto de gráfico do mecanismo de criação, intrínsecos de linguagem XAML, suporte à serialização e assim por diante.  
  
 No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], serviços de XAML do .NET Framework e o assembly System. XAML definem grande parte do que é necessário para dar suporte a recursos da linguagem XAML. Isso inclui as classes base para leitores XAML e gravadores XAML. O recurso mais importante adicionado para serviços XAML do .NET Framework que não estava presente em qualquer uma das implementações específicas da estrutura XAML é uma representação de sistema de tipo para XAML. A representação de sistema de tipo apresenta a XAML de forma orientada a objeto centraliza nos recursos XAML sem colocar as dependências nos recursos específicos de estruturas.  
  
 O sistema de tipos XAML não é limitado pelo formulário de marcação ou informações específicas de tempo de execução de origem XAML; nem é limitado por qualquer sistema de tipos específicos com suporte. O sistema de tipos XAML inclui representações de objeto para tipos, membros, contextos de esquema XAML, conceitos de nível de XML e outros conceitos da linguagem XAML ou intrínsecos XAML. Usar ou estender o sistema de tipos XAML torna possível derivar de classes, como leitores XAML e gravadores XAML e estender a funcionalidade de representações XAML em recursos específicos, habilitadas por uma estrutura, uma tecnologia ou um aplicativo que consome ou emite XAML. O conceito de um contexto de esquema XAML permite que operações de gravação de gráfico de objeto prático da combinação de uma implementação de gravador de objeto XAML, sistema de tipo de backup de uma tecnologia conforme comunicado por meio das informações de assembly no contexto e o nó XAML código-fonte. Para obter mais informações sobre o conceito de esquema XAML. ver [contexto de esquema de XAML padrão e contexto de esquema XAML WPF](default-xaml-schema-context-and-wpf-xaml-schema-context.md).  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>Fluxos de nós XAML, leitores de XAML e gravadores XAML  
 Para entender a função Serviços de XAML do .NET Framework na relação entre a linguagem XAML e tecnologias específicas que usam XAML como uma linguagem, é útil entender o conceito de um fluxo do nó XAML e como a API de formas desse conceito e terminologia. O fluxo do nó XAML é um intermediário conceitual entre uma representação de linguagem XAML e o grafo de objeto que representa o XAML ou o define.  
  
- Um leitor XAML é uma entidade que processa XAML de alguma forma e produz um fluxo do nó XAML. Na API, um leitor XAML é representado pela classe base <xref:System.Xaml.XamlReader>.  
  
- Um gravador XAML é uma entidade que processa um fluxo do nó XAML e produz algo diferente. Na API, um gravador XAML é representado pela classe base <xref:System.Xaml.XamlWriter>.  
  
 Os dois cenários mais comuns que envolvem XAML estão carregando XAML para criar uma instância de um gráfico de objeto e salvar um gráfico de objeto de um aplicativo ou uma ferramenta e produzir uma representação de XAML (normalmente na forma de marcação salva como arquivo de texto). Carregar o XAML e criar um gráfico de objeto geralmente é chamado nesta documentação como o caminho de carregamento. Salvar ou serializar um grafo de objeto existente para o XAML é conhecido nesta documentação como salvar caminho.  
  
 O tipo mais comum de caminho de carregamento pode ser descrito da seguinte maneira:  
  
- Começar com uma representação de XAML, em formato XML codificado em UTF- e salvo como um arquivo de texto.  
  
- Carregar esse XAML em <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> é um <xref:System.Xaml.XamlReader> subclasse.  
  
- O resultado é um fluxo do nó XAML. Você pode acessar nós individuais no fluxo de nó XAML usando <xref:System.Xaml.XamlXmlReader>  /  <xref:System.Xaml.XamlReader> API. A operação mais comum aqui é para percorrer o fluxo do nó XAML, processamento de cada nó usando um "registro atual" metáfora.  
  
- Passe os nós resultantes do fluxo de nó XAML para um <xref:System.Xaml.XamlObjectWriter> API. <xref:System.Xaml.XamlObjectWriter> é um <xref:System.Xaml.XamlWriter> subclasse.  
  
- O <xref:System.Xaml.XamlObjectWriter> grava um grafo de objeto, um objeto por vez, de acordo com o andamento por meio do fluxo de nó XAML de origem. Isso é feito com o auxílio de um contexto de esquema XAML e uma implementação que pode acessar os assemblies e tipos de uma estrutura e o sistema de tipo de backup.  
  
- Chamar <xref:System.Xaml.XamlObjectWriter.Result%2A> no final do fluxo de nó XAML para obter o objeto raiz do grafo do objeto.  
  
 O tipo mais comum de caminho de salvamento pode ser descrito da seguinte maneira:  
  
- Comece com o gráfico do objeto de um tempo de execução do aplicativo inteiro, o conteúdo de interface do usuário e estado de um tempo de execução ou um segmento menor de representação do objeto do aplicativo geral em tempo de execução.  
  
- De um objeto lógico de início, como uma raiz do aplicativo ou a raiz do documento, carregar os objetos em <xref:System.Xaml.XamlObjectReader>. <xref:System.Xaml.XamlObjectReader> é um <xref:System.Xaml.XamlReader> subclasse.  
  
- O resultado é um fluxo do nó XAML. Você pode acessar nós individuais no fluxo de nó XAML usando <xref:System.Xaml.XamlObjectReader> e <xref:System.Xaml.XamlReader> API. A operação mais comum aqui é para percorrer o fluxo do nó XAML, processamento de cada nó usando um "registro atual" metáfora.  
  
- Passe os nós resultantes do fluxo de nó XAML para um <xref:System.Xaml.XamlXmlWriter> API. <xref:System.Xaml.XamlXmlWriter> é um <xref:System.Xaml.XamlWriter> subclasse.  
  
- O <xref:System.Xaml.XamlXmlWriter> grava XAML em uma UTF XML de codificação. Você pode salvar isso como um arquivo de texto, como um fluxo ou em outros formulários.  
  
- Chamar <xref:System.Xaml.XamlXmlWriter.Flush%2A> para obter a saída final.  
  
 Para obter mais informações sobre os conceitos de fluxo de nó XAML, consulte [Noções básicas sobre XAML Stream estruturas e conceitos nó](understanding-xaml-node-stream-structures-and-concepts.md).  
  
### <a name="the-xamlservices-class"></a>A classe XamlServices  
 Nem sempre é necessário lidar com um fluxo do nó XAML. Se você quiser um caminho de carga básico ou o caminho de salvamento básico, você pode usar APIs no <xref:System.Xaml.XamlServices> classe.  
  
- Várias assinaturas de <xref:System.Xaml.XamlServices.Load%2A> implementar um caminho de carga. Você pode carregar um arquivo ou fluxo ou pode carregar uma <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> ou <xref:System.Xaml.XamlReader> que encapsulam a entrada XAML Carregando com APIs desse leitor.  
  
- Várias assinaturas do <xref:System.Xaml.XamlServices.Save%2A> salvar um gráfico de objeto e produzir uma saída como um fluxo, arquivo, ou <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> instância.  
  
- <xref:System.Xaml.XamlServices.Transform%2A> Converte a XAML vinculando um caminho de carga e de salvar caminho como uma única operação. Um contexto de esquema diferente ou o sistema de tipos de backup diferente pode ser usado para <xref:System.Xaml.XamlReader> e <xref:System.Xaml.XamlWriter>, que é o que influenciará como o XAML resultante é transformado.  
  
 Para obter mais informações sobre como usar <xref:System.Xaml.XamlServices>, consulte [classe de serviços e leitura básicas de XAML ou escrevendo](xamlservices-class-and-basic-xaml-reading-or-writing.md).  
  
## <a name="xaml-type-system"></a>Sistema de tipos XAML  
 O sistema de tipos XAML fornece as APIs que são necessárias para trabalhar com um determinado nó individual de um fluxo de nó XAML.  
  
 <xref:System.Xaml.XamlType> é a representação para um objeto — o que você está processando entre um nó de objeto inicial e um nó de objeto final.  
  
 <xref:System.Xaml.XamlMember> é a representação para um membro de um objeto — o que você está processando entre um nó de membro inicial e um nó de membro final.  
  
 APIs, como <xref:System.Xaml.XamlType.GetAllMembers%2A> e <xref:System.Xaml.XamlType.GetMember%2A> e <xref:System.Xaml.XamlMember.DeclaringType%2A> relatar as relações entre uma <xref:System.Xaml.XamlType> e <xref:System.Xaml.XamlMember>.  
  
 O comportamento padrão do sistema de tipo XAML como implementado pelos serviços de XAML do .NET Framework se baseia no common language runtime (CLR) e análise estática de tipos CLR em assemblies usando reflexão. Portanto, para um tipo específico de CLR, a implementação padrão do sistema de tipo XAML pode expor o esquema XAML de tipo e seus membros e relatá-lo em termos do sistema de tipos XAML. No sistema de tipos XAML padrão, o conceito da atribuição de tipos é mapeado para a herança de CLR e os conceitos de instâncias, tipos de valor e assim por diante também são mapeados para os comportamentos de suporte e recursos do CLR.  
  
## <a name="reference-for-xaml-language-features"></a>Referência para recursos da linguagem XAML  
 Para dar suporte a XAML, serviços de XAML do .NET Framework fornece uma implementação específica de conceitos da linguagem XAML conforme definido para o namespace XAML de linguagem XAML. Essas situações são documentadas como páginas de referência específica. Os recursos de linguagem são documentados da perspectiva de como esses recursos de linguagem se comportam quando eles são processados por um leitor XAML ou gravador XAML que é definido por serviços XAML do .NET Framework. Para obter mais informações, consulte [Namespace de XAML (x) Recursos de linguagem](xaml-namespace-x-language-features.md).
