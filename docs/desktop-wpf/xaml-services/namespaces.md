---
title: XAML Namespaces para serviços .NET XAML
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: 2ae57d08fade85c59fea2a54b653a2f775b57415
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071839"
---
# <a name="xaml-namespaces-for-net-xaml-services"></a>XAML Namespaces para serviços .NET XAML
Um namespace XAML é um conceito que se expande na definição de um namespace XML. Semelhante a um namespace XML, você pode definir `xmlns` um namespace XAML usando um atributo na marcação. Os namespaces XAML também estão representados no fluxo de nós XAML e em outras APIs de Serviços XAML. Este tópico define o conceito de namespace XAML e descreve como os namespaces XAML podem ser definidos e são usados por contextos de esquema XAML e outros aspectos dos Serviços .NET XAML.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>Espaço de nome XML e Espaço de Nome XAML  
 Um namespace XAML é um namespace XML especializado, assim como XAML é uma forma especializada de XML e usa a forma xml básica para sua marcação. Na marcação, você declara um namespace XAML e seu mapeamento através de um `xmlns` atributo aplicado a um elemento. A `xmlns` declaração pode ser feita para o mesmo elemento em que o namespace XAML é declarado. Uma declaração de namespace XAML feita a um elemento é válida para esse elemento, todos os atributos desse elemento, e todos os filhos desse elemento. Os atributos podem usar um namespace XAML que não é o mesmo que o elemento que contém o atributo, desde que o próprio nome do atributo faça referência ao prefixo como parte de seu nome de atributo na marcação.  
  
 A distinção de um namespace XAML versus um namespace XML é que um namespace XML pode ser usado para referenciar um esquema ou simplesmente para diferenciar entidades. Para XAML, os tipos e membros usados no XAML devem finalmente ser resolvidos para tipos de backup, e os conceitos de esquema XML não se aplicam bem a esse recurso. O namespace XAML contém informações que o contexto do esquema XAML deve ter disponível para realizar esse mapeamento de tipo.  
  
## <a name="xaml-namespace-components"></a>Componentes de namespace xaml  
 A definição de namespace XAML tem dois componentes: um prefixo e um identificador. Cada um desses componentes está presente quando um namespace XAML é declarado na marcação, ou definido no sistema do tipo XAML.  
  
 O prefixo pode ser qualquer string permitida pelos [Namespaces W3C na especificação XML 1.0](https://www.w3.org/TR/REC-xml-names/). Por convenção, os prefixos são tipicamente strings curtas, porque o prefixo é repetido muitas vezes em um arquivo de marcação típico. Certos namespaces XAML que devem ser usados em várias implementações XAML usam prefixos convencionais específicos. Por exemplo, o espaço de nome XAML da linguagem `x`XAML é tipicamente mapeado usando o prefixo . Você pode definir um namespace XAML padrão, onde o prefixo não é dado na definição, mas é representado como uma seqüência vazia se definida ou consultada by.NET API de Serviços XAML. Normalmente, o namespace XAML padrão é deliberadamente escolhido para promover uma quantidade maximizada de marcação de prefixo por uma tecnologia de implementação xaml e seus cenários e vocabulários.  
  
 O identificador pode ser qualquer string permitida pelos [Namespaces W3C na especificação XML 1.0](https://www.w3.org/TR/REC-xml-names/). Por convenção, os identificadores para espaços de nome XML ou namespaces XAML são frequentemente dados na forma URI, tipicamente como um URI absoluto qualificado para protocolo. Muitas vezes, as informações da versão que define um vocabulário XAML em particular estão implícitas como parte da seqüência de caminhos. Os namespaces XAML adicionam uma convenção de identificadores adicionais além da convenção XML URI. Para namespaces XAML, o identificador comunica informações necessárias por um contexto de esquema XAML para resolver os tipos especificados como elementos sob esse namespace XAML ou para resolver atributos aos membros.  
  
 Para fins de comunicação de informações a um contexto de esquema XAML, o identificador de um namespace XAML ainda pode estar no formulário URI. No entanto, neste caso, o URI também é declarado como um identificador correspondente em uma assembléia específica ou lista de assembléias. Isso é feito em assembléias atribuindo <xref:System.Windows.Markup.XmlnsDefinitionAttribute>a montagem com . Este método de identificar o namespace XAML e suportar um comportamento de resolução de tipo baseado em CLR no conjunto atribuído é suportado pelo contexto padrão do esquema XAML em Serviços XAML .NET. De forma mais geral, esta convenção pode ser usada para casos em que o contexto do esquema XAML incorpora a CLR ou se baseia no contexto padrão do esquema XAML, que é necessário para ler atributos CLR de assembléias CLR.  
  
 Os namespaces XAML também podem ser identificados por uma convenção que comunica um namespace CLR e um conjunto de definição de tipo. Esta convenção é usada <xref:System.Windows.Markup.XmlnsDefinitionAttribute> nos casos em que não existe atribuição nas assembléias que contêm tipos. Esta convenção é potencialmente mais complexa do que a convenção uri, e também tem o potencial de ambiguidade e duplicação, porque há múltiplas maneiras de se referir a uma assembléia.  
  
 A forma mais básica de um identificador que usa o namespace clr e a convenção de montagem é a seguinte:  
  
 `clr-namespace:clrnsName; assembly=assemblyShortName`
  
 `clr-namespace:`e `; assembly=` são componentes literais da sintaxe.  
  
 *clrnsName* é o nome da seqüência que identifica um namespace CLR. Este nome de seqüência inclui quaisquer caracteres de dot interno (.) que fornecem dicas sobre o namespace clr e sua relação com outros namespaces CLR.
  
 *assemblyShortName* é o nome da seqüência de um conjunto que define tipos que são úteis em XAML. Espera-se que os tipos a serem acessados através do namespace XAML declarado sejam definidos pela montagem e sejam declarados dentro do namespace CLR especificado por *clrnsName*. Este nome de seqüência normalmente <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>faz um paralelo com as informações relatadas por .  
  
 Uma definição mais completa do namespace e da convenção de montagem da CLR é a seguinte:  
  
 `clr-namespace:clrnsName; assembly=assemblyName`
  
 *assemblyName* representa qualquer string que <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> seja legal como entrada. Essa string pode incluir cultura, chave pública ou informações de versão (definições desses conceitos são definidas no tópico de referência para <xref:System.Reflection.Assembly>). O formato e a evidência COFF <xref:System.Reflection.Assembly.Load%2A>(como usado por outras sobrecargas de ) não são relevantes para fins de carregamento de montagem XAML; todas as informações de carga devem ser apresentadas como uma string.  
  
 Especificar uma chave pública para o conjunto é uma técnica útil para a segurança XAML ou para remover possíveis ambiguidades que podem existir se os conjuntos forem carregados por nome simples ou pré-existirem em um cache ou domínio de aplicativo. Para obter mais informações, consulte [Considerações de segurança XAML](security-considerations.md).  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>Declarações de namespace xaml na API de serviços XAML  
 Na API de serviços XAML, uma declaração <xref:System.Xaml.NamespaceDeclaration> de namespace XAML é representada por um objeto. Se você estiver declarando um namespace XAML <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> em código, você chamará o construtor. Os `ns` `prefix` parâmetros e parâmetros são especificados como strings, e a entrada para fornecer esses parâmetros corresponde à definição do identificador de namespace XAML e do prefixo xaml namespace, conforme fornecido anteriormente neste tópico.  
  
 Se você estiver examinando as informações do namespace XAML como parte de um fluxo de <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> nós XAML ou através <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> de outro acesso ao sistema do tipo XAML, informa o identificador de namespace XAML e reporta o prefixo de namespace XAML.  
  
 Em um fluxo de nó XAML, as informações do namespace XAML podem aparecer como um nó XAML que precede a entidade à qual ele se aplica. Isso inclui casos em que as informações de `StartObject` namespace XAML precedem o elemento raiz XAML. Para obter mais informações, consulte [Entendendo estruturas e conceitos de fluxo de nó XAML](understanding-xaml-node-stream-structures-and-concepts.md).  
  
 Para muitos cenários que usam a API de Serviços XAML .NET, espera-se que pelo menos uma declaração de namespace XAML exista, e a declaração deve conter ou se referir às informações exigidas por um contexto de esquema XAML. Os namespaces XAML devem especificar conjuntos a serem carregados ou ajudar a resolver tipos específicos dentro de espaços de nomes e conjuntos que já estão carregados ou conhecidos pelo contexto do esquema XAML.  
  
 Para gerar um fluxo de nó XAML, as informações do tipo XAML devem estar disponíveis, através do contexto do esquema XAML. As informações do tipo XAML não podem ser determinadas sem antes determinar o namespace XAML relevante para cada nó a ser criado. Neste ponto, ainda não foram criadas instâncias de tipos, mas o contexto do esquema XAML pode precisar procurar informações do tipo de montagem e respaldo definidor. Por exemplo, para processar a `<Party><PartyFavor/></Party>`marcação, o contexto do esquema XAML deve ser `ContentProperty` `Party`capaz de determinar o nome e o `Party` tipo `PartyFavor`do de , e, portanto, também deve conhecer as informações de namespace XAML para e . No caso do contexto padrão do esquema XAML, a reflexão estática relata grande parte das informações do sistema do tipo XAML necessárias para gerar nonos do tipo XAML no fluxo de nó.  
  
 Para gerar um gráfico de objeto a partir de um fluxo de nó XAML, as declarações de namespace XAML devem existir para cada prefixo XAML usado na marcação original e gravado no fluxo de nó XAML. Neste ponto, instâncias estão sendo criadas, e ocorre um verdadeiro comportamento de mapeamento de tipos.  
  
 Se você precisar prepreencher informações de namespace XAML, nos casos em que o namespace XAML que você pretende que o contexto do esquema XAML <xref:System.Xml.XmlParserContext> use <xref:System.Xml.XmlReader>não esteja definido na marcação, uma técnica que você pode usar é declarar declarações de namespace XML no para um . Em seguida, use isso <xref:System.Xml.XmlReader> como entrada para <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>um construtor de leitor XAML, ou .  
  
 Duas outras APIs relevantes para o manuseio de namespace XAML <xref:System.Windows.Markup.XmlnsDefinitionAttribute> em <xref:System.Windows.Markup.XmlnsPrefixAttribute>Serviços XAML .NET são os atributos e . Esses atributos se aplicam às assembléias. <xref:System.Windows.Markup.XmlnsDefinitionAttribute>é usado por um contexto de esquema XAML para interpretar qualquer declaração de namespace XAML que inclua um URI. <xref:System.Windows.Markup.XmlnsPrefixAttribute>é usado por ferramentas que emitem XAML para que um espaço de nome XAML em particular possa ser serializado com um prefixo previsível. Para obter mais informações, consulte [Atributos CLR relacionados à XAML para tipos e bibliotecas personalizados](clr-attributes-with-custom-types-and-libraries.md).  
  
## <a name="see-also"></a>Confira também

- [Noções básicas sobre estruturas e conceitos do fluxo de nó XAML](understanding-xaml-node-stream-structures-and-concepts.md)
