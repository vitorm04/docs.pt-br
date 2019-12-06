---
title: Namespaces XAML para serviços XAML do .NET Framework
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: 11bf5d112c64fb0b942decf7635f02b90a98bdeb
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837162"
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>Namespaces XAML para serviços XAML do .NET Framework
Um namespace XAML é um conceito que se expande na definição de um namespace XML. Semelhante a um namespace XML, você pode definir um namespace XAML usando um atributo `xmlns` na marcação. Os namespaces XAML também são representados no fluxo do nó XAML e em outras APIs de serviços XAML. Este tópico define o conceito de namespace XAML e descreve como os namespaces XAML podem ser definidos e são usados por contextos de esquema XAML e outros aspectos de .NET Framework serviços XAML.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>Namespace XML e namespace XAML  
 Um namespace XAML é um namespace XML especializado, assim como o XAML é uma forma especializada de XML e usa o formulário XML básico para sua marcação. Na marcação, você declara um namespace XAML e seu mapeamento por meio de um atributo `xmlns` aplicado a um elemento. A declaração de `xmlns` pode ser feita no mesmo elemento em que o namespace XAML é declarado. Uma declaração de namespace XAML feita a um elemento é válida para esse elemento, todos os atributos desse elemento e todos os filhos desse elemento. Os atributos podem usar um namespace XAML que não seja o mesmo que o elemento que contém o atributo, desde que o próprio nome do atributo referencie o prefixo como parte de seu nome de atributo na marcação.  
  
 A distinção de um namespace XAML versus um namespace XML é que um namespace XML pode ser usado para fazer referência a um esquema ou pode ser usado para simplesmente diferenciar as entidades. Para o XAML, os tipos e membros como usados em XAML, em última análise, devem ser resolvidos para tipos de backup e os conceitos do esquema XML não se aplicam bem a esse recurso. O namespace XAML contém informações que o contexto de esquema XAML deve ter disponível para executar esse mapeamento de tipo.  
  
## <a name="xaml-namespace-components"></a>Componentes de namespace XAML  
 A definição do namespace XAML tem dois componentes: um prefixo e um identificador. Cada um desses componentes está presente quando um namespace XAML é declarado em marcação ou definido no sistema de tipos XAML.  
  
 O prefixo pode ser qualquer cadeia de caracteres como permitido pelos [namespaces W3C na especificação XML 1,0](https://www.w3.org/TR/REC-xml-names/) . Por convenção, os prefixos normalmente são cadeias de caracteres muito curtas, porque o prefixo é repetido muitas vezes em um arquivo de marcação típico. Determinados namespaces XAML que se destinam a serem usados em várias implementações XAML usam prefixos convencionais específicos. Por exemplo, o XAML Language XAML namespace é normalmente mapeado usando o prefixo `x`. Você pode definir um namespace XAML padrão, em que o prefixo não é fornecido na definição, mas é representado como uma cadeia de caracteres vazia, se definido ou consultado API de serviços XAML do by.NET Framework. Normalmente, o namespace XAML padrão é deliberadamente escolhido para promover uma quantidade maximizada de prefixo, omitindo marcação por uma tecnologia de implementação de XAML e seus cenários e vocabulários.  
  
 O identificador pode ser qualquer cadeia de caracteres como permitido pelos [namespaces W3C na especificação XML 1,0](https://www.w3.org/TR/REC-xml-names/). Por convenção, identificadores para namespaces XML ou namespaces XAML geralmente são fornecidos em formato de URI, normalmente como um URI absoluto qualificado por protocolo. Geralmente, as informações de versão que definem um vocabulário XAML específico são implícitas como parte da cadeia de caracteres do caminho. Os namespaces XAML adicionam uma Convenção de identificador adicional além da Convenção de URI XML. Para namespaces XAML, o identificador comunica as informações necessárias para um contexto de esquema XAML para resolver os tipos especificados como elementos sob esse namespace XAML ou para resolver atributos para membros.  
  
 Para fins de comunicação de informações para um contexto de esquema XAML, o identificador de um namespace XAML ainda pode estar no formato URI. No entanto, nesse caso, o URI também é declarado como um identificador correspondente em um determinado assembly ou lista de assemblies. Isso é feito em assemblies ao atribuir o assembly com <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Esse método de identificar o namespace XAML e dar suporte a um comportamento de resolução de tipo baseado em CLR no assembly atribuído tem suporte do contexto de esquema XAML padrão em .NET Framework serviços XAML. Em geral, essa convenção pode ser usada para casos em que o contexto do esquema XAML incorpora o CLR ou é baseado no contexto do esquema XAML padrão, que é necessário para ler atributos CLR de assemblies CLR.  
  
 Os namespaces XAML também podem ser identificados por uma convenção que comunica um namespace CLR e um assembly de definição de tipo. Essa convenção é usada nos casos em que nenhuma atribuição de <xref:System.Windows.Markup.XmlnsDefinitionAttribute> existe nos assemblies que contêm tipos. Essa convenção é potencialmente mais complexa do que a Convenção de URI e também tem o potencial de ambiguidade e duplicação, pois há várias maneiras de fazer referência a um assembly.  
  
 A forma mais básica de um identificador que usa o namespace CLR e a Convenção de assembly é a seguinte:  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:` e `; assembly=` são componentes literais da sintaxe.  
  
 *clrnsName* é o nome da cadeia de caracteres que identifica um namespace CLR. Esse nome de cadeia de caracteres inclui quaisquer caracteres de ponto internos (.) que fornecem dicas sobre o namespace CLR e sua relação com outros namespaces CLR.  
  
 *AssemblyShortName* é o nome da cadeia de caracteres de um assembly que define os tipos que são úteis em XAML. Os tipos a serem acessados por meio do namespace XAML declarado devem ser definidos pelo assembly e para serem especificamente declarados dentro do namespace CLR especificado por *clrnsName*. Esse nome de cadeia de caracteres normalmente paraleliza as informações conforme relatadas pelo <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>.  
  
 Uma definição mais completa do namespace CLR e da Convenção de assembly é a seguinte:  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyName*  
  
 *AssemblyName* representa qualquer cadeia de caracteres que seja válida como entrada de <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>. Essa cadeia de caracteres pode incluir informações de cultura, chave pública ou versão (definições desses conceitos são definidas no tópico de referência para <xref:System.Reflection.Assembly>). O formato COFF e a evidência (conforme usado por outras sobrecargas de <xref:System.Reflection.Assembly.Load%2A>) não são relevantes para fins de carregamento de assembly XAML; todas as informações de carga devem ser apresentadas como uma cadeia de caracteres.  
  
 A especificação de uma chave pública para o assembly é uma técnica útil para segurança XAML ou para remover uma possível ambiguidade que pode existir se os assemblies forem carregados por nome simples ou se houver um domínio de aplicativo ou cache. Para obter mais informações, consulte [considerações de segurança de XAML](xaml-security-considerations.md).  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>Declarações de namespace XAML na API de serviços XAML  
 Na API de serviços XAML, uma declaração de namespace XAML é representada por um objeto <xref:System.Xaml.NamespaceDeclaration>. Se você estiver declarando um namespace XAML no código, chame o Construtor <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29>. Os parâmetros `ns` e `prefix` são especificados como cadeias de caracteres, e a entrada a ser fornecida para esses parâmetros corresponde à definição do identificador do namespace XAML e do prefixo do namespace XAML, conforme fornecido anteriormente neste tópico.  
  
 Se você estiver examinando as informações do namespace XAML como parte de um fluxo do nó XAML ou por meio de outro acesso ao sistema de tipos XAML, o <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> relatará o identificador do namespace XAML e <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> relatará o prefixo do namespace XAML.  
  
 Em um fluxo de nó XAML, as informações do namespace XAML podem aparecer como um nó XAML que precede a entidade à qual se aplica. Isso inclui casos em que as informações do namespace XAML precede o `StartObject` do elemento raiz XAML. Para obter mais informações, consulte [noções básicas sobre estruturas e conceitos de fluxo do nó XAML](understanding-xaml-node-stream-structures-and-concepts.md).  
  
 Para muitos cenários que usam .NET Framework API de serviços XAML, espera-se que pelo menos uma declaração de namespace XAML exista e a declaração deve conter ou se referir a informações exigidas por um contexto de esquema XAML. Os namespaces XAML devem especificar assemblies a serem carregados ou auxiliar na resolução de tipos específicos em namespaces e assemblies já carregados ou conhecidos pelo contexto de esquema XAML.  
  
 Para gerar um fluxo de nó XAML, as informações do tipo XAML devem estar disponíveis, por meio do contexto do esquema XAML. As informações do tipo XAML não podem ser determinadas sem determinar primeiro o namespace XAML relevante para cada nó a ser criado. Neste ponto, nenhuma instância dos tipos foi criada ainda, mas o contexto do esquema XAML pode precisar pesquisar informações do assembly de definição e do tipo de suporte. Por exemplo, para processar a marcação `<Party><PartyFavor/></Party>`, o contexto do esquema XAML deve ser capaz de determinar o nome e o tipo do `ContentProperty` de `Party`e, portanto, também deve conhecer as informações do namespace XAML para `Party` e `PartyFavor`. No caso do contexto de esquema XAML padrão, a reflexão estática relata grande parte do tipo XAML de informações do sistema que é necessária para gerar nós de tipo XAML no fluxo do nó.  
  
 Para gerar um grafo de objeto de um fluxo de nó XAML, as declarações de namespace XAML devem existir para cada prefixo XAML usado na marcação original e registrados no fluxo do nó XAML. Neste ponto, as instâncias estão sendo criadas e verdadeiro comportamento de mapeamento de tipo ocorre.  
  
 Se você precisar pré-popular informações de namespace XAML, nos casos em que o namespace XAML que você pretende que o contexto de esquema XAML use não esteja definido na marcação, uma técnica que você pode usar é declarar declarações de namespace XML no <xref:System.Xml.XmlParserContext> para um <xref:System.Xml.XmlReader>. Em seguida, use essa <xref:System.Xml.XmlReader> como entrada para um construtor de leitor XAML ou <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>.  
  
 Duas outras APIs que são relevantes para o tratamento de namespace XAML em .NET Framework serviços XAML são os atributos <xref:System.Windows.Markup.XmlnsDefinitionAttribute> e <xref:System.Windows.Markup.XmlnsPrefixAttribute>. Esses atributos se aplicam a assemblies. <xref:System.Windows.Markup.XmlnsDefinitionAttribute> é usado por um contexto de esquema XAML para interpretar qualquer declaração de namespace XAML que inclua um URI. <xref:System.Windows.Markup.XmlnsPrefixAttribute> é usado por ferramentas que emitem XAML para que um namespace XAML específico possa ser serializado com um prefixo previsível. Para obter mais informações, consulte [atributos CLR relacionados a XAML para tipos e bibliotecas personalizadas](xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="see-also"></a>Consulte também

- [Noções básicas sobre estruturas e conceitos do fluxo de nó XAML](understanding-xaml-node-stream-structures-and-concepts.md)
