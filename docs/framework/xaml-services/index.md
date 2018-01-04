---
title: "Serviços XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
caps.latest.revision: "13"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 458b4c94d26b7bc083c5d31fcbccf05b42bba52e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-services"></a>Serviços XAML
Este tópico descreve os recursos de um conjunto de tecnologia serviços conhecidos como XAML do .NET Framework. A maioria dos serviços e APIs descritos estão localizados no assembly System. XAML, que é um assembly introduzido com o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] conjunto de assemblies de núcleo do .NET. Os serviços incluem leitores e gravadores, classes de esquema e suporte a esquema, fábricas, atribuição de classes, suporte intrínseco de linguagem XAML e outros recursos de linguagem XAML.  
  
## <a name="about-this-documentation"></a>Sobre esta documentação  
 Documentação conceitual para serviços XAML do .NET Framework pressupõe que você tenha experiência anterior com a linguagem XAML e como ele pode se aplicar a uma estrutura específica, por exemplo [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ou [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)], ou uma tecnologia específica de recurso, para exemplo de recursos de compilação personalizada em <xref:Microsoft.Build.Framework.XamlTypes>. Esta documentação não tenta explicar os conceitos básicos de XAML como uma linguagem de marcação, terminologia de sintaxe XAML ou outro material introdutório. Em vez disso, esta documentação enfoca especificamente usando os serviços de XAML do .NET Framework que estão habilitados na biblioteca do assembly System. XAML. A maioria dessas APIs são cenários de extensibilidade e integração de linguagem XAML. Isso pode incluir qualquer um dos seguintes:  
  
-   Estendendo os recursos dos leitores XAML base ou gravadores XAML (processamento de fluxo do nó XAML diretamente; derivar seu próprio leitor XAML ou gravador XAML).  
  
-   Definindo tipos personalizados XAML utilizável que não têm dependências de estrutura específico e atribuir os tipos para transmitir sua XAML digite características do sistema para serviços XAML do .NET Framework.  
  
-   Hospedando leitores XAML ou gravadores XAML como um componente de um aplicativo, como um visual designer ou editor interativo para fontes de marcação XAML.  
  
-   Gravando conversores de valor XAML (extensões de marcação; conversores de tipo para tipos personalizados).  
  
-   Definindo um contexto de esquema XAML personalizado (usando técnicas de carregamento de assembly alternativas para fontes do tipo de backup; usando técnicas de pesquisa de tipos conhecidos em vez de sempre refletir assemblies; com os conceitos de assembly carregado que não usam o CLR `AppDomain` e seu modelo de segurança associadas).  
  
-   Estendendo o sistema de tipo base do XAML.  
  
-   Usando o `Lookup` ou `Invoker` técnicas para influenciar o XAML digite sistema e como as pendências de tipo são avaliadas.  
  
 Se você estiver procurando material introdutório em XAML, como um idioma, você pode tentar [visão geral de XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md). Esse tópico discute XAML para um público que há de novo para [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] e também para usar a marcação XAML e recursos de linguagem XAML. Outro documento útil é o material introdutório o [especificação da linguagem XAML](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>Serviços XAML do .NET framework e System. XAML na arquitetura do .NET  
 Em versões anteriores do [!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)], suporte para recursos de linguagem XAML foi implementado por estruturas criado em [!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)] ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] e [!INCLUDE[vsindigo](../../../includes/vsindigo-md.md)]) e portanto variadas em seu comportamento e a API usada dependendo de qual estrutura específica que você estava usando. Isso incluído o XAML analisador e seu objeto de gráfico de mecanismo de criação, intrínsecos de linguagem XAML, suporte de serialização e assim por diante.  
  
 Em [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], serviços XAML do .NET Framework e o assembly System. XAML definem muita o que é necessário para dar suporte a recursos de linguagem XAML. Isso inclui classes base para os leitores XAML e gravadores XAML. O recurso mais importante adicionado para serviços XAML do .NET Framework que não estava presente em qualquer uma das implementações de XAML específica da estrutura é uma representação de sistema de tipo para XAML. A representação de tipo de sistema apresenta XAML de forma orientada a objeto centers nos recursos XAML sem colocar as dependências nos recursos específicos de estruturas.  
  
 O sistema de tipo XAML não é limitado pelo formulário de marcação ou especificações de tempo de execução da origem XAML; nem é limitado por qualquer sistema de tipos de backup específico. O sistema de tipo XAML inclui representações de objeto para tipos, membros, contextos de esquema XAML, conceitos de nível de XML e outros conceitos de linguagem XAML ou intrínsecos do XAML. Usando ou estendendo o sistema de tipo XAML, é possível derivar de classes como leitores XAML e autores de XAML, e estender a funcionalidade de representações de XAML em recursos específicos habilitados por uma estrutura, uma tecnologia ou um aplicativo que consome ou emite XAML. O conceito de um contexto de esquema XAML permite operações de gravação de gráfico de objeto prático da combinação de uma implementação de gravador de objeto XAML, sistema de tipos de backup da tecnologia como comunicadas por meio das informações de assembly no contexto e o nó XAML código-fonte. Para obter mais informações sobre o conceito de esquema XAML. consulte [contexto do esquema XML padrão e o contexto do esquema XAML WPF](../../../docs/framework/xaml-services/default-xaml-schema-context-and-wpf-xaml-schema-context.md).  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>Fluxos de nós XAML, XAML leitores e gravadores XAML  
 Para entender a função Serviços de XAML do .NET Framework na relação entre a linguagem XAML e tecnologias específicas que usam XAML como uma linguagem, é útil entender o conceito de um fluxo do nó XAML e como esse conceito formas a API e terminologia. O fluxo do nó XAML é um intermediário conceitual entre uma representação de linguagem XAML e o gráfico de objeto que representa o XAML ou o define.  
  
-   Um leitor XAML é uma entidade que processa XAML de alguma forma e produz um fluxo do nó XAML. Na API, um leitor XAML é representado pela classe base <xref:System.Xaml.XamlReader>.  
  
-   Um gravador XAML é uma entidade que processa um fluxo do nó XAML e gera outra coisa. Na API, um gravador XAML é representado pela classe base <xref:System.Xaml.XamlWriter>.  
  
 Os dois cenários mais comuns que envolvem XAML são carregamento XAML para criar uma instância de um gráfico de objeto e salvar um gráfico de objeto de um aplicativo ou a ferramenta e gera uma representação de XAML (normalmente na forma de marcação salva como arquivo de texto). Carregamento XAML e criar um gráfico de objeto geralmente é conhecido nesta documentação como o caminho de carga. Salvar ou serializar um gráfico de objeto existente para XAML é geralmente conhecido nesta documentação como salvar caminho.  
  
 O tipo mais comum de carga de caminho pode ser descrito como segue:  
  
-   Começar com uma representação de XAML, no formato XML codificado em UTF e salvo como um arquivo de texto.  
  
-   Carregar esse XAML em <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader>é um <xref:System.Xaml.XamlReader> subclasse.  
  
-   O resultado é um fluxo do nó XAML. Você pode acessar nós individuais do XAML nó fluxo usando <xref:System.Xaml.XamlXmlReader>  /  <xref:System.Xaml.XamlReader> API. É aqui a operação mais comum para percorrer o fluxo do nó XAML, processamento de cada nó usando um "registro atual" metáfora.  
  
-   Passe os nós resultantes do fluxo do nó XAML para um <xref:System.Xaml.XamlObjectWriter> API. <xref:System.Xaml.XamlObjectWriter>é um <xref:System.Xaml.XamlWriter> subclasse.  
  
-   O <xref:System.Xaml.XamlObjectWriter> grava um gráfico de objeto, um objeto ao mesmo tempo, de acordo com o andamento por meio do fluxo de nó XAML de origem. Isso é feito com a Ajuda de um contexto de esquema XAML e uma implementação que pode acessar os assemblies e tipos de um sistema de tipos de backup e do framework.  
  
-   Chamar <xref:System.Xaml.XamlObjectWriter.Result%2A> no final do fluxo do nó XAML para obter o objeto raiz do gráfico do objeto.  
  
 O tipo mais comum de caminho de salvamento pode ser descrito como segue:  
  
-   Inicie com o gráfico de objeto de um tempo de execução do aplicativo inteiro, o conteúdo de interface do usuário e o estado de tempo de execução, ou um segmento menor de representação de objeto do aplicativo geral em tempo de execução.  
  
-   De um objeto de início lógico, como uma raiz do aplicativo ou a raiz do documento, carregue os objetos em <xref:System.Xaml.XamlObjectReader>. <xref:System.Xaml.XamlObjectReader>é um <xref:System.Xaml.XamlReader> subclasse.  
  
