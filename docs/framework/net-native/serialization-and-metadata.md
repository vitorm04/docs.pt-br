---
title: Serialização e metadados
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c82d32fe5b1e62a19ff5e2920c5943f1303b2d64
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207019"
---
# <a name="serialization-and-metadata"></a>Serialização e metadados
Se seu aplicativo serializa ou desserializa objetos, talvez seja necessário adicionar entradas aos seus arquivos de diretivas de tempo de execução (.rd.xml) para garantir que os metadados necessários estejam presentes no tempo de execução. Há duas categorias de serializadores e cada uma necessita de um tratamento diferente no arquivo de diretivas de tempo de execução:  
  
-   Serializadores de terceiros baseados em reflexão. Eles necessitam de modificações no arquivo de diretivas de tempo de execução e são discutidos na próxima seção.  
  
-   Serializadores não baseados em reflexão localizados na Biblioteca de Classes do .NET Framework. Eles podem necessitar de modificações no arquivo de diretivas de tempo de execução e são discutidos na seção [Serializadores da Microsoft](#Microsoft).  
  
<a name="ThirdParty"></a>   
## <a name="third-party-serializers"></a>Serializadores de terceiros  
 Serializadores de terceiros, incluindo o Newtonsoft.JSON, normalmente são baseadas em reflexão. Dado um BLOB (objeto binário grande) de dados serializados, os campos nos dados são atribuídos a um tipo concreto examinando os campos do tipo de destino por nome. No mínimo, usar essas bibliotecas causa exceções [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) para cada objeto <xref:System.Type> que você tentar serializar ou desserializar em uma coleção `List<Type>`.  
  
 A maneira mais fácil para solucionar problemas causados pela falta de metadados para esses serializadores é coletar tipos que serão usados na serialização de um único namespace (como `App.Models`) e aplicar uma diretiva de metadados `Serialize` a ele:  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 Para obter informações sobre a sintaxe usada no exemplo, consulte [Elemento \<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md).  
  
<a name="Microsoft"></a>   
## <a name="microsoft-serializers"></a>Serializadores da Microsoft  
 Embora as classes <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> e <xref:System.Xml.Serialization.XmlSerializer> não dependam de reflexão, elas necessitam que o código seja gerado com base no objeto a ser serializado ou desserializado. Os construtores sobrecarregados para cada serializador incluem um parâmetro <xref:System.Type> que especifica o tipo a ser serializado ou desserializado. A maneira como este tipo é especificado no código define a ação que deve ser tomada, conforme discutido nas duas próximas seções.  
  
### <a name="typeof-used-in-the-constructor"></a>typeof usado no construtor  
 Se você chamar um construtor dessas classes de serialização e incluir a palavra-chave de C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) na chamada do método, **não será necessário realizar qualquer trabalho adicional**. Por exemplo, em cada uma das seguintes chamadas para um construtor de classe de serialização, a palavra-chave `typeof` é usada como parte da expressão passada para o construtor.  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 O compilador [!INCLUDE[net_native](../../../includes/net-native-md.md)] lida automaticamente com esse código.  
  
### <a name="typeof-used-outside-the-constructor"></a>typeof usado fora do construtor  
 Se você chamar um construtor dessas classes de serialização e usar palavra-chave de C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) fora da expressão fornecida para o parâmetro <xref:System.Type> do construtor, como no código a seguir, o compilador [!INCLUDE[net_native](../../../includes/net-native-md.md)] não poderá resolver o tipo:  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 Nesse caso, você deve especificar o tipo do arquivo de diretivas de tempo de execução adicionando uma entrada como esta:  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 Da mesma forma, se você chamar um construtor como <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> e fornecer uma matriz de objetos <xref:System.Type> adicionais a serem serializados, como no código a seguir, o compilador [!INCLUDE[net_native](../../../includes/net-native-md.md)] não pode resolver esses tipos.  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 Você deve adicionar entradas como mostrado a seguir para cada tipo para o arquivo de diretivas de tempo de execução:  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 Para obter informações sobre a sintaxe usada no exemplo, consulte [Elemento \<Type>](../../../docs/framework/net-native/type-element-net-native.md).  
  
## <a name="see-also"></a>Consulte também

- [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementos da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-elements.md)
- [\<Tipo > elemento](../../../docs/framework/net-native/type-element-net-native.md)
- [Elemento \<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)
