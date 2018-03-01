---
title: Substitutos de contrato de dados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data contracts [WCF], surrogates
ms.assetid: 8c31134c-46c5-4ed7-94af-bab0ac0dfce5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f6fcae1989b75a668fd6ff38596b06feca7be9e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="data-contract-surrogates"></a>Substitutos de contrato de dados
O contrato de dados *substituto* é um recurso avançado baseado em modelo de contrato de dados. Esse recurso destina-se a ser usada para personalização de tipo e substituição em situações em que os usuários desejarem alterar como um tipo é serializado, desserializado ou projetado nos metadados. Alguns cenários onde um substituto pode ser usado é quando um contrato de dados não foi especificado para o tipo, campos e propriedades não são marcadas com o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo ou usuários deseja criar dinamicamente as variações de esquema.  
  
 Serialização e desserialização são realizadas com o substituto de contrato de dados ao usar <xref:System.Runtime.Serialization.DataContractSerializer> para converter do .NET Framework para um formato adequado, como XML. Substitutos de contrato de dados também podem ser usado para modificar os metadados exportado para tipos, ao gerar representações de metadados, como documentos de esquema XML (XSD). Após a importação, o código é criado de metadados e o substituto pode ser usado nesse caso, para personalizar o código gerado.  
  
## <a name="how-the-surrogate-works"></a>Como funciona o substituto  
 Um substituto funciona por um tipo de mapeamento (do tipo "original") em outro tipo (do tipo "surrogated"). O exemplo a seguir mostra o tipo original `Inventory` e um novo substituto `InventorySurrogated` tipo. O `Inventory` tipo não é serializável, mas o `InventorySurrogated` é do tipo:  
  
 [!code-csharp[C_IDataContractSurrogate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#1)]  
  
 Como um contrato de dados não foi definido para esta classe, converta a classe para uma classe de substitutos com um contrato de dados. A classe surrogated é mostrada no exemplo a seguir:  
  
 [!code-csharp[C_IDataContractSurrogate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#2)]  
  
## <a name="implementing-the-idatacontractsurrogate"></a>Implementação de IDataContractSurrogate  
 Para usar o substituto de contrato de dados, implemente o <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.  
  
 A seguir está uma visão geral de cada método de <xref:System.Runtime.Serialization.IDataContractSurrogate> com uma possível implementação.  
  
### <a name="getdatacontracttype"></a>GetDataContractType  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> método mapeia um tipo para outro. Este método é necessário para a serialização, desserialização, importação e exportação.  
  
 A primeira tarefa é definir o tipos que serão mapeados para outros tipos. Por exemplo:  
  
 [!code-csharp[C_IDataContractSurrogate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#3)]  
  
-   Na serialização, o mapeamento retornado por este método é usado posteriormente para transformar a instância original para uma instância surrogated chamando o <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> método.  
  
-   Na desserialização, o mapeamento retornado por este método é usado pelo serializador a ser desserializado em uma instância do tipo substituto. Posteriormente, ele chama <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> para transformar a instância surrogated em uma instância do tipo original.  
  
-   Na exportação, o tipo de substitutos retornado por esse método é refletido para obter o contrato de dados a ser usado para a geração de metadados.  
  
-   Na importação, o tipo inicial é alterado para um tipo substituto que é refletido para obter o contrato de dados a ser usado para finalidades como referência de suporte.  
  
 O <xref:System.Type> parâmetro é do tipo do objeto que está sendo serializado desserializado, importado ou exportado. O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> método deve retornar o tipo de entrada se o substituto não lidar com o tipo. Caso contrário, retorna o tipo apropriado de surrogated. Se existem vários tipos de substitutos, vários mapeamentos podem ser definidos nesse método.  
  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> método não é chamado de dados interna primitivos de contrato, como <xref:System.Int32> ou <xref:System.String>. Para outros tipos, como matrizes, tipos definidos pelo usuário e outras estruturas de dados, esse método será chamado para cada tipo.  
  
 No exemplo anterior, o método verifica se o `type` parâmetro e `Inventory` são comparáveis. Se assim, o método mapeia para `InventorySurrogated`. Sempre que uma serialização, desserialização, esquema de importação ou exportação de esquema é chamada, essa função é chamada primeiro para determinar o mapeamento entre tipos.  
  
### <a name="getobjecttoserialize-method"></a>Método GetObjectToSerialize  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> método converte a instância do tipo original para a instância do tipo substituído. O método é necessário para a serialização.  
  
 A próxima etapa é definir o modo como os dados físicos serão mapeados da instância original para o substituto Implementando o <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> método. Por exemplo:  
  
 [!code-csharp[C_IDataContractSurrogate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#4)]  
  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> método é chamado quando um objeto é serializado. Esse método transfere dados do tipo original para os campos do tipo surrogated. Campos podem ser mapeados diretamente para substitutos campos ou manipulações de dados originais podem ser armazenadas em do substituto. Algumas utilizações possíveis incluem: diretamente os campos de mapeamento, executar operações nos dados a ser armazenado nos campos surrogated ou armazenar o XML do tipo original no campo surrogated.  
  
 O `targetType` parâmetro refere-se para o tipo declarado do membro. Esse parâmetro é do tipo surrogated retornado pelo <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> método. O serializador não impõe que o objeto retornado será atribuído a esse tipo. O `obj` parâmetro é o objeto a ser serializado e será convertido em seu substituto se necessário. Esse método deve retornar o objeto de entrada se o surrogated não processa o objeto. Caso contrário, o novo objeto substituto será retornado. O substituto não será chamado se o objeto é nulo. Vários mapeamentos alternativos para instâncias diferentes podem ser definidos dentro desse método.  
  
 Ao criar um <xref:System.Runtime.Serialization.DataContractSerializer>, você pode instruir a preservar referências de objeto. ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Serialização e desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).) Isso é feito definindo o `preserveObjectReferences` parâmetro no construtor para `true`. Nesse caso, o substituto é chamado apenas uma vez para um objeto, desde que todas as serializações subsequentes gravar apenas a referência no fluxo. Se `preserveObjectReferences` é definido como `false`, em seguida, o substituto é chamado sempre que uma instância for encontrada.  
  
 Se o tipo da instância serializada difere do tipo declarado, informações de tipo são gravadas no fluxo, por exemplo, `xsi:type` para permitir que a instância a ser desserializado na outra extremidade. Esse processo ocorre se o objeto é substituído ou não.  
  
 O exemplo anterior converte os dados do `Inventory` de instância `InventorySurrogated`. Ele verifica o tipo do objeto e executa as manipulações necessário para converter para o tipo surrogated. Nesse caso, os campos do `Inventory` classe diretamente são copiadas para o `InventorySurrogated` campos de classe.  
  
### <a name="getdeserializedobject-method"></a>Método GetDeserializedObject  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> método converte a instância do tipo substituído para a instância do tipo original. Ele é necessário para desserialização.  
  
 A próxima tarefa é definir o modo como os dados físicos serão mapeados da instância substituto para o original. Por exemplo:  
  
 [!code-csharp[C_IDataContractSurrogate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#5)]  
  
 Esse método é chamado apenas durante a desserialização de um objeto. Ele fornece o mapeamento de dados inversa para a desserialização do tipo substituto volta para seu tipo original. Como o `GetObjectToSerialize` método, alguns possíveis usos podem ser a troca de dados de campo, executar operações nos dados e armazenar dados XML diretamente. Durante a desserialização, não sempre obter os valores de dados exato do original devido a manipulações na conversão de dados.  
  
 O `targetType` parâmetro refere-se para o tipo declarado do membro. Esse parâmetro é do tipo surrogated retornado pelo `GetDataContractType` método. O `obj` parâmetro faz referência ao objeto que tiver sido desserializado. O objeto pode ser convertido para o tipo original se ele é substituído. Esse método retorna o objeto de entrada se o substituto não processa o objeto. Caso contrário, o objeto desserializado será retornado após a conversão foi concluída. Se existem vários tipos de substitutos, você pode fornecer conversão de dados de substitutos para tipo primário para cada indicando cada tipo e a conversão.  
  
 Ao retornar um objeto, as tabelas internas do objeto são atualizadas com o objeto retornado por este substituto. Todas as referências subsequentes para uma instância obterá a instância surrogated das tabelas do objeto.  
  
 O exemplo anterior converte objetos do tipo `InventorySurrogated` volta para o tipo inicial `Inventory`. Nesse caso, os dados são transferidos diretamente do `InventorySurrogated` para seus campos correspondentes no `Inventory`. Como não há nenhuma manipulações de dados, a cada um dos campos de membro conterá os mesmos valores antes da serialização.  
  
### <a name="getcustomdatatoexport-method"></a>Método GetCustomDataToExport  
 Ao exportar um esquema, o <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A> é opcional. Ele é usado para inserir dados adicionais ou dicas de esquema exportadas. Dados adicionais podem ser inseridos no nível de membro ou tipo. Por exemplo:  
  
 [!code-csharp[C_IDataContractSurrogate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#6)]  
  
 Este método (com duas sobrecargas) permite a inclusão de informações adicionais nos metadados no nível do membro ou tipo. É possível incluir dicas sobre se um membro é público ou privado e comentários que poderiam ser preservados durante a exportação e importação do esquema. Essas informações seriam perdidas sem esse método. Esse método não faz com que a inserção ou exclusão de tipos ou membros, mas em vez disso, adiciona dados adicionais para os esquemas em qualquer um desses níveis.  
  
 O método está sobrecarregado e pode levar a um `Type` (`clrtype` parâmetro) ou <xref:System.Reflection.MemberInfo> (`memberInfo` parâmetro). O segundo parâmetro é sempre um `Type` (`dataContractType` parâmetro). Este método é chamado para cada membro e o tipo do substituído `dataContractType` tipo.  
  
 Qualquer um dessas sobrecargas deve retornar `null` ou um objeto serializável. Um objeto nulo não será serializado como anotação no esquema exportado. Para o `Type` sobrecarga, cada tipo que é exportado para o esquema é enviado para esse método no primeiro parâmetro junto com o tipo surrogated como o `dataContractType` parâmetro. Para o `MemberInfo` sobrecarga, cada membro que é exportado para o esquema envia suas informações como o `memberInfo` parâmetro com o tipo surrogated no segundo parâmetro.  
  
#### <a name="getcustomdatatoexport-method-type-type"></a>Método GetCustomDataToExport (tipo, tipo)  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Type%2CSystem.Type%29?displayProperty=nameWithType> método é chamado durante a exportação de esquema para cada definição de tipo. O método adiciona informações para os tipos de dentro do esquema durante a exportação. Cada tipo definido é enviado para esse método para determinar se há dados adicionais que deve ser incluído no esquema.  
  
#### <a name="getcustomdatatoexport-method-memberinfo-type"></a>Método GetCustomDataToExport (MemberInfo, tipo)  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=nameWithType> é chamado durante a exportação para todos os membros de tipos que são exportados. Esta função permite que você personalize os comentários para os membros que serão incluídos no esquema na exportação. As informações para todos os membros dentro da classe são enviadas para esse método para verificar se todos os dados adicionais precisam ser adicionados no esquema.  
  
 O exemplo acima pesquisas por meio de `dataContractType` para cada membro do substituto. Em seguida, retorna o modificador de acesso apropriados para cada campo. Sem essa personalização, o valor padrão para modificadores de acesso é público. Portanto, todos os membros seriam definidos como público no código gerado usando o esquema exportado, independentemente de quais são suas restrições de acesso real. Quando não estiver usando essa implementação, o membro `numpens` será pública no esquema exportado, mesmo que foi definido em substituto como particular. Com o uso deste método, no esquema exportado, o modificador de acesso pode ser gerado como privado.  
  
### <a name="getreferencedtypeonimport-method"></a>Método GetReferencedTypeOnImport  
 Esse método mapeia o <xref:System.Type> do substituto para o tipo original. Esse método é opcional para a importação de esquema.  
  
 Ao criar um substituto que importa um esquema e gera código para ele, a próxima tarefa é definir o tipo de instância de um substituto para seu tipo original.  
  
 Se o código gerado precisa referenciar um tipo de usuário existente, isso é feito através da implementação de <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> método.  
  
 Ao importar um esquema, esse método é chamado para cada declaração de tipo mapear o contrato de dados substituído para um tipo. Os parâmetros de cadeia de caracteres `typeName` e `typeNamespace` definir o nome e o namespace do tipo surrogated. O valor de retorno para <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> é usado para determinar se um novo tipo precisa ser gerado. Esse método deve retornar null ou um tipo válido. Para os tipos válidos, o tipo retornado será ser usado como um tipo referenciado no código gerado. Se null for retornado, nenhum tipo será referenciado e deve ser criado um novo tipo. Se existirem vários substitutos, é possível realizar o mapeamento para cada tipo de substitutos para seu tipo inicial.  
  
 O `customData` parâmetro é o objeto retornado originalmente do <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A>. Isso `customData` é usado quando os autores de substitutos deseja inserir dados/dicas adicionais para os metadados a ser usado durante a importação para gerar o código.  
  
### <a name="processimportedtype-method"></a>Método ProcessImportedType  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.ProcessImportedType%2A> método personaliza qualquer tipo criado a partir de importação de esquema. Esse método é opcional.  
  
 Ao importar um esquema, esse método permite qualquer informação de tipo e compilação importada para serem personalizados. Por exemplo:  
  
 [!code-csharp[C_IDataContractSurrogate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#7)]  
  
 Durante a importação, esse método é chamado para cada tipo gerado. Alterar especificado <xref:System.CodeDom.CodeTypeDeclaration> ou modificar o <xref:System.CodeDom.CodeCompileUnit>. Isso inclui alterar o nome, membros, atributos e várias outras propriedades da `CodeTypeDeclaration`. Processando o `CodeCompileUnit`, é possível modificar as diretivas e vários outros aspectos, assemblies referenciados e namespaces.  
  
 O `CodeTypeDeclaration` parâmetro contém o código de declaração de tipo de DOM. O `CodeCompileUnit` parâmetro permite a modificação para o código de processamento.  Retornando `null` resulta na declaração de tipo que está sendo descartada. Por outro lado, ao retornar um `CodeTypeDeclaration`, as modificações são preservadas.  
  
 Se os dados personalizados são inseridos durante a exportação de metadados, ele deve ser fornecido para o usuário durante a importação para que ele possa ser usado. Esses dados podem ser usados para dicas de modelo de programação ou outros comentários. Cada `CodeTypeDeclaration` e <xref:System.CodeDom.CodeTypeMember> instância inclui dados personalizados, como o <xref:System.CodeDom.CodeObject.UserData%2A> propriedade, convertida para o `IDataContractSurrogate` tipo.  
  
 O exemplo acima executa algumas alterações no esquema importado. O código preserva membros particulares do tipo original usando um substituto. O modificador de acesso padrão ao importar um esquema é `public`. Portanto, todos os membros do esquema substituto será públicos, a menos que modificado, como neste exemplo. Durante a exportação, os dados personalizados são inseridos no metadados sobre quais membros são privados. O exemplo procura os dados personalizados, verifica se o modificador de acesso é particular e, em seguida, modifica o membro apropriado para ser privada definindo seus atributos. Sem essa personalização, o `numpens` membro deve ser definido como público, em vez de particular.  
  
### <a name="getknowncustomdatatypes-method"></a>Método GetKnownCustomDataTypes  
 Esse método obtém os tipos de dados personalizados definidos no esquema. O método é opcional para a importação de esquema.  
  
 O método é chamado no começo de importação e exportação de esquema. O método retorna os tipos de dados personalizados usados no esquema exportados ou importados. O método é passado um <xref:System.Collections.ObjectModel.Collection%601> (o `customDataTypes` parâmetro), que é uma coleção de tipos. O método deve adicionar tipos conhecidos adicionais a essa coleção. Os tipos de dados personalizados conhecidos são necessárias para habilitar a serialização e desserialização de dados personalizados usando o <xref:System.Runtime.Serialization.DataContractSerializer>. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="implementing-a-surrogate"></a>Implementando um substituto  
 Para usar o substituto de contrato de dados dentro de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], você deve seguir alguns procedimentos especiais.  
  
### <a name="to-use-a-surrogate-for-serialization-and-deserialization"></a>Para usar um substituto para serialização e desserialização  
 Use o <xref:System.Runtime.Serialization.DataContractSerializer> para realizar a serialização e desserialização de dados com o substituto. O <xref:System.Runtime.Serialization.DataContractSerializer> é criado o <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. O substituto também deve ser especificado.  
  
##### <a name="to-implement-serialization-and-deserialization"></a>Para implementar a serialização e desserialização  
  
1.  Criar uma instância do <xref:System.ServiceModel.ServiceHost> para seu serviço. Para obter instruções completas, consulte [básicas de programação WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
2.  Para cada <xref:System.ServiceModel.Description.ServiceEndpoint> do host do serviço especificado, localizar seu <xref:System.ServiceModel.Description.OperationDescription>.  
  
3.  Pesquise os comportamentos de operação para determinar se uma instância do <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> foi encontrado.  
  
4.  Se um <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> é encontrado, defina seu <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> propriedade para uma nova instância do substituto. Se nenhum <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> é encontrado, em seguida, criar uma nova instância e definir o <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> membro do novo comportamento para uma nova instância do substituto.  
  
5.  Finalmente, adicione esse novo comportamento para os comportamentos da operação atual, conforme mostrado no exemplo a seguir:  
  
     [!code-csharp[C_IDataContractSurrogate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#8)]  
  
### <a name="to-use-a-surrogate-for-metadata-import"></a>Para usar um substituto para importação de metadados  
 Ao importar metadados como WSDL e XSD para gerar o código do lado do cliente, o substituto precisa ser adicionada ao componente responsável pela geração de código do esquema XSD, <xref:System.Runtime.Serialization.XsdDataContractImporter>. Para fazer isso, modifique diretamente o <xref:System.ServiceModel.Description.WsdlImporter> usado para importar os metadados.  
  
##### <a name="to-implement-a-surrogate-for-metadata-importation"></a>Para implementar um substituto de importação de metadados  
  
1.  Importar metadados usando o <xref:System.ServiceModel.Description.WsdlImporter> classe.  
  
2.  Use o <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> método para verificar se um <xref:System.Runtime.Serialization.XsdDataContractImporter> foi definido.  
  
3.  Se o <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> método retorna `false`, crie um novo <xref:System.Runtime.Serialization.XsdDataContractImporter> e defina seu <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> propriedade para uma nova instância do <xref:System.Runtime.Serialization.ImportOptions> classe. Caso contrário, use o importador retornado pelo `out` parâmetro o <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> método.  
  
4.  Se o <xref:System.Runtime.Serialization.XsdDataContractImporter> não tem nenhum <xref:System.Runtime.Serialization.ImportOptions> definido, então, defina a propriedade seja uma nova instância do <xref:System.Runtime.Serialization.ImportOptions> classe.  
  
5.  Definir o <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> propriedade do <xref:System.Runtime.Serialization.ImportOptions> do <xref:System.Runtime.Serialization.XsdDataContractImporter> para uma nova instância do substituto.  
  
6.  Adicionar o <xref:System.Runtime.Serialization.XsdDataContractImporter> a coleção retornada pelo <xref:System.ServiceModel.Description.MetadataExporter.State%2A> propriedade o <xref:System.ServiceModel.Description.WsdlImporter> (herdado da <xref:System.ServiceModel.Description.MetadataExporter> classe.)  
  
7.  Use o <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> método o <xref:System.ServiceModel.Description.WsdlImporter> para importar todos os contratos de dados dentro do esquema. Durante a última etapa, o código é gerado de esquemas carregados chamando o substituto.  
  
     [!code-csharp[C_IDataContractSurrogate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#9)]  
  
### <a name="to-use-a-surrogate-for-metadata-export"></a>Para usar um substituto para exportação de metadados  
 Por padrão, ao exportar metadados de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para um serviço, o esquema WSDL e XSD precisa ser gerado. O substituto precisa ser adicionada para o componente responsável por gerar esquema XSD para tipos de contrato de dados, <xref:System.Runtime.Serialization.XsdDataContractExporter>. Para fazer isso, use um comportamento que implementa <xref:System.ServiceModel.Description.IWsdlExportExtension> para modificar o <xref:System.ServiceModel.Description.WsdlExporter>, ou modificar diretamente o <xref:System.ServiceModel.Description.WsdlExporter> usado para exportar metadados.  
  
##### <a name="to-use-a-surrogate-for-metadata-export"></a>Para usar um substituto para exportação de metadados  
  
1.  Criar um novo <xref:System.ServiceModel.Description.WsdlExporter> ou use o `wsdlExporter` parâmetro passado para o <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> método.  
  
2.  Use o <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> para verificar se um <xref:System.Runtime.Serialization.XsdDataContractExporter> foi definido.  
  
3.  Se <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> retorna `false`, criar um novo <xref:System.Runtime.Serialization.XsdDataContractExporter> com os esquemas XML gerados do <xref:System.ServiceModel.Description.WsdlExporter>e adicioná-lo à coleção retornada pelo <xref:System.ServiceModel.Description.MetadataExporter.State%2A> propriedade o <xref:System.ServiceModel.Description.WsdlExporter>. Caso contrário, use o exportador retornado pelo `out` parâmetro o <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> método.  
  
4.  Se o <xref:System.Runtime.Serialization.XsdDataContractExporter> não tem nenhum <xref:System.Runtime.Serialization.ExportOptions> definido, então, defina o <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> propriedade para uma nova instância do <xref:System.Runtime.Serialization.ExportOptions> classe.  
  
5.  Definir o <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A> propriedade do <xref:System.Runtime.Serialization.ExportOptions> do <xref:System.Runtime.Serialization.XsdDataContractExporter> para uma nova instância do substituto. As etapas subsequentes para a exportação de metadados não requer alterações.  
  
     [!code-csharp[C_IDataContractSurrogate#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#10)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.IDataContractSurrogate>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.Runtime.Serialization.ImportOptions>  
 <xref:System.Runtime.Serialization.ExportOptions>  
 [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