-   O resultado é um fluxo do nó XAML. Você pode acessar nós individuais do XAML nó fluxo usando <xref:System.Xaml.XamlObjectReader> e <xref:System.Xaml.XamlReader> API. É aqui a operação mais comum para percorrer o fluxo do nó XAML, processamento de cada nó usando um "registro atual" metáfora.  
  
-   Passe os nós resultantes do fluxo do nó XAML para um <xref:System.Xaml.XamlXmlWriter> API. <xref:System.Xaml.XamlXmlWriter>é um <xref:System.Xaml.XamlWriter> subclasse.  
  
-   O <xref:System.Xaml.XamlXmlWriter> grava o XAML em um XML UTF codificação. Você pode salvar isso como um arquivo de texto, como um fluxo ou em outros formatos.  
  
-   Chamar <xref:System.Xaml.XamlXmlWriter.Flush%2A> para obter a saída final.  
  
 Para obter mais informações sobre conceitos de fluxo do nó XAML, consulte [Noções básicas sobre estruturas de fluxo de nó de XAML e conceitos](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
### <a name="the-xamlservices-class"></a>A classe XamlServices  
 Nem sempre é necessário lidar com um fluxo do nó XAML. Se você quiser um caminho de carga básica ou caminho de salvamento básico, você pode usar APIs no <xref:System.Xaml.XamlServices> classe.  
  
-   Várias assinaturas de <xref:System.Xaml.XamlServices.Load%2A> implementar um caminho de carga. Você pode carregar um arquivo ou fluxo ou pode carregar um <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> ou <xref:System.Xaml.XamlReader> que encapsular sua entrada XAML Carregando com as APIs do leitor que.  
  
-   Várias assinaturas de <xref:System.Xaml.XamlServices.Save%2A> salvar um gráfico de objeto e produzir uma saída como um fluxo, arquivo, ou <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> instância.  
  
-   <xref:System.Xaml.XamlServices.Transform%2A>Converte o XAML por meio da vinculação de um caminho de carregar e salvar caminho como uma única operação. Um contexto de esquema diferente ou o sistema de tipos diferentes de backup pode ser usado para <xref:System.Xaml.XamlReader> e <xref:System.Xaml.XamlWriter>, que é o que influencia como o XAML resultante é transformado.  
  
 Para obter mais informações sobre como usar <xref:System.Xaml.XamlServices>, consulte [classe de serviços e a leitura de XAML básica ou a gravação](../../../docs/framework/xaml-services/xamlservices-class-and-basic-xaml-reading-or-writing.md).  
  
## <a name="xaml-type-system"></a>Sistema de tipo XAML  
 O sistema de tipo XAML fornece as APIs que são necessárias para trabalhar com um determinado nó individual de um fluxo do nó XAML.  
  
 <xref:System.Xaml.XamlType>é a representação de um objeto - o que você está processando entre um nó de objeto inicial e o objeto nó.  
  
 <xref:System.Xaml.XamlMember>é a representação para um membro de um objeto - o que você está processando entre um nó de membro inicial e o nó de membro final.  
  
 APIs, como <xref:System.Xaml.XamlType.GetAllMembers%2A> e <xref:System.Xaml.XamlType.GetMember%2A> e <xref:System.Xaml.XamlMember.DeclaringType%2A> relatar as relações entre um <xref:System.Xaml.XamlType> e <xref:System.Xaml.XamlMember>.  
  
 O comportamento padrão do sistema de tipo XAML conforme implementado pelos serviços XAML do .NET Framework é baseado no common language runtime (CLR) e de análise estática de tipos CLR em assemblies usando reflexão. Portanto, para um tipo específico de CLR, a implementação padrão do sistema de tipo XAML pode expor o esquema XAML de tipo e seus membros e relatá-lo de acordo com o sistema de tipo XAML. No sistema de tipo de XAML padrão, o conceito de assignability de tipos é mapeado para a herança de CLR e os conceitos de instâncias, tipos de valor e assim por diante também são mapeados para os recursos do CLR e comportamentos de suporte.  
  
## <a name="reference-for-xaml-language-features"></a>Referência de recursos de linguagem XAML  
 Para dar suporte a XAML, serviços XAML do .NET Framework fornece a implementação específica de conceitos de linguagem XAML conforme definido para o namespace XAML de linguagem XAML. Essas situações são documentadas como páginas de referência específica. Os recursos de idioma são documentados da perspectiva de como esses recursos de idioma se comportam quando eles são processados pelo XAML leitor ou gravador XAML que é definido por serviços XAML do .NET Framework. Para obter mais informações, consulte [Namespace XAML (x) Recursos de linguagem](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).
