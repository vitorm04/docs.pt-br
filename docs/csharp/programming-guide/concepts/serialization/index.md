---
title: Serialização (C#)
ms.date: 01/02/2020
ms.openlocfilehash: d914298a370b09307e84c88959542b4823cf37ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167589"
---
# <a name="serialization-c"></a>Serialização (C#)

A serialização é o processo de converter um objeto em um fluxo de bytes para armazenar o objeto ou transmiti-lo para a memória, um banco de dados ou um arquivo. Sua finalidade principal é salvar o estado de um objeto para recriá-lo quando necessário. O processo inverso é chamado desserialização.

## <a name="how-serialization-works"></a>Como a serialização funciona

Esta ilustração mostra o processo geral de serialização:

![Gráfico de serialização](./media/index/serialization-process.gif)

O objeto é serializado para um fluxo que carrega os dados. O fluxo também pode ter informações sobre o tipo do objeto, como sua versão, cultura e nome de montagem. A partir desse fluxo, o objeto pode ser armazenado em um banco de dados, um arquivo ou memória.

### <a name="uses-for-serialization"></a>Usos para serialização

A serialização permite que o desenvolvedor salve o estado de um objeto e o recrie conforme necessário, fornecendo armazenamento de objetos, bem como troca de dados. Através da serialização, um desenvolvedor pode executar ações como:

* Enviando o objeto para um aplicativo remoto usando um serviço web
* Passando um objeto de um domínio para outro
* Passando um objeto através de um firewall como uma seqüência JSON ou XML
* Manutenção de informações de segurança ou específicas do usuário entre aplicativos

## <a name="json-serialization"></a>Serialização JSON

O <xref:System.Text.Json> namespace contém classes para serialização e desserialização de Notação de Objeto JavaScript (JSON). JSON é um padrão aberto que é comumente usado para compartilhar dados na web.

A serialização JSON serializa as propriedades públicas de um objeto em uma seqüência, matriz de byteou ou fluxo que esteja em conformidade com [a especificação RFC 8259 JSON](https://tools.ietf.org/html/rfc8259). Para controlar <xref:System.Text.Json.JsonSerializer> a forma como serializa ou desserializa uma instância da classe:

* Use <xref:System.Text.Json.JsonSerializerOptions> um objeto
* Aplicar atributos <xref:System.Text.Json.Serialization> do namespace a classes ou propriedades
* [Implementar conversores personalizados](../../../../standard/serialization/system-text-json-converters-how-to.md)

## <a name="binary-and-xml-serialization"></a>Serialização XML e binária

O <xref:System.Runtime.Serialization> namespace contém classes para serialização e desserialização binárias e XML.

A serialização binária usa a codificação binária para produzir uma serialização compacta para usos como armazenamento ou fluxos de rede com base em soquete. Na serialização binária, todos os membros, mesmo aqueles que são somente leitura, são serializados e o desempenho é aprimorado.

A serialização XML serializa as propriedades e os campos públicos de um objeto, ou os parâmetros e os valores de retorno de métodos, em um fluxo XML que esteja de acordo com um documento XSD (linguagem de definição de esquema XML) específico. A serialização XML resulta em classes fortemente tipadas com propriedades e campos públicos que são convertidos em XML. <xref:System.Xml.Serialization>contém classes para serialização e desserialização do XML. Aplique atributos a classes e a membros de classe para controlar a maneira como o <xref:System.Xml.Serialization.XmlSerializer> serializa ou desserializa uma instância da classe.

### <a name="making-an-object-serializable"></a>Tornando um objeto serializável

Para serialização binária ou XML, você precisa:

* O objeto a ser serializado
* Um fluxo para conter o objeto serializado
* Um <xref:System.Runtime.Serialization.Formatter?displayProperty=fullName> exemplo

Aplique <xref:System.SerializableAttribute> o atributo a um tipo para indicar que as instâncias do tipo podem ser serializadas. Uma exceção será gerada se você tentar serializar, mas o tipo não terá o atributo <xref:System.SerializableAttribute>.

Para evitar que um campo seja <xref:System.NonSerializedAttribute> serializado, aplique o atributo. Se um campo de um tipo serializável contiver um ponteiro, um identificador ou outra estrutura de dados que é específica de um determinado ambiente e o campo não puder ser reconstituído em um ambiente diferente, será necessário torná-lo não serializável.

Se uma classe serializada contiver referências a objetos de outras classes que estão marcadas como <xref:System.SerializableAttribute>, esses objetos também serão serializados.

### <a name="basic-and-custom-serialization"></a>Serialização básica e personalizada

A serialização binária e XML pode ser realizada de duas maneiras, básica e personalizada.

A serialização básica usa o .NET Framework para serializar o objeto automaticamente. O único requisito é que <xref:System.SerializableAttribute> a classe tenha o atributo aplicado. O <xref:System.NonSerializedAttribute> pode ser usado para impedir a serialização de campos específicos.

Quando você usa a serialização básica, a criação de versão de objetos pode criar problemas. Use a serialização personalizada quando problemas de criação de versão forem importantes. A serialização básica é a maneira mais fácil de executar a serialização, mas ela não fornece muito controle sobre o processo.

Na serialização personalizada, você pode especificar exatamente quais objetos vão ser serializados e como isso será feito. A classe deve ser marcada como <xref:System.SerializableAttribute> e implementar a interface <xref:System.Runtime.Serialization.ISerializable>. Se você quiser que seu objeto seja desserializado de forma personalizada também, use um construtor personalizado.

## <a name="designer-serialization"></a>Serialização de designer

A serialização de designer é um formulário especial de serialização que envolve o tipo de persistência do objeto associado a ferramentas de desenvolvimento. A serialização de designer é o processo de conversão de um grafo do objeto em um arquivo de origem que pode, posteriormente, ser usado para recuperar o grafo do objeto. Um arquivo de origem pode conter código, marcação ou até mesmo informações de tabela do SQL.

## <a name="BKMK_RelatedTopics"></a> Exemplos e tópicos relacionados  

[Visão geral do System.Text.Json](../../../../standard/serialization/system-text-json-overview.md) Mostra como conseguir `System.Text.Json` a biblioteca.

[Como serializar e desserializar JSON em .NET](../../../../standard/serialization/system-text-json-how-to.md).
Mostra como ler e gravar dados de objetos <xref:System.Text.Json.JsonSerializer> de e para JSON usando a classe.

[Passo a passo: mantendo um objeto no Visual Studio (C#)](walkthrough-persisting-an-object-in-visual-studio.md)  
Demonstra como a serialização pode ser usada para manter dados de um objeto entre instâncias, permitindo que você armazene e recupere valores na próxima vez que o objeto for instanciado.

[Como ler dados de objeto de um arquivo XML (C#)](how-to-read-object-data-from-an-xml-file.md)  
Mostra como ler dados de objeto que foram previamente gravados em um arquivo XML usando a classe <xref:System.Xml.Serialization.XmlSerializer>.

[Como gravar dados de objeto em um arquivo XML (C#)](how-to-write-object-data-to-an-xml-file.md)  
Mostra como gravar o objeto de uma classe para um arquivo XML usando a classe <xref:System.Xml.Serialization.XmlSerializer>.
