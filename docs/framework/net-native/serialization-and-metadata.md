---
title: Serialização e metadados
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
ms.openlocfilehash: cc9adf0e6627ef3190e74fea5d4f0f3afd581811
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389230"
---
# <a name="serialization-and-metadata"></a>Serialização e metadados

Se seu aplicativo serializa ou desserializa objetos, talvez seja necessário adicionar entradas aos seus arquivos de diretivas de runtime (.rd.xml) para garantir que os metadados necessários estejam presentes no runtime. Há duas categorias de serializadores e cada uma necessita de um tratamento diferente no arquivo de diretivas de runtime:  
  
- Serializadores de terceiros baseados em reflexão. Eles necessitam de modificações no arquivo de diretivas de runtime e são discutidos na próxima seção.  
  
- Serializadores não baseados em reflexão encontrados na biblioteca de classes .NET Framework. Eles podem necessitar de modificações no arquivo de diretivas de runtime e são discutidos na seção [Serializadores da Microsoft](#Microsoft).  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a>Serializadores de terceiros

 Serializadores de terceiros, incluindo o Newtonsoft.JSON, normalmente são baseadas em reflexão. Dado um BLOB (objeto binário grande) de dados serializados, os campos nos dados são atribuídos a um tipo concreto examinando os campos do tipo de destino por nome. No mínimo, usar essas bibliotecas causa exceções [MissingMetadataException](missingmetadataexception-class-net-native.md) para cada objeto <xref:System.Type> que você tentar serializar ou desserializar em uma coleção `List<Type>`.  
  
 A maneira mais fácil para solucionar problemas causados pela falta de metadados para esses serializadores é coletar tipos que serão usados na serialização de um único namespace (como `App.Models`) e aplicar uma diretiva de metadados `Serialize` a ele:  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 Para obter informações sobre a sintaxe usada no exemplo, consulte [ \<Namespace> Element](namespace-element-net-native.md).  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a>Serializadores da Microsoft

 Embora as classes <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> e <xref:System.Xml.Serialization.XmlSerializer> não dependam de reflexão, elas necessitam que o código seja gerado com base no objeto a ser serializado ou desserializado. Os construtores sobrecarregados para cada serializador incluem um parâmetro <xref:System.Type> que especifica o tipo a ser serializado ou desserializado. A maneira como este tipo é especificado no código define a ação que deve ser tomada, conforme discutido nas duas próximas seções.  
  
### <a name="typeof-used-in-the-constructor"></a>typeof usado no construtor

 Se você chamar um construtor dessas classes de serialização e incluir o [operador tipo](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) C# na chamada do método, você não precisa fazer nenhum **trabalho adicional**. Por exemplo, em cada uma das seguintes chamadas para um construtor de classe de serialização, a palavra-chave `typeof` é usada como parte da expressão passada para o construtor.  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 O compilador .NET Native manuseará automaticamente esse código.  
  
### <a name="typeof-used-outside-the-constructor"></a>typeof usado fora do construtor

 Se você chamar um construtor dessas classes de serialização e usar o [operador tipo](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) <xref:System.Type> C# fora da expressão fornecida ao parâmetro do construtor, como no código a seguir, o compilador .NET Native não poderá resolver o tipo:  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 Nesse caso, você deve especificar o tipo do arquivo de diretivas de runtime adicionando uma entrada como esta:  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 Da mesma forma, se você <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29> chamar um construtor <xref:System.Type> como e fornecer uma matriz de objetos adicionais para serializar, como no código a seguir, o compilador Nativo .NET não poderá resolver esses tipos.  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
Adicionar entradas como o seguinte para cada tipo ao arquivo de diretivas de tempo de execução:  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
Para obter informações sobre a sintaxe usada no exemplo, consulte [ \<Tipo> Elemento](type-element-net-native.md).  
  
## <a name="see-also"></a>Confira também

- [Referência do arquivo de configuração das diretivas de runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementos da diretiva de runtime](runtime-directive-elements.md)
- [\<Tipo elemento>](type-element-net-native.md)
- [\<Elemento> de espaço de nome](namespace-element-net-native.md)
