---
title: "Serializa&#231;&#227;o (c#) | Microsoft Docs"
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
ms.assetid: 704ff2bf-02ab-4fea-94ea-594107825645
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Serializa&#231;&#227;o (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

A serialização é o processo de converter um objeto em um fluxo de bytes para armazenar o objeto ou transmiti\-los na memória, um banco de dados ou um arquivo. Sua finalidade principal é salvar o estado de um objeto para ser capaz de recriá\-lo quando necessário. O processo inverso é chamado desserialização.  
  
## Como a serialização funciona  
 Esta ilustração mostra o processo geral de serialização.  
  
 ![Gráfico de serialização](../../../../csharp/programming-guide/concepts/serialization/media/serialization.png "serialization")  
  
 O objeto é serializado em um fluxo, que transporta não apenas a dados, mas informações sobre o tipo de objeto, como seu nome de versão, cultura e assembly. Desse fluxo, ele pode ser armazenado em um banco de dados, um arquivo ou memória.  
  
### Usos para a serialização  
 Serialização permite que o desenvolvedor salve o estado de um objeto e recrie conforme necessário, fornecendo o armazenamento dos objetos, bem como a troca de dados. Através da serialização, um desenvolvedor pode executar ações como enviar o objeto para um aplicativo remoto por meio de um serviço da Web, passando um objeto de um domínio para outro, passando um objeto através de um firewall como uma cadeia de caracteres XML ou manter a segurança ou informações específicas de usuário entre aplicativos.  
  
### Tornando um objeto serializável  
 Para serializar um objeto, é necessário o objeto a ser serializado, um fluxo para conter o objeto serializado e um <xref:System.Runtime.Serialization.Formatter>.<xref:System.Runtime.Serialization> contém as classes necessárias para serializar e desserializar objetos.  
  
 Aplicar o <xref:System.SerializableAttribute> de atributo para um tipo para indicar que as instâncias desse tipo podem ser serializadas. Um <xref:System.Runtime.Serialization.SerializationException> exceção é lançada se você tentar serializar mas o tipo não tem o <xref:System.SerializableAttribute> atributo.  
  
 Se você não quiser que um campo em sua classe para ser serializável, aplique o <xref:System.NonSerializedAttribute> atributo. Se um campo de um tipo serializável contém um ponteiro, um identificador ou outra estrutura de dados que é específica para um determinado ambiente, e o campo não pode ser reconstituído em um ambiente diferente, convém torná\-lo serializável.  
  
 Se uma classe serializada contiver referências a objetos de outras classes que estão marcadas <xref:System.SerializableAttribute>, os objetos também poderão ser serializados.  
  
## Binário e serialização de XML  
 Binário ou serialização XML pode ser usada. Na serialização binária, todos os membros, mesmo aqueles que são somente leitura, são serializados, e o desempenho é aprimorado. Serialização XML fornece código mais legível, bem como maior flexibilidade de compartilhamento do objeto e uso para fins de interoperabilidade.  
  
### Serialização binária  
 Serialização binária usa a codificação binária para produzir uma serialização compacta para usos, como armazenamento ou fluxos com soquetes de rede.  
  
### Serialização XML  
 Serialização XML serializa os campos públicos e as propriedades de um objeto, ou os parâmetros e valores de retorno de métodos, em um fluxo XML que está de acordo com um documento específico do XML Schema definition language \(XSD\). Serialização XML resulta em classes fortemente tipadas com propriedades públicas e campos que são convertidos em XML.<xref:System.Xml.Serialization> contém as classes necessárias para serializar e desserializar XML.  
  
 Você pode aplicar atributos a classes e membros de classe para controlar a maneira como o <xref:System.Xml.Serialization.XmlSerializer> serializa ou desserializa uma instância da classe.  
  
## Serialização básica e personalizada  
 Serialização pode ser realizada de duas maneiras básicas e personalizadas. Serialização básica usa o .NET Framework para serializar o objeto automaticamente.  
  
### Serialização básica  
 O único requisito na serialização básica é que o objeto tem o <xref:System.SerializableAttribute> atributo aplicado. O <xref:System.NonSerializedAttribute> pode ser usado para manter campos específicos sendo serializados.  
  
 Quando você usa a serialização básica, a versão dos objetos pode criar problemas, caso em que a serialização personalizada pode ser preferível. Serialização básica é a maneira mais fácil de executar serialização, mas ela não fornece muito controle sobre o processo.  
  
### Serialização personalizada  
 Na serialização personalizada, você pode especificar exatamente quais objetos vão ser serializados e como será feito. A classe deve ser marcada como <xref:System.SerializableAttribute> e implementar o <xref:System.Runtime.Serialization.ISerializable> interface.  
  
 Se você quiser que o objeto a ser desserializado de uma maneira personalizada também, você deve usar um construtor personalizado.  
  
## O designer de serialização  
 O designer de serialização é um formulário especial de serialização que envolve o tipo de persistência do objeto geralmente associado a ferramentas de desenvolvimento. O designer de serialização é o processo de converter um objeto gráfico em um arquivo de origem que posteriormente pode ser usado para recuperar o objeto gráfico. Um arquivo de origem pode conter código, marcação ou até mesmo informações de tabela do SQL. Para obter mais informações, consulte [Designer Serialization Overview](../Topic/Designer%20Serialization%20Overview.md).  
  
##  <a name="BKMK_RelatedTopics"></a> Exemplos e tópicos relacionados  
 [Passo a passo: Mantendo um objeto no Visual Studio \(c\#\)](../Topic/Walkthrough:%20Persisting%20an%20Object%20in%20Visual%20Studio%20\(C%23\).md)  
 Demonstra como a serialização pode ser usada para manter dados de um objeto entre instâncias, permitindo que você armazene valores e recuperá\-las na próxima vez que o objeto é instanciado.  
  
 [Como: ler dados de objeto de um arquivo XML \(c\#\)](../Topic/How%20to:%20Read%20Object%20Data%20from%20an%20XML%20File%20\(C%23\).md)  
 Mostra como ler dados de objeto que foram previamente gravados em um arquivo XML usando o <xref:System.Xml.Serialization.XmlSerializer> classe.  
  
 [Como: gravar dados de objeto para um arquivo XML \(c\#\)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 Mostra como escrever o objeto de uma classe para um arquivo XML usando o <xref:System.Xml.Serialization.XmlSerializer> classe.