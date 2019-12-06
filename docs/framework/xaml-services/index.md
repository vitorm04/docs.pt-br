---
title: Serviços XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
ms.openlocfilehash: 8e1e8dc9a1410d05c19e4dd1bccb30c65d7c5e66
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837279"
---
# <a name="xaml-services"></a>Serviços XAML
Este tópico descreve os recursos de um conjunto de tecnologias conhecido como .NET Framework serviços XAML. A maioria dos serviços e APIs descritos está localizada no assembly System. XAML, que é um assembly introduzido com o conjunto de .NET Framework 4 de assemblies do .NET Core. Os serviços incluem leitores e gravadores, classes de esquema e suporte a esquemas, fábricas, atribuição de classes, suporte intrínseco à linguagem XAML e outros recursos de linguagem XAML.  
  
## <a name="about-this-documentation"></a>Sobre esta documentação  
 A documentação conceitual para .NET Framework serviços XAML pressupõe que você tenha experiência anterior com a linguagem XAML e como ela pode se aplicar a uma estrutura específica, por exemplo [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ou Windows Workflow Foundation, ou uma área de recursos de tecnologia específica, por exemplo, os recursos de criação de personalização no <xref:Microsoft.Build.Framework.XamlTypes>. Esta documentação não tenta explicar os conceitos básicos do XAML como linguagem de marcação, terminologia de sintaxe XAML ou outro material introdutório. Em vez disso, esta documentação se concentra especificamente em usar os .NET Framework serviços XAML que estão habilitados na biblioteca de assemblies System. XAML. A maioria dessas APIs destina-se a cenários de integração e extensibilidade da linguagem XAML. Isso pode incluir qualquer um dos seguintes:  
  
- Estender os recursos dos leitores XAML base ou gravadores XAML (processando o fluxo do nó XAML diretamente; derivando seu próprio leitor XAML ou gravador XAML).  
  
- Definindo tipos personalizados utilizáveis por XAML que não têm dependências de estrutura específicas e atribuindo os tipos para transmitir suas características de sistema de tipo XAML para .NET Framework serviços XAML.  
  
- Hospedagem de leitores XAML ou gravadores XAML como um componente de um aplicativo, como um designer visual ou editor interativo para fontes de marcação XAML.  
  
- Gravando conversores de valor XAML (extensões de marcação; conversores de tipo para tipos personalizados).  
  
- Definição de um contexto de esquema XAML personalizado (usando técnicas alternativas de carregamento de assembly para fazer backup de fontes de tipo; usando técnicas de pesquisa de tipos conhecidos em vez de sempre refletir assemblies; usando conceitos de assembly carregados que não usam o CLR `AppDomain` e seu modelo de segurança associado).  
  
- Estendendo o sistema de tipos XAML de base.  
  
- Usar as técnicas de `Lookup` ou `Invoker` para influenciar o sistema de tipos XAML e como os backups de tipo são avaliados.  
  
 Se você estiver procurando material introdutório em XAML como uma linguagem, você pode experimentar o [XAML Overview (WPF)](../../desktop-wpf/fundamentals/xaml.md). Esse tópico discute o XAML para um público que é novo para [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] e também para usar a marcação XAML e os recursos de linguagem XAML. Outro documento útil é o material introdutório na [especificação da linguagem XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>.NET Framework os serviços XAML e System. XAML na arquitetura do .NET  
 Nas versões anteriores do Microsoft .NET Framework, o suporte para recursos de linguagem XAML foi implementado por estruturas que se baseiam no Microsoft .NET Framework ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Windows Workflow Foundation e Windows Communication Foundation (WCF)) e, portanto, variados em seu comportamento e na API usada dependendo da estrutura específica que você estava usando. Isso incluiu o analisador XAML e seu mecanismo de criação do grafo de objetos, os intrínsecos da linguagem XAML, o suporte de serialização e assim por diante.  
  
 No .NET Framework 4, .NET Framework serviços XAML e o assembly System. XAML definem grande parte do que é necessário para dar suporte aos recursos da linguagem XAML. Isso inclui classes base para leitores XAML e gravadores XAML. O recurso mais importante adicionado a .NET Framework serviços XAML que não estavam presentes em nenhuma das implementações XAML específicas da estrutura é uma representação do sistema de tipos para XAML. A representação do sistema de tipos apresenta o XAML de forma orientada a objeto, que centraliza os recursos de XAML sem assumir dependências de recursos específicos das estruturas.  
  
 O sistema de tipos XAML não é limitado pelo formulário de marcação ou por especificações de tempo de execução da origem XAML; Nem é limitado por qualquer sistema de tipo de apoio específico. O sistema de tipos XAML inclui representações de objeto para tipos, membros, contextos de esquema XAML, conceitos de nível de XML e outros conceitos de linguagem XAML ou intrínsecos XAML. Usar ou estender o sistema de tipos XAML torna possível derivar de classes como leitores XAML e gravadores XAML e estender a funcionalidade de representações XAML para recursos específicos habilitados por uma estrutura, uma tecnologia ou um aplicativo que consome ou emite XAML. O conceito de um contexto de esquema XAML permite operações de gravação de grafo de objetos práticos da combinação de uma implementação de gravador de objeto XAML, um sistema de tipo de apoio de tecnologia como comunicado por meio de informações de assembly no contexto e o nó XAML original. Para obter mais informações sobre o conceito de esquema XAML. consulte [contexto do esquema XAML padrão e contexto do esquema XAML do WPF](default-xaml-schema-context-and-wpf-xaml-schema-context.md).  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>Fluxos de nó XAML, leitores XAML e gravadores XAML  
 Para entender a função que .NET Framework serviços XAML desempenha na relação entre a linguagem XAML e as tecnologias específicas que usam XAML como linguagem, é útil entender o conceito de um fluxo de nó XAML e como esse conceito forma a API e terminologia. O fluxo do nó XAML é um intermediário conceitual entre uma representação de linguagem XAML e o grafo de objeto que o XAML representa ou define.  
  
- Um leitor XAML é uma entidade que processa XAML em algum formato e produz um fluxo de nó XAML. Na API, um leitor XAML é representado pela classe base <xref:System.Xaml.XamlReader>.  
  
- Um gravador XAML é uma entidade que processa um fluxo de nó XAML e produz algo mais. Na API, um gravador XAML é representado pela classe base <xref:System.Xaml.XamlWriter>.  
  
 Os dois cenários mais comuns que envolvem XAML estão carregando XAML para instanciar um grafo de objeto e salvar um grafo de objeto de um aplicativo ou uma ferramenta e produzir uma representação XAML (normalmente no formulário de marcação salvo como arquivo de texto). O carregamento de XAML e a criação de um grafo de objeto costuma ser referenciado nesta documentação como o caminho de carga. O salvamento ou a serialização de um grafo de objeto existente para XAML costuma ser mencionado nesta documentação como o caminho de salvamento.  
  
 O tipo mais comum de caminho de carga pode ser descrito da seguinte maneira:  
  
- Comece com uma representação XAML, no formato XML codificado em UTF e salvo como um arquivo de texto.  
  
- Carregue esse XAML em <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> é uma subclasse <xref:System.Xaml.XamlReader>.  
  
- O resultado é um fluxo de nó XAML. Você pode acessar nós individuais do fluxo do nó XAML usando <xref:System.Xaml.XamlXmlReader> / API <xref:System.Xaml.XamlReader>. A operação mais típica aqui é avançar pelo fluxo do nó XAML, processando cada nó usando uma metáfora de "registro atual".  
  
- Passe os nós resultantes do fluxo do nó XAML para uma API <xref:System.Xaml.XamlObjectWriter>. <xref:System.Xaml.XamlObjectWriter> é uma subclasse <xref:System.Xaml.XamlWriter>.  
  
- O <xref:System.Xaml.XamlObjectWriter> grava um gráfico de objeto, um objeto por vez, de acordo com o progresso por meio do fluxo do nó XAML de origem. Isso é feito com a assistência de um contexto de esquema XAML e uma implementação que pode acessar os assemblies e tipos de um sistema de apoio e estrutura.  
  
- Chame <xref:System.Xaml.XamlObjectWriter.Result%2A> no final do fluxo do nó XAML para obter o objeto raiz do grafo do objeto.  
  
 O tipo mais comum de caminho de salvamento pode ser descrito da seguinte maneira:  
  
- Comece com o gráfico de objeto de um tempo de execução completo do aplicativo, o conteúdo da interface do usuário e o estado de um tempo de execução ou um segmento menor de uma representação geral do objeto do aplicativo em tempo de execução.  
  
- De um objeto de início lógico, como uma raiz do aplicativo ou raiz do documento, carregue os objetos em <xref:System.Xaml.XamlObjectReader>. <xref:System.Xaml.XamlObjectReader> é uma subclasse <xref:System.Xaml.XamlReader>.  
  
- O resultado é um fluxo de nó XAML. Você pode acessar nós individuais do fluxo do nó XAML usando a API <xref:System.Xaml.XamlObjectReader> e <xref:System.Xaml.XamlReader>. A operação mais típica aqui é avançar pelo fluxo do nó XAML, processando cada nó usando uma metáfora de "registro atual".  
  
- Passe os nós resultantes do fluxo do nó XAML para uma API <xref:System.Xaml.XamlXmlWriter>. <xref:System.Xaml.XamlXmlWriter> é uma subclasse <xref:System.Xaml.XamlWriter>.  
  
- O <xref:System.Xaml.XamlXmlWriter> grava XAML em uma codificação XML UTF. Você pode salvá-lo como um arquivo de texto, como um fluxo ou em outros formulários.  
  
- Chame <xref:System.Xaml.XamlXmlWriter.Flush%2A> para obter a saída final.  
  
 Para obter mais informações sobre conceitos de fluxo do nó XAML, consulte [noções básicas sobre estruturas e conceitos de fluxo do nó XAML](understanding-xaml-node-stream-structures-and-concepts.md).  
  
### <a name="the-xamlservices-class"></a>A classe XamlServices  
 Nem sempre é necessário lidar com um fluxo de nó XAML. Se você quiser um caminho de carga básico ou um caminho de salvamento básico, poderá usar APIs na classe <xref:System.Xaml.XamlServices>.  
  
- Várias assinaturas do <xref:System.Xaml.XamlServices.Load%2A> implementam um caminho de carga. Você pode carregar um arquivo ou fluxo, ou pode carregar um <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> ou <xref:System.Xaml.XamlReader> que encapsulam a entrada XAML carregando com as APIs desse leitor.  
  
- Várias assinaturas do <xref:System.Xaml.XamlServices.Save%2A> salvam um grafo de objeto e produzem a saída como um fluxo, arquivo ou <xref:System.Xml.XmlWriter>instância de <xref:System.IO.TextWriter> /.  
  
- <xref:System.Xaml.XamlServices.Transform%2A> converte XAML vinculando um caminho de carga e um caminho de salvamento como uma única operação. Um contexto de esquema diferente ou um sistema de tipo de backup diferente pode ser usado para <xref:System.Xaml.XamlReader> e <xref:System.Xaml.XamlWriter>, que é o que influencia como o XAML resultante é transformado.  
  
 Para obter mais informações sobre como usar <xref:System.Xaml.XamlServices>, consulte [classe XamlServices e leitura ou gravação básica de XAML](xamlservices-class-and-basic-xaml-reading-or-writing.md).  
  
## <a name="xaml-type-system"></a>Sistema de tipos XAML  
 O sistema de tipos XAML fornece as APIs necessárias para trabalhar com um determinado nó individual de um fluxo de nó XAML.  
  
 <xref:System.Xaml.XamlType> é a representação de um objeto – o que você está processando entre um nó de objeto inicial e o nó de objeto final.  
  
 <xref:System.Xaml.XamlMember> é a representação de um membro de um objeto-o que você está processando entre um nó de membro inicial e o nó de membro final.  
  
 APIs como <xref:System.Xaml.XamlType.GetAllMembers%2A> e <xref:System.Xaml.XamlType.GetMember%2A> e <xref:System.Xaml.XamlMember.DeclaringType%2A> relatam as relações entre um <xref:System.Xaml.XamlType> e o <xref:System.Xaml.XamlMember>.  
  
 O comportamento padrão do sistema de tipos XAML conforme implementado por .NET Framework serviços XAML é baseado no Common Language Runtime (CLR) e na análise estática de tipos CLR em assemblies usando reflexão. Portanto, para um tipo CLR específico, a implementação padrão do sistema de tipos XAML pode expor o esquema XAML desse tipo e seus membros e relatá-lo em termos do sistema de tipos XAML. No sistema de tipos XAML padrão, o conceito de atribuição de tipos é mapeado para herança CLR, e os conceitos de instâncias, tipos de valor e assim por diante também são mapeados para os comportamentos de suporte e recursos do CLR.  
  
## <a name="reference-for-xaml-language-features"></a>Referência para recursos de linguagem XAML  
 Para dar suporte a XAML, .NET Framework serviços XAML fornece implementação específica dos conceitos da linguagem XAML, conforme definido para o namespace XAML da linguagem XAML. Elas são documentadas como páginas de referência específicas. Os recursos de linguagem são documentados a partir da perspectiva de como esses recursos de idioma se comportam quando são processados por um leitor XAML ou um gravador XAML definido por .NET Framework serviços XAML. Para obter mais informações, consulte [XAML namespace (x:) Recursos de linguagem](xaml-namespace-x-language-features.md).
