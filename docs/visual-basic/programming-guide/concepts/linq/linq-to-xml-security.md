---
title: "Segurança LINQ to XML (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: d99b4af2-d447-4a3b-991b-6da0231a8637
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 559bf330640840a310ff947cac118953d1df1a13
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-security-visual-basic"></a>Segurança LINQ to XML (Visual Basic)
Este tópico descreve problemas de segurança associadas LINQ to XML. Além disso, fornece alguma orientação para a exposição de segurança de abrandamento.  
  
## <a name="linq-to-xml-security-overview"></a>Visão geral de segurança LINQ to XML  
 LINQ to XML é criado mais para sua conveniência de programação do que para aplicativos do lado com requisitos de segurança estritos. A maioria das situações XML consistem processar documentos XML de confiança, em vez de processar os documentos XML não confiáveis que são carregados em um servidor. LINQ to XML é otimizado para esses cenários.  
  
 Se você deve processar dados não confiáveis de fontes desconhecidas, a Microsoft recomenda que você use uma instância da <xref:System.Xml.XmlReader>classe que tenha sido configurado para filtrar conhecidos XML ataques de negação de serviço (DoS).</xref:System.Xml.XmlReader>  
  
 Se você tiver configurado um <xref:System.Xml.XmlReader>para atenuar ataques negação de serviço, você pode usar esse leitor para preencher uma árvore LINQ to XML e ainda aproveitar os aprimoramentos de produtividade do programador do LINQ to XML.</xref:System.Xml.XmlReader> Várias técnicas mitigação envolvem criar os leitores que são configurados para reduzir a problema de segurança, e então instanciar uma árvore XML através do leitor configurado.  
  
 XML é intrinsecamente vulnerável a ataques de negação de serviço como documentos são ilimitadas em tamanho, a profundidade, o tamanho do nome do elemento, e mais. Independentemente do componente que você usa para processar XML, você sempre deve estar preparado para reciclar o domínio de aplicativo usa recursos excessivos.  
  
## <a name="mitigation-of-xml-xsd-xpath-and-xslt-attacks"></a>Redução de XML, XSD, XPath, e de ataques XSLT  
 O LINQ to XML é construído <xref:System.Xml.XmlReader>e <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader> LINQ to XML suporta XSD e XPath por meio de métodos de extensão na <xref:System.Xml.Schema?displayProperty=fullName>e <xref:System.Xml.XPath?displayProperty=fullName>namespaces.</xref:System.Xml.XPath?displayProperty=fullName> </xref:System.Xml.Schema?displayProperty=fullName> Usando o <xref:System.Xml.XmlReader>, <xref:System.Xml.XPath.XPathNavigator>, e <xref:System.Xml.XmlWriter>classes em conjunto com o LINQ to XML, você pode chamar XSLT para transformar árvores XML.</xref:System.Xml.XmlWriter> </xref:System.Xml.XPath.XPathNavigator> </xref:System.Xml.XmlReader>  
  
 Se você estiver operando em um ambiente menos seguro, há vários problemas de segurança que estão associadas com XML e o uso das classes <xref:System.Xml?displayProperty=fullName>, <xref:System.Xml.Schema?displayProperty=fullName>, <xref:System.Xml.XPath?displayProperty=fullName>e <xref:System.Xml.Xsl?displayProperty=fullName>.</xref:System.Xml.Xsl?displayProperty=fullName> </xref:System.Xml.XPath?displayProperty=fullName> </xref:System.Xml.Schema?displayProperty=fullName> </xref:System.Xml?displayProperty=fullName> Esses problemas incluem, mas não estão limitados a, o seguinte:  
  
-   XSD, XPath, e XSLT são linguagens cadeia de caracteres- baseados em que você pode especificar as operações que consomem muito tempo ou memória. É responsabilidade de programadores do aplicativo que recebem XSD, o XPath, ou cadeias de caracteres XSLT de fontes não confiáveis para validar que as cadeias de caracteres não são mal-intencionados, ou para monitorar e reduzir a possibilidade que avaliar estas cadeias de caracteres resultará ao consumo excessivo de recurso do sistema.  
  
-   Os esquemas XSD (incluindo esquemas in-line) são inerentemente vulneráveis a ataques de negação de serviço; você não deve aceitar esquemas de fontes não confiáveis.  
  
-   XSD e XSLT podem incluir referências a outros arquivos, e essas referências podem levar a ataques entre zona e entre domínios.  
  
-   As entidades externas nos DTDs pode levar a ataques entre zona e entre domínios.  
  
-   Os DTDs é vulnerável a ataques de negação de serviço.  
  
-   Documentos XML exclusivamente profundos podem disparar problemas de negação de serviço; talvez você queira limitar o tamanho dos documentos XML.  
  
-   Não aceitar componentes de suporte, como <xref:System.Xml.NameTable>, <xref:System.Xml.XmlNamespaceManager>, e <xref:System.Xml.XmlResolver>objetos de assemblies não confiáveis.</xref:System.Xml.XmlResolver> </xref:System.Xml.XmlNamespaceManager> </xref:System.Xml.NameTable>  
  
-   Ler dados em partes para atenuar grandes ataques do documento.  
  
-   Blocos de script em folhas de estilos XSLT podem expor um número de ataques.  
  
-   Validar cuidadosamente antes de construir expressões XPath dinâmicos.  
  
## <a name="linq-to-xml-security-issues"></a>Problemas de segurança LINQ to XML  
 Questões de segurança neste tópico não são apresentadas em qualquer ordem específica. Todos os problemas são importantes e devem ser endereçados conforme apropriado.  
  
 Um ataue de elevação de privilégio fornece a um conjunto mal-intencionado mais controle sobre seu ambiente. Um ataue de elevação de privilégio pode levar a divulgação de dados, negação de serviço, e mais.  
  
 Aplicativos não devem revelar dados para os usuários que não estão autorizados consulte os dados.  
  
 Ataques de negação de serviço faz com que o analisador XML ou LINQ to XML consome quantidades de memória excessivas ou processador central - tempo. Ataques de negação de serviço são considerados menos severos da ataques de elevação de privilégio ou de divulgação de ataques de dados. No entanto, são importantes em um cenário onde um servidor precisa processar documentos XML de fontes não confiáveis.  
  
### <a name="exceptions-and-error-messages-might-reveal-data"></a>Exceções e mensagens de erro podem revelar dados  
 A descrição de um erro pode revelar dados, como os dados que estão sendo convertidos, nomes de arquivo, ou detalhes de implementação. Mensagens de erro não devem ser expostos aos chamadores que não são expostos. Devido você capturar erros e erros de relatório com suas próprias mensagens de erro personalizadas.  
  
### <a name="do-not-call-codeaccesspermissionsassert-in-an-event-handler"></a>Não chamar CodeAccessPermissions.Assert em um manipulador de eventos  
 Um assembly pode ter o invés ou mais permissões. Um assembly que tem mais permissões tem maior controle sobre o computador e seus ambientes.  
  
 Se o código em um assembly com mais permissões chama <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>em um manipulador de eventos e, em seguida, o XML árvore é passada para um assembly mal-intencionado que tem permissões restritas, o conjunto mal-intencionado pode causar um evento a ser gerado.</xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> Como o evento executa o código que está no assembly com mais permissões, o conjunto mal-intencionado então seria operando com privilégios elevados.  
  
 A Microsoft recomenda que você nunca chamar <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>em um manipulador de eventos.</xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>  
  
### <a name="dtds-are-not-secure"></a>Os DTDs não é seguro  
 As entidades nos DTDs não são inerentemente seguros. É possível para um documento XML mal-intencionado que contém um DTD para fazer com que o analisador use qualquer memória e processador central - tempo, causando um ataque de negação de serviço. Portanto, em LINQ to XML, o processamento de DTD é desativada por padrão. Você não deve aceitar os DTDs de fontes não confiáveis.  
  
 Um exemplo de aceitar os DTDs de fontes não confiáveis é um aplicativo da Web que permite que os usuários carreguem Web de um arquivo XML que referencia um DTD e um arquivo de DTD. Em cima de validação de arquivo, um DTD mal-intencionado pode executar um ataque de negação de serviço no seu servidor. Um exemplo de aceitar os DTDs de fontes não confiáveis é fazer referência a um DTD em um compartilhamento de rede que também permite acesso de FTP anônimo.  
  
### <a name="avoid-excessive-buffer-allocation"></a>Evite a alocação excessiva de buffer  
 Desenvolvedores de aplicativos devem estar cientes que as fontes de dados muito grandes podem levar a exaustão e a ataques de negação de serviço de recurso.  
  
 Se um usuário mal-intencionado envia ou carregar um documento XML muito grande, pode fazer com que LINQ to XML consome recursos do sistema excessivos. Isso pode constituir um ataque de negação de serviço. Para evitar isso, você pode definir o <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=fullName>propriedade e cria um leitor que é delimitado no tamanho do documento que pode carregar.</xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=fullName> Você usa o leitor para criar a árvore XML.  
  
 Por exemplo, se você souber que o tamanho esperado máximo dos documentos XML provenientes de uma fonte não confiável será ter menos de 50 mil bytes, defina <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=fullName>a 100.000.</xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=fullName> Isso não impedirá seu processamento de documentos XML, e ao mesmo tempo abrandará as ameaças de negação de serviço onde os documentos podem ser carregados que consumiriam grandes quantidades de memória.  
  
### <a name="avoid-excess-entity-expansion"></a>Evite a expansão adicional de entidade  
 Um de ataques de negação de serviço conhecidas quando usar um DTD for um documento que causa a expansão excessiva de entidade. Para evitar isso, você pode definir o <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=fullName>propriedade e cria um leitor que é delimitado no número de caracteres resultantes de expansão de entidade.</xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=fullName> Você usa o leitor para criar a árvore XML.  
  
### <a name="limit-the-depth-of-the-xml-hierarchy"></a>Limitar o tamanho da hierarquia XML  
 Um ataque de negação de serviço é possível quando um documento é enviado que possui a profundidade excessiva a hierarquia. Para evitar isso, você pode encapsular um <xref:System.Xml.XmlReader>em sua própria classe que a conta profundidade de elementos.</xref:System.Xml.XmlReader> Se o tamanho excede um nível razoável pré-determinado, você pode finalizar o processamento de documento mal-intencionado.  
  
### <a name="protect-against-untrusted-xmlreader-or-xmlwriter-implementations"></a>Proteger contra implementações não confiáveis de XmlReader ou de XmlWriter  
 Os administradores devem verificar que alguns externamente fornecer <xref:System.Xml.XmlReader>ou <xref:System.Xml.XmlWriter>implementações ter nomes fortes e foram registradas na configuração do computador.</xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader> Isso evita código mal-intencionado de masquerading como um leitor ou gravador de ser carregado.  
  
### <a name="periodically-free-objects-that-reference-xname"></a>Liberar periodicamente os objetos que referenciam XName  
 Para proteger contra determinados tipos de ataques, programadores de aplicativo devem liberar todos os objetos que fazem referência a um <xref:System.Xml.Linq.XName>objeto no domínio do aplicativo regularmente.</xref:System.Xml.Linq.XName>  
  
### <a name="protect-against-random-xml-names"></a>Proteger contra nomes aleatórios XML  
 Aplicativos que utilizam dados de fontes não confiáveis devem considerar usando um <xref:System.Xml.XmlReader>que é encapsulado no código personalizado para verificar a possibilidade de nomes aleatórios e XML namespaces.</xref:System.Xml.XmlReader> Se tais nomes aleatórios e namespaces XML são detectados, o aplicativo pode então terminar o processamento de documento mal-intencionado.  
  
 Talvez você queira limitar o número de nomes em qualquer namespace determinada (incluindo nomes em qualquer namespace) a um limite razoável.  
  
### <a name="annotations-are-accessible-by-software-components-that-share-a-linq-to-xml-tree"></a>As anotações são acessíveis por componentes de software que compartilham uma árvore LINQ to XML  
 LINQ to XML pode ser usado para criar pipelines de processamento em que os diferentes componentes do aplicativo, carregam valida, consulta, transformações, atualizar, e salvar os dados XML que são passados entre componentes como árvores XML. Isso pode ajudar a otimizar o desempenho, porque a sobrecarga de carregamento e objetos serializar ao texto XML é feita apenas termina de pipeline. Os desenvolvedores devem estar cientes, entretanto, que todas as anotações e manipuladores de eventos criados por um componente são acessíveis a outros componentes. Isso pode criar um número de vulnerabilidades se os componentes têm diferentes níveis de confiança. Para compilar proteger pipelines através de componentes menos confiável, você deve serializar objetos LINQ to XML ao texto XML antes de passar os dados a um componente não confiável.  
  
 Qualquer segurança é fornecida pelo Common Language Runtime (CLR). Por exemplo, um componente que não inclui uma classe privada não pode acessar as anotações fechadas pela classe. No entanto, as anotações podem ser excluídas por componentes que não podem ler os. Isso pode ser usado como um ataque violação.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de programação (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
