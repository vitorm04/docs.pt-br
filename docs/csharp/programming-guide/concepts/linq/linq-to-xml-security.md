---
title: "Seguran&#231;a LINQ to XML (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: ef2c0dc9-ecf9-4c17-b24e-144184ab725f
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Seguran&#231;a LINQ to XML (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico descreve problemas de segurança associados com o LINQ to XML. Além disso, ele fornece alguma orientação para minimizar a exposição de segurança.  
  
## LINQ to XML visão geral de segurança  
 LINQ to XML destina\-se mais de conveniência que para aplicativos do lado do servidor com requisitos de segurança rigorosas de programação. A maioria dos cenários XML consistem processar documentos XML confiáveis, em vez de processar documentos XML não confiáveis que são carregados em um servidor. O LINQ to XML é otimizado para esses cenários.  
  
 Se você deve processar dados não confiáveis de fontes desconhecidas, a Microsoft recomenda que você use uma instância da <xref:System.Xml.XmlReader> classe que tenha sido configurado para filtrar conhecidos XML ataques de negação de serviço \(DoS\).  
  
 Se você tiver configurado um <xref:System.Xml.XmlReader> para atenuar ataques negação de serviço, você pode usar esse leitor para preencher uma árvore LINQ to XML e ainda aproveitar os aprimoramentos de produtividade do programador do LINQ to XML. Várias técnicas mitigação envolvem criar os leitores que estão configurados para reduzir o problema de segurança e então instanciar uma árvore XML através do leitor configurado.  
  
 XML é intrinsecamente vulnerável a ataques negação de serviço, como documentos são ilimitadas em tamanho, profundidade, tamanho do nome do elemento e muito mais. Independentemente do componente que você usa para processar XML, você sempre deve estar preparado para reciclar o domínio de aplicativo se ele usar recursos em excesso.  
  
## Redução de XML, XSD, XPath e XSLT ataques  
 O LINQ to XML é construído <xref:System.Xml.XmlReader> e <xref:System.Xml.XmlWriter>. LINQ to XML suporta XSD e XPath por meio de métodos de extensão na <xref:System.Xml.Schema?displayProperty=fullName> e <xref:System.Xml.XPath?displayProperty=fullName> namespaces. Usando o <xref:System.Xml.XmlReader>, <xref:System.Xml.XPath.XPathNavigator>, e <xref:System.Xml.XmlWriter> classes em conjunto com o LINQ to XML, você pode chamar XSLT para transformar árvores XML.  
  
 Se você estiver operando em um ambiente menos seguro, há vários problemas de segurança que estão associadas com XML e o uso das classes <xref:System.Xml?displayProperty=fullName>, <xref:System.Xml.Schema?displayProperty=fullName>, <xref:System.Xml.XPath?displayProperty=fullName>, e <xref:System.Xml.Xsl?displayProperty=fullName>. Esses problemas incluem, mas não estão limitados ao seguinte:  
  
-   XSD, XPath e XSLT são linguagens baseadas em cadeia de caracteres na qual você pode especificar as operações que consomem muita memória ou tempo. É responsabilidade de programadores de aplicativos que usem cadeias de caracteres XSD, XPath ou XSLT de fontes não confiáveis para validar que as cadeias de caracteres não são mal\-intencionados, ou monitorar e reduzir a possibilidade que avaliar essas cadeias de caracteres resultará ao consumo de recursos do sistema em excesso.  
  
-   Esquemas XSD \(incluindo esquemas in\-line\) são inerentemente vulneráveis a ataques negação de serviço; Você não deve aceitar esquemas de fontes não confiáveis.  
  
-   XSD e XSLT podem incluir referências a outros arquivos, e essas referências podem resultar em ataques entre zona e entre domínios.  
  
-   Entidades externas nos DTDs podem resultar em ataques entre zona e entre domínios.  
  
