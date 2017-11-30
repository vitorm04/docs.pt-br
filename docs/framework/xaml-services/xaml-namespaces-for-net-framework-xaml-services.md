---
title: "Namespaces XAML para serviços XAML do .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: e09279209bf3d6925b61d55d6988b5af658f5aab
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>Namespaces XAML para serviços XAML do .NET Framework
Um namespace XAML é um conceito que se expande na definição de um namespace XML. Semelhante a um namespace XML, você pode definir um namespace XAML usando um `xmlns` atributo na marcação. Namespaces XAML também são representados no fluxo do nó XAML e outras APIs de serviços de XAML. Este tópico define o conceito de namespace XAML e descreve como namespaces XAML podem ser definidos e são usados por contextos de esquema XAML e outros aspectos de serviços XAML do .NET Framework.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>Namespace XML e o Namespace do XAML  
 Um namespace XAML é um namespace XML especializado, como é uma forma especializada de XML e usa o formato XML básico para sua marcação XAML. Na marcação, você declarar um namespace XAML e seu mapeamento por meio de um `xmlns` atributo aplicado a um elemento. O `xmlns` declaração pode ser feita para o mesmo elemento declarada no namespace XAML. Uma declaração de namespace XAML feita a um elemento é válida para esse elemento, todos os atributos desse elemento e todos os filhos desse elemento. Atributos podem usar um namespaces XAML que não é o mesmo que o elemento que contém o atributo, desde que o nome do atributo referencia o prefixo como parte de seu nome de atributo na marcação.  
  
 A diferença de um namespace XAML versus um namespace de XML é que um namespace XML pode ser usado para fazer referência a um esquema, ou pode ser usado para diferenciar simplesmente entidades. Para XAML, os tipos e membros como usado no XAML, por fim, devem ser resolvidos para tipos de backup e conceitos do esquema XML não se aplicam a esse recurso. O namespace XAML contém informações que o contexto do esquema XAML deve ter disponível para realizar o mapeamento de tipo.  
  
