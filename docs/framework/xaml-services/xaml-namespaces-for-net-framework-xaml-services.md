---
title: Namespaces XAML para serviços XAML do .NET Framework
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: ac6554cbdeb5bc6e0fe7fb96ea95d0143c293d22
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43787240"
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>Namespaces XAML para serviços XAML do .NET Framework
Um namespace XAML é um conceito que se expande na definição de um namespace de XML. Semelhante a um namespace de XML, você pode definir um namespace XAML usando um `xmlns` atributo na marcação. Namespaces XAML também estão representados no fluxo de nó XAML e outras APIs de serviços de XAML. Este tópico define o conceito de namespace XAML e descreve como namespaces XAML podem ser definidas e usadas por contextos de esquema XAML e outros aspectos dos serviços de XAML do .NET Framework.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>Namespace XML e o Namespace XAML  
 Um namespace XAML é um namespace XML especializado, assim como o XAML é uma forma especializada de XML e usa a forma do XML básica para sua marcação. Na marcação, você declarar um namespace XAML e seu mapeamento por meio de um `xmlns` atributo aplicado a um elemento. O `xmlns` declaração pode ser feita ao mesmo elemento declarado no namespace de XAML. Uma declaração de namespace XAML feita a um elemento é válida para esse elemento, todos os atributos desse elemento e todos os filhos desse elemento. Atributos podem usar uma namespaces XAML que não seja o mesmo que o elemento que contém o atributo, desde que o próprio nome de atributo referencia o prefixo como parte de seu nome de atributo na marcação.  
  
 A distinção de um namespace XAML versus um namespace de XML é que um namespace de XML pode ser usado para fazer referência a um esquema, ou pode ser usado para diferenciar simplesmente entidades. Para XAML, os tipos e membros como usado no XAML, por fim, devem ser resolvidos para tipos de suporte e conceitos do esquema XML não se aplicam bem a esse recurso. O namespace XAML contém informações que o contexto do esquema XAML deve ter disponível para realizar esse mapeamento de tipo.  
  
## <a name="xaml-namespace-components"></a>Componentes do Namespace XAML  
 A definição do namespace XAML tem dois componentes: um prefixo e um identificador. Cada um desses componentes estão presentes quando um namespace XAML é declarado na marcação ou definido no sistema de tipos XAML.  
  
 O prefixo pode ser qualquer cadeia de caracteres, conforme permitido pela [Namespaces W3C na especificação XML 1.0](https://go.microsoft.com/fwlink/?LinkID=161735) . Por convenção, os prefixos são cadeias de caracteres normalmente é muito curtas, porque o prefixo é repetido várias vezes em um arquivo de marcação típica. Determinados namespaces XAML que se destinam a ser usado em várias implementações de XAML podem usar prefixos convencionais específicos. Por exemplo, o namespace XAML de linguagem XAML é normalmente mapeado usando o prefixo `x`. Você pode definir um namespace XAML padrão, em que o prefixo não for fornecido na definição, mas é representado como uma cadeia de caracteres vazia se definidas ou consultado by.NET API de serviços de XAML do Framework. Normalmente, o namespace XAML padrão deliberadamente é escolhido para promover uma quantidade maximizada de omitir o prefixo de marcação por uma tecnologia de implementação de XAML e seus cenários e os vocabulários.  
  
 O identificador pode ser qualquer cadeia de caracteres, conforme permitido pela [Namespaces W3C na especificação XML 1.0](https://go.microsoft.com/fwlink/?LinkID=161735). Por convenção, identificadores de namespaces XML ou XAML namespaces são geralmente fornecidos em forma de URI, normalmente como um URI absoluto do protocolo qualificado. Muitas vezes, as informações de versão que define um vocabulário específico do XAML são sugeridas como parte da cadeia de caracteres de caminho. Namespaces XAML adicionar uma convenção de identificador adicional além da convenção de URI de XML. Para namespaces XAML, o identificador se comunica informações que é necessária para um contexto de esquema XAML para resolver os tipos que são especificados como elementos no namespace XAML ou para resolver os atributos para membros.  
  
 Para fins de comunicação de informações para um contexto de esquema XAML, o identificador para um namespace XAML pode ainda ser na forma de URI. No entanto, nesse caso, o URI é declarado também como um identificador correspondente em um assembly específico ou uma lista de assemblies. Isso é feito em assemblies por atribuição o assembly com <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Este método de identificar o namespace XAML e dar suporte a um comportamento de resolução de tipo baseado em CLR no assembly atribuído é compatível com o contexto do esquema XAML padrão nos serviços de XAML do .NET Framework. De modo geral, essa convenção pode ser usada para casos em que o contexto do esquema XAML incorpora o CLR ou baseia-se o contexto de esquema XAML padrão, é necessário para ler os atributos CLR de assemblies do CLR.  
  
 Namespaces XAML também pode ser identificado por uma convenção que se comunica um namespace CLR e um assembly de definição de tipo. Essa convenção é usada em casos onde não <xref:System.Windows.Markup.XmlnsDefinitionAttribute> atribuição existe em assemblies que contêm tipos. Essa convenção é potencialmente mais complexa do que a convenção URI e também tem o potencial de ambiguidade e eliminação de duplicação, pois há várias maneiras de se referir a um assembly.  
  
 A forma mais básica de um identificador que usa a convenção de namespace e assembly do CLR é da seguinte maneira:  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:` e `; assembly=` são componentes de literais de sintaxe.  
  
 *clrnsName* é o nome de cadeia de caracteres que identifica um namespace CLR. Esse nome de cadeia de caracteres inclui quaisquer caracteres interno de ponto (.) que fornecem dicas sobre o namespace CLR e sua relação com outros namespaces CLR.  
  
 *assemblyShortName* é o nome de cadeia de caracteres de um assembly que define tipos que são úteis em XAML. Os tipos sejam acessados por meio do namespace XAML declarado devem ser definidos pelo assembly e especificamente ser declarados dentro do namespace CLR especificado por *clrnsName*. Esse nome de cadeia de caracteres normalmente é comparável as informações conforme relatado pelo <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>.  
  
 Uma definição mais completa da convenção de namespace e assembly do CLR é da seguinte maneira:  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyName*  
  
 *assemblyName* representa qualquer cadeia de caracteres que é permitida como um <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> entrada. Essa cadeia de caracteres pode incluir a cultura, chave pública ou informações de versão (definições desses conceitos são definidas no tópico de referência para <xref:System.Reflection.Assembly>). COFF formato e a evidência (conforme usado por outras sobrecargas do <xref:System.Reflection.Assembly.Load%2A>) não são relevantes para o assembly XAML ao carregar finalidades; todas as informações de carga devem ser apresentadas como uma cadeia de caracteres.  
  
 Especificando uma chave pública para o assembly é uma técnica útil para segurança XAML ou para remover a ambiguidade possíveis que pode existir se os assemblies são carregados por nome simples ou existirem previamente em um domínio de aplicativo ou de cache. Para obter mais informações, consulte [considerações sobre segurança de XAML](../../../docs/framework/xaml-services/xaml-security-considerations.md).  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>Declarações de Namespace XAML em que a API de serviços XAML  
 Na API de serviços de XAML, uma declaração de namespace XAML é representada por um <xref:System.Xaml.NamespaceDeclaration> objeto. Se você está declarando um namespace XAML no código, você chama o <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> construtor. O `ns` e `prefix` são especificados como cadeias de caracteres e a entrada para fornecer para esses parâmetros corresponde à definição de identificador de namespace XAML e o prefixo de namespace XAML conforme fornecido anteriormente neste tópico.  
  
 Se você está examinando as informações de namespace XAML como parte de um fluxo do nó XAML ou por meio de outro acesso para o sistema de tipos XAML <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> relata o identificador de namespace XAML, e <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> relata o prefixo de namespace XAML.  
  
 Em um fluxo de nó XAML, as informações do namespace XAML podem aparecer como um nó XAML que precede a entidade à qual se aplica. Isso inclui os casos em que as informações do namespace XAML precede o `StartObject` do elemento raiz XAML. Para obter mais informações, consulte [Noções básicas sobre XAML Stream estruturas e conceitos nó](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
 Para muitos cenários que usam a API de serviços XAML do .NET Framework, pelo menos uma declaração de namespace XAML deve existir e a declaração deve conter ou fazem referência a informações que é necessário para um contexto de esquema XAML. Os namespaces XAML deve especificar assemblies para ser carregado ou ajudar a resolver tipos específicos dentro de namespaces e assemblies que já foram carregados ou conhecidos pelo contexto de esquema de XAML.  
  
 Para gerar um fluxo do nó XAML, as informações de tipo XAML devem estar disponíveis, por meio do contexto de esquema XAML. As informações de tipo XAML não podem ser determinadas sem primeiro determinando o namespace XAML relevante para cada nó criar. Neste ponto, não há instâncias de tipos são criadas, ainda, mas talvez seja necessário o contexto do esquema XAML pesquisar informações de definição de assembly e tipo subjacente. Por exemplo, para processar a marcação `<Party><PartyFavor/></Party>`, o contexto do esquema XAML deve ser capaz de determinar o nome e tipo dos `ContentProperty` dos `Party`e, portanto, também deve saber as informações de namespace XAML para `Party` e `PartyFavor`. No caso do contexto do esquema XAML padrão, a reflexão estática relata muitas das informações de sistema tipo XAML que é necessário para gerar nós de tipo XAML no fluxo de nó.  
  
 Para gerar um gráfico de objeto de um fluxo de nó XAML, as declarações de namespace XAML devem existir para cada prefixo XAML usado na marcação original e gravado no fluxo de nó XAML. Neste ponto, instâncias estão sendo criadas e comportamento de mapeamento de tipo true ocorre.  
  
 Se você precisar preencher previamente as informações de namespace XAML, em casos em que você pretende que o contexto do esquema XAML para usar o namespace de XAML não está definido na marcação, uma técnica que você pode usar é declarar declarações de namespace XML no <xref:System.Xml.XmlParserContext> para um <xref:System.Xml.XmlReader>. Em seguida, usá-lo <xref:System.Xml.XmlReader> como entrada para um construtor de leitor XAML ou <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>.  
  
 Outra API que são relevantes para serviços XAML do .NET Framework de tratamento de namespace XAML são os atributos <xref:System.Windows.Markup.XmlnsDefinitionAttribute> e <xref:System.Windows.Markup.XmlnsPrefixAttribute>. Esses atributos se aplicam a assemblies. <xref:System.Windows.Markup.XmlnsDefinitionAttribute> é usado por um contexto de esquema XAML para interpretar qualquer declaração de namespace XAML que inclui um URI. <xref:System.Windows.Markup.XmlnsPrefixAttribute> é usado por ferramentas de emissão de XAML para que um namespace XAML específico pode ser serializado com um prefixo previsível. Para obter mais informações, consulte [XAML-Related atributos de CLR para tipos personalizados e bibliotecas](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="see-also"></a>Consulte também  
 [Noções básicas sobre estruturas e conceitos do fluxo de nó XAML](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)