-   Os DTDs é vulneráveis a ataques negação de serviço.  
  
-   Documentos XML exclusivamente profundos podem causar negação de problemas de serviço; Você talvez queira limitar a profundidade de documentos XML.  
  
-   Não aceitar componentes de suporte, como <xref:System.Xml.NameTable>, <xref:System.Xml.XmlNamespaceManager>, e <xref:System.Xml.XmlResolver> objetos de assemblies não confiáveis.  
  
-   Ler dados em partes para atenuar grandes ataques do documento.  
  
-   Blocos de script em folhas de estilos XSLT podem expor um número de ataques.  
  
-   Valide cuidadosamente antes de construir expressões XPath dinâmicos.  
  
## LINQ to XML problemas de segurança  
 Os problemas de segurança neste tópico não são apresentados em uma ordem específica. Todos os problemas são importantes e devem ser endereçados conforme apropriados.  
  
 Um ataue de elevação de privilégio fornece um conjunto mal\-intencionado mais controle sobre seu ambiente. Um ataue de elevação de privilégio pode resultar na divulgação de dados, negação de serviço e muito mais.  
  
 Aplicativos não devem revelar dados para usuários que não estão autorizados a ver esses dados.  
  
 Serviço de ataques de negação de fazer com que o analisador XML ou LINQ to XML consome quantidades excessivas de memória ou tempo de CPU. Ataques negação de serviço são considerados menos grave de elevação de privilégio ataques ou divulgação de ataques de dados. No entanto, elas são importantes em um cenário em que um servidor precisa processar documentos XML de fontes não confiáveis.  
  
### Exceções e mensagens de erro podem revelar dados  
 A descrição do erro pode revelar dados, como os dados que estão sendo convertidos, nomes ou detalhes de implementação de arquivos. Mensagens de erro não devem ser expostas a chamadores que não são confiáveis. Você deve capturar todos os erros e relatório de erros com suas próprias mensagens de erro personalizadas.  
  
### Não chamar codeaccesspermissions. Assert em um manipulador de eventos  
 Um assembly pode ter menos ou mais permissões. Um assembly que tem mais permissões tem maior controle sobre o computador e seus ambientes.  
  
 Se o código em um assembly com mais permissões chama <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> em um manipulador de eventos e, em seguida, o XML árvore é passada para um assembly mal\-intencionado que tem permissões restritas, o conjunto mal\-intencionado pode causar um evento a ser gerado. Como o evento executa o código que está no assembly com mais permissões, o conjunto mal\-intencionado então seria operando com privilégios elevados.  
  
 A Microsoft recomenda que você nunca chamar <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> em um manipulador de eventos.  
  
### Os DTDs não serão seguro  
 Entidades nos DTDs não são inerentemente seguras. É possível para um documento XML mal\-intencionado que contém um DTD para fazer com que o analisador use toda a memória e tempo de CPU, causando um ataque de negação de serviço. Portanto, em LINQ to XML, o processamento de DTD é desativado por padrão. Você não deve aceitar os DTDs de fontes não confiáveis.  
  
 Um exemplo de aceitar os DTDs de fontes não confiáveis é um aplicativo Web que permite que os usuários da Web carregar um arquivo XML que referencia um DTD e um arquivo DTD. Após a validação do arquivo, um DTD mal\-intencionado pode executar um ataque de negação de serviço no servidor. Outro exemplo de aceitar os DTDs de fontes não confiáveis é fazer referência a um DTD em um compartilhamento de rede que também permite acesso anônimo de FTP.  
  