## <a name="xaml-namespace-components"></a>Componentes do Namespace XAML  
 A definição do namespace XAML tem dois componentes: um prefixo e um identificador. Cada um desses componentes estão presentes quando um namespace XAML é declarado na marcação ou definido no sistema de tipo de XAML.  
  
 O prefixo pode ser qualquer cadeia de caracteres, conforme permitido pelo [Namespaces W3C na especificação XML 1.0](http://go.microsoft.com/fwlink/?LinkID=161735) . Por convenção, os prefixos são cadeias de caracteres geralmente é muito curtas, pois o prefixo é repetido várias vezes em um arquivo de marcação típico. Determinados XAML namespaces que se destinam a ser usado em várias implementações de XAML usar prefixos de convencionais específicos. Por exemplo, o namespace XAML de linguagem XAML é normalmente mapeado usando o prefixo `x`. Você pode definir um namespace XAML padrão, onde o prefixo não estiver especificado na definição de, mas é representado como uma cadeia de caracteres vazia se definido ou consultado by.NET API de serviços do Framework XAML. Normalmente, o namespace XAML padrão é deliberadamente escolhido para promover uma quantidade maximizada de omitindo o prefixo de marcação por uma tecnologia de implementação de XAML e cenários e vocabulários.  
  
 O identificador pode ser qualquer cadeia de caracteres, conforme permitido pelo [Namespaces W3C na especificação XML 1.0](http://go.microsoft.com/fwlink/?LinkID=161735). Por convenção, identificadores de namespaces XML ou namespaces XAML geralmente são exibidos em forma de URI, normalmente como um URI absoluto do protocolo qualificado. Frequentemente, informações de versão que define um vocabulário específico do XAML são sugeridas como parte da cadeia de caracteres de caminho. Namespaces XAML adicionar uma convenção de identificador adicionais além da convenção de URI de XML. Namespaces XAML, o identificador comunica-se as informações necessárias por um contexto de esquema XAML para resolver os tipos que são especificados como elementos no namespace XAML ou resolver atributos para membros.  
  
 Para fins de comunicação de informações em um contexto de esquema XAML, o identificador para um namespace XAML ainda pode ser na forma de URI. No entanto, nesse caso o URI também está declarado como um identificador correspondente em um assembly específico ou uma lista de assemblies. Isso é feito em assemblies por atribuição o assembly com <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. O contexto do esquema XAML padrão nos serviços de XAML do .NET Framework dá suporte a esse método de identificar o namespace XAML e dando suporte a um comportamento de resolução de tipo baseado em CLR no assembly atribuído. Geralmente, essa convenção pode ser usada para casos em que o contexto do esquema XAML incorpora o CLR ou baseia-se o contexto do esquema XAML padrão, que é necessário para ler os atributos CLR de assemblies do CLR.  
  
 Namespaces XAML também podem ser identificados por uma convenção que se comunica um namespace CLR e um definição de tipo de assembly. Essa convenção é usada em casos onde não <xref:System.Windows.Markup.XmlnsDefinitionAttribute> atribuição existe em assemblies que contêm tipos. Essa convenção é potencialmente mais complexa do que a convenção URI e também tem o potencial de ambiguidade e a eliminação de duplicação, porque há várias maneiras de fazer referência a um assembly.  
  
 A forma mais básica de um identificador que usa a convenção de namespace e assembly CLR é o seguinte:  
  
 `clr-namespace:`*clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:`e `; assembly=` são componentes literal da sintaxe.  
  
 *clrnsName* é o nome de cadeia de caracteres que identifica um namespace CLR. Esse nome de cadeia de caracteres inclui quaisquer caracteres interno de ponto (.) que fornecem dicas sobre o namespace CLR e sua relação com outros namespaces CLR.  
  
 *assemblyShortName* é o nome de cadeia de caracteres de um assembly que define os tipos que são úteis em XAML. Os tipos para ser acessado por meio do namespace XAML declarado devem definidos pelo assembly e especificamente seja declarado no namespace CLR especificado por *clrnsName*. Esse nome de cadeia de caracteres normalmente comparável às informações conforme relatado pelo <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>.  
  
 Uma definição mais completa de convenção de namespace e assembly CLR é o seguinte:  
  
 `clr-namespace:`*clrnsName* `; assembly=` *assemblyName*  
  
 *assemblyName* representa qualquer cadeia de caracteres que é permitida como um <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> entrada. Essa cadeia de caracteres pode incluir a cultura, chave pública ou informações de versão (definições desses conceitos são definidas no tópico de referência de <xref:System.Reflection.Assembly>). COFF formato e evidência (conforme usado por outras sobrecargas de <xref:System.Reflection.Assembly.Load%2A>) não são relevantes para propósitos de carregamento do assembly XAML todas as informações de carga devem ser apresentadas como uma cadeia de caracteres.  
  
 Especificar uma chave pública para o assembly é uma técnica útil para segurança XAML ou para remover a ambiguidade possíveis que pode existir se assemblies são carregados pelo nome simples ou já existem em um domínio de aplicativo ou de cache. Para obter mais informações, consulte [considerações sobre segurança XAML](../../../docs/framework/xaml-services/xaml-security-considerations.md).  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>Declarações de Namespace XAML nos serviços de XAML API  
 Na API de serviços do XAML, uma declaração de namespace XAML é representada por um <xref:System.Xaml.NamespaceDeclaration> objeto. Se você está declarando um namespace XAML no código, você chama o <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> construtor. O `ns` e `prefix` são especificados como cadeias de caracteres, e a entrada para fornecer esses parâmetros corresponde à definição do identificador do namespace XAML e o prefixo do namespace XAML conforme fornecido anteriormente neste tópico.  
  
 Se você está examinando as informações do namespace XAML como parte de um fluxo do nó XAML ou por meio de outros acesso ao sistema de tipo de XAML, <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> relata o identificador do namespace XAML, e <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> relata o prefixo do namespace XAML.  
  
 Em um fluxo do nó XAML, as informações do namespace XAML podem aparecer como um nó XAML que precede a entidade à qual se aplica. Isso inclui os casos em que as informações do namespace XAML precede o `StartObject` do elemento raiz XAML. Para obter mais informações, consulte [Noções básicas sobre estruturas de fluxo de nó de XAML e conceitos](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
 Para muitos cenários que usam a API de serviços XAML do .NET Framework, pelo menos uma declaração de namespace XAML deve existir e a declaração deve conter ou fazer referência a informações necessárias por um contexto de esquema XAML. Os namespaces XAML deve especificar assemblies para ser carregado ou ajudar na resolução específicos tipos em namespaces e assemblies que já são carregados ou conhecidos pelo contexto de esquema XAML.  
  
 Para gerar um fluxo do nó XAML, informações de tipo XAML devem estar disponíveis, por meio do contexto de esquema XAML. As informações de tipo XAML não podem ser determinadas sem primeiro determinar o namespace XAML relevante para cada nó criar. Neste momento, não há instâncias de tipos são criadas ainda, mas o contexto do esquema XAML pode ser necessário procurar informações de definição de assembly e tipo de backup. Por exemplo, para processar a marcação `<Party><PartyFavor/></Party>`, o contexto do esquema XAML deve ser capaz de determinar o nome e o tipo do `ContentProperty` de `Party`e, portanto, também deve saber as informações do namespace XAML para `Party` e `PartyFavor`. No caso do contexto do esquema padrão XAML, reflexão estática relatórios muito as informações do sistema de tipo XAML é necessário para gerar nós de tipo XAML no fluxo do nó.  
  
 Para gerar um gráfico de objeto de um fluxo do nó XAML, declarações de namespace XAML devem existir para cada prefixo XAML usado na marcação original e registrada no fluxo do nó XAML. Neste ponto, instâncias são criadas e comportamento de mapeamento de tipo true ocorre.  
  
 Se você precisa preencher informações de namespace XAML, nos casos em que você pretende que o contexto do esquema XAML para usar o namespace do XAML não está definido na marcação, uma técnica que você pode usar é declarar declarações de namespace XML no <xref:System.Xml.XmlParserContext> para um <xref:System.Xml.XmlReader>. Em seguida, use <xref:System.Xml.XmlReader> como entrada para um construtor de leitor XAML ou <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>.  
  
 Dois outros API que são relevantes para o namespace XAML tratamento em serviços XAML do .NET Framework são os atributos <xref:System.Windows.Markup.XmlnsDefinitionAttribute> e <xref:System.Windows.Markup.XmlnsPrefixAttribute>. Esses atributos se aplicam a assemblies. <xref:System.Windows.Markup.XmlnsDefinitionAttribute>é usado por um contexto de esquema XAML para interpretar qualquer declaração de namespace XAML que inclui um URI. <xref:System.Windows.Markup.XmlnsPrefixAttribute>é usado pelas ferramentas que emite o XAML para que um determinado namespace XAML pode ser serializado com um prefixo previsível. Para obter mais informações, consulte [XAML-Related CLR atributos para tipos personalizados e bibliotecas](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="see-also"></a>Consulte também  
 [Noções básicas sobre estruturas e conceitos do fluxo de nó XAML](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)