### Como evitar a alocação excessiva de Buffer  
 Os desenvolvedores de aplicativos devem estar cientes de que fontes de dados muito grande podem levar a ataques negação de serviço e de esgotamento de recursos.  
  
 Se um usuário mal\-intencionado envia ou carrega um documento XML muito grande, isso pode causar o LINQ to XML consome muitos recursos do sistema. Isso pode constituir um ataque de negação de serviço. Para evitar isso, você pode definir o <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=fullName> propriedade e cria um leitor que é delimitado no tamanho do documento que puder ser carregado. Você usar o leitor para criar a árvore XML.  
  
 Por exemplo, se você souber que o tamanho esperado máximo dos documentos XML provenientes de uma fonte não confiável será ter menos de 50 mil bytes, defina <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=fullName> a 100.000. Isso não impedirá o processamento de documentos XML e, ao mesmo tempo, ele atenuará negação de serviço onde os documentos podem ser carregados que consumiriam grandes quantidades de memória.  
  
### Evite a expansão adicional de entidade  
 Um dos conhecidos ataques de negação de serviço ao usar um DTD é um documento que causa a expansão excessiva de entidade. Para evitar isso, você pode definir o <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=fullName> propriedade e cria um leitor que é delimitado no número de caracteres resultantes de expansão de entidade. Você usar o leitor para criar a árvore XML.  
  
### Limitar a profundidade da hierarquia XML  
 Um possível ataque de negação de serviço é quando um documento é enviado que possui a profundidade excessiva de hierarquia. Para evitar isso, você pode encapsular um <xref:System.Xml.XmlReader> em sua própria classe que a conta profundidade de elementos. Se o tamanho excede um nível razoável pré\-determinado, você pode encerrar o processamento de documento mal\-intencionado.  
  
### Proteger contra não confiável, XmlReader ou implementações de XmlWriter  
 Os administradores devem verificar que alguns externamente fornecer <xref:System.Xml.XmlReader> ou <xref:System.Xml.XmlWriter> implementações ter nomes fortes e foram registradas na configuração do computador. Isso impede que o código mal\-intencionado disfarçado como um leitor ou gravador sejam carregados.  
  
### Liberar periodicamente os objetos que referenciam XName  
 Para proteger contra determinados tipos de ataques, programadores de aplicativo devem liberar todos os objetos que fazem referência a um <xref:System.Xml.Linq.XName> objeto no domínio do aplicativo regularmente.  
  
### Proteger contra nomes aleatórios XML  
 Aplicativos que utilizam dados de fontes não confiáveis devem considerar usando um <xref:System.Xml.XmlReader> que é encapsulado no código personalizado para verificar a possibilidade de nomes aleatórios e XML namespaces. Se tais nomes aleatórios e XML namespaces forem detectados, o aplicativo pode então terminar o processamento de documento mal\-intencionado.  
  
 Você talvez queira limitar o número de nomes em qualquer namespace determinada \(incluindo nomes em nenhum namespace\) a um limite razoável.  
  
### As anotações são acessíveis por componentes de Software que compartilham uma árvore LINQ to XML  
 LINQ to XML poderia ser usado para criar pipelines de processamento em que componentes diferentes do aplicativo carregar, validarem, consultarem, transformam, atualizam em Salvar os dados XML que são passados entre componentes como árvores XML. Isso pode ajudar a otimizar o desempenho, porque a sobrecarga de carregamento e objetos serializar ao texto XML é feita apenas nas extremidades do pipeline. Os desenvolvedores devem estar cientes, no entanto, todas as anotações e manipuladores de eventos criados por um componente são acessíveis a outros componentes. Isso pode criar um número de vulnerabilidades se os componentes têm diferentes níveis de confiança. Para compilar proteger pipelines através de componentes menos confiável, você deve serializar LINQ para objetos XML ao texto XML antes de passar os dados para um componente não confiável.  
  
 Qualquer segurança é fornecida pelo common language runtime \(CLR\). Por exemplo, um componente que não inclui uma classe privada não pode acessar as anotações fechadas pela classe. No entanto, as anotações podem ser excluídas por componentes que não podem lê\-los. Isso pode ser usado como um ataque violação.  
  
## Consulte também  
 [Guia de programação \(LINQ to XML\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)