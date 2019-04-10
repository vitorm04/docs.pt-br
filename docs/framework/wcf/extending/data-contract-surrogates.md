---
title: Substitutos de contrato de dados
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], surrogates
ms.assetid: 8c31134c-46c5-4ed7-94af-bab0ac0dfce5
ms.openlocfilehash: f97826cb5154035b535b5eac3a8818d8b366d639
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315342"
---
# <a name="data-contract-surrogates"></a>Substitutos de contrato de dados
O contrato de dados *substituto* é um recurso avançado, criado sobre o modelo de contrato de dados. Esse recurso destina-se a ser usado para o tipo de personalização e substituição em situações em que os usuários quiserem alterar como um tipo é serializado, desserializados ou projetado em metadados. Alguns cenários onde um substituto pode ser usado é quando um contrato de dados não foi especificado para o tipo, campos e propriedades não são marcadas com o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo ou usuários desejarem criar dinamicamente as variações de esquema.  
  
 Serialização e desserialização são realizadas com o substituto de contrato de dados ao usar <xref:System.Runtime.Serialization.DataContractSerializer> para converter do .NET Framework em um formato adequado, como XML. Substitutos de contrato de dados também podem ser usado para modificar os metadados exportados para tipos, durante a produção de representações de metadados, como documentos de esquema XML (XSD). Após a importação, código é criado a partir de metadados e o substituto pode ser usado nesse caso, para personalizar o código gerado.  
  
## <a name="how-the-surrogate-works"></a>Como funciona o substituto  
 Um substituto funciona por um tipo de mapeamento (o tipo "original") em outro tipo (o tipo "surrogated"). O exemplo a seguir mostra o tipo original `Inventory` e um substituto novo `InventorySurrogated` tipo. O `Inventory` tipo não é serializável, mas o `InventorySurrogated` é do tipo:  
  
 [!code-csharp[C_IDataContractSurrogate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#1)]  
  
 Como um contrato de dados não foi definido para esta classe, converta a classe a uma classe de substitutos com um contrato de dados. A classe surrogated é mostrada no exemplo a seguir:  
  
 [!code-csharp[C_IDataContractSurrogate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#2)]  
  
## <a name="implementing-the-idatacontractsurrogate"></a>Implementação de IDataContractSurrogate  
 Para usar o substituto de contrato de dados, implementar o <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.  
  
 A seguir está uma visão geral de cada método de <xref:System.Runtime.Serialization.IDataContractSurrogate> com uma implementação possível.  
  
### <a name="getdatacontracttype"></a>GetDataContractType  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> método mapeia um tipo para outro. Esse método é necessário para serialização, desserialização, importação e exportação.  
  
 A primeira tarefa é definir quais tipos serão mapeados para outros tipos. Por exemplo:  
  
 [!code-csharp[C_IDataContractSurrogate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#3)]  
  
-   Na serialização, o mapeamento retornado por esse método é usado posteriormente para transformar a instância original para uma instância surrogated chamando o <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> método.  
  
-   Na desserialização, o mapeamento retornado por esse método é usado pelo serializador para desserializar em uma instância do tipo substituto. Ele chama subsequentemente <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> para transformar a instância surrogated em uma instância do tipo original.  
  
-   Na exportação, o tipo de substitutos retornado por esse método é refletido para obter o contrato de dados a ser usado para geração de metadados.  
  
-   Na importação, o tipo inicial é alterado para um tipo substituto que é refletido para obter o contrato de dados a ser usado para fins como a referenciação a suporte.  
  
 O <xref:System.Type> parâmetro é o tipo do objeto que está sendo serializado desserializado, importado ou exportado. O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> método deve retornar o tipo de entrada se o substituto não manipular o tipo. Caso contrário, retorne o tipo surrogated apropriado. Se existem vários tipos de substitutos, vários mapeamentos podem ser definidos nesse método.  
  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> método não é chamado para os dados internos primitivos de contrato, como <xref:System.Int32> ou <xref:System.String>. Para outros tipos, como matrizes, tipos definidos pelo usuário e outras estruturas de dados, esse método será chamado para cada tipo.  
  
 No exemplo anterior, o método verifica se o `type` parâmetro e `Inventory` são comparáveis. Se assim, o método que ele mapeia `InventorySurrogated`. Sempre que uma serialização, desserialização, o esquema de importação ou exportação de esquema é chamada, essa função é chamada primeiro para determinar o mapeamento entre tipos.  
  
### <a name="getobjecttoserialize-method"></a>Método GetObjectToSerialize  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> método converte a instância do tipo original para a instância do tipo alternativo. O método é necessário para serialização.  
  
 A próxima etapa é definir o modo como os dados físicos serão mapeados da instância original para o substituto Implementando o <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> método. Por exemplo:  
  
 [!code-csharp[C_IDataContractSurrogate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#4)]  
  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> método é chamado quando um objeto é serializado. Esse método transfere dados do tipo original para os campos do tipo surrogated. Campos podem ser mapeados diretamente para campos de substitutos ou manipulações dos dados originais podem ser armazenadas no substituto. Alguns usos possíveis incluem: diretamente os campos de mapeamento, executar operações nos dados para ser armazenados nos campos surrogated ou armazenar o XML do tipo original no campo surrogated.  
  
 O `targetType` parâmetro refere-se para o tipo declarado do membro. Esse parâmetro é o tipo surrogated retornado pelo <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> método. O serializador não impõe que o objeto retornado é atribuível a esse tipo. O `obj` parâmetro é o objeto a serem serializados e será convertido em seu substituto se necessário. Esse método deve retornar o objeto de entrada se o surrogated não manipular o objeto. Caso contrário, o novo objeto de substituto será retornado. A alternativa não é chamada se o objeto é nulo. Vários mapeamentos de substitutos para instâncias diferentes podem ser definidos dentro desse método.  
  
 Ao criar um <xref:System.Runtime.Serialization.DataContractSerializer>, você pode instruí-lo a preservar as referências de objeto. (Para obter mais informações, consulte [serialização e desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).) Isso é feito definindo a `preserveObjectReferences` parâmetro em seu construtor para `true`. Nesse caso, o substituto é chamado apenas uma vez para um objeto, já que todas as serializações subsequentes simplesmente escrever a referência no fluxo. Se `preserveObjectReferences` é definido como `false`, em seguida, o substituto é chamado sempre que uma instância é encontrada.  
  
 Se o tipo da instância serializada difere do tipo declarado, informações de tipo serão gravadas no fluxo, por exemplo, `xsi:type` para permitir que a instância a ser desserializado na outra extremidade. Esse processo ocorre se o objeto é substituído ou não.  
  
 O exemplo anterior converte os dados do `Inventory` instância de `InventorySurrogated`. Ele verifica o tipo do objeto e realiza as manipulações necessário para converter o tipo surrogated. Nesse caso, os campos do `Inventory` classe são copiados diretamente para o `InventorySurrogated` campos de classe.  
  
### <a name="getdeserializedobject-method"></a>Método GetDeserializedObject  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> método converte a instância do tipo alternativo para a instância do tipo original. Ele é necessário para desserialização.  
  
 A próxima tarefa é definir o modo como os dados físicos serão mapeados da instância do substituto para o original. Por exemplo:  
  
 [!code-csharp[C_IDataContractSurrogate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#5)]  
  
 Esse método é chamado somente durante a desserialização de um objeto. Ele fornece o mapeamento inverso de dados para a desserialização do tipo substituto volta para seu tipo original. Semelhante ao `GetObjectToSerialize` alguns usos possíveis do método, podem ser para troca de campo de dados, executar operações nos dados e armazenar dados XML diretamente. Ao desserializar, você pode não sempre obter os valores de dados exata do original devido a manipulações na conversão de dados.  
  
 O `targetType` parâmetro refere-se para o tipo declarado do membro. Esse parâmetro é o tipo surrogated retornado pelo `GetDataContractType` método. O `obj` parâmetro faz referência ao objeto que foi desserializado. O objeto pode ser convertido novamente para seu tipo original, se ele é alternativo. Esse método retorna o objeto de entrada se o substituto não manipular o objeto. Caso contrário, o objeto desserializado será retornado quando a conversão tiver sido concluída. Se existirem vários tipos de substitutos, você pode fornecer conversão de dados substituto para o tipo primário para cada indicando cada tipo e a conversão.  
  
 Ao retornar um objeto, as tabelas de objeto interno são atualizadas com o objeto retornado por este substituto. Todas as referências subsequentes para uma instância obterá a instância surrogated das tabelas do objeto.  
  
 O exemplo anterior converte objetos do tipo `InventorySurrogated` volta para o tipo inicial `Inventory`. Nesse caso, os dados são transferidos diretamente do `InventorySurrogated` aos seus campos correspondentes no `Inventory`. Como não há nenhuma manipulação de dados, cada um dos campos de membro conterá os mesmos valores que antes da serialização.  
  
### <a name="getcustomdatatoexport-method"></a>Método GetCustomDataToExport  
 Ao exportar um esquema, o <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A> método é opcional. Ele é usado para inserir dados adicionais ou dicas de esquema exportado. Dados adicionais podem ser inseridos no nível de membro ou tipo. Por exemplo:  
  
 [!code-csharp[C_IDataContractSurrogate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#6)]  
  
 Esse método (com duas sobrecargas) permite a inclusão de informações extras para os metadados no nível do membro ou tipo. É possível incluir dicas sobre se um membro é público ou privado e comentários que poderiam ser preservados durante a exportação e importação do esquema. Essas informações seriam perdidas sem esse método. Esse método não faz com que a inserção ou exclusão de tipos ou membros, mas em vez disso, adiciona dados adicionais para os esquemas em qualquer um desses níveis.  
  
 O método está sobrecarregado e pode levar a um `Type` (`clrtype` parâmetro) ou <xref:System.Reflection.MemberInfo> (`memberInfo` parâmetro). O segundo parâmetro é sempre uma `Type` (`dataContractType` parâmetro). Esse método é chamado para cada membro e o tipo das substituído `dataContractType` tipo.  
  
 Qualquer uma dessas sobrecargas deve retornar `null` ou um objeto serializável. Um objeto não nulo será serializado como a anotação para o esquema exportado. Para o `Type` sobrecarga, cada tipo que é exportado para o esquema é enviado para esse método no primeiro parâmetro junto com o tipo surrogated como o `dataContractType` parâmetro. Para o `MemberInfo` sobrecarga, cada membro que é exportado para o esquema envia suas informações de como o `memberInfo` parâmetro com o tipo surrogated no segundo parâmetro.  
  
#### <a name="getcustomdatatoexport-method-type-type"></a>Método GetCustomDataToExport (tipo, tipo)  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Type%2CSystem.Type%29?displayProperty=nameWithType> método é chamado durante a exportação de esquema para cada definição de tipo. O método adiciona informações para os tipos dentro do esquema ao exportar. Cada tipo definido é enviado para esse método para determinar se há quaisquer dados adicionais que precisa ser incluído no esquema.  
  
#### <a name="getcustomdatatoexport-method-memberinfo-type"></a>Método GetCustomDataToExport (MemberInfo, tipo)  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=nameWithType> é chamado durante a exportação para todos os membros de tipos que são exportados. Essa função permite que você personalize os comentários para os membros que serão incluídos no esquema na exportação. As informações para todos os membros dentro da classe são enviadas para esse método para verificar se todos os dados adicionais precisam ser adicionados no esquema.  
  
 O exemplo acima pesquisas por meio de `dataContractType` para cada membro do substituto. Ele então retorna o modificador de acesso apropriados para cada campo. Sem essa personalização, o valor padrão de modificadores de acesso é público. Portanto, todos os membros seriam definidos como público no código gerado usando o esquema exportado, independentemente de quais são suas restrições de acesso real. Quando não estiver usando essa implementação, o membro `numpens` seria público no esquema exportado, mesmo que ela foi definida no substituto como particular. Com o uso desse método, no esquema exportado, o modificador de acesso pode ser gerado como particular.  
  
### <a name="getreferencedtypeonimport-method"></a>GetReferencedTypeOnImport Method  
 Esse método mapeia o <xref:System.Type> do substituto para o tipo original. Esse método é opcional para a importação de esquema.  
  
 Durante a criação de um substituto que importa um esquema e gera código para ele, a próxima tarefa é definir o tipo de instância de um substituto para seu tipo original.  
  
 Se o código gerado precisar fazer referência a um tipo de usuário existente, isso é feito com a implementação de <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> método.  
  
 Ao importar um esquema, esse método é chamado para cada declaração de tipo mapear o contrato de dados alternativo para um tipo. Os parâmetros de cadeia de caracteres `typeName` e `typeNamespace` definem o nome e o namespace do tipo surrogated. O valor de retorno para <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> é usado para determinar se um novo tipo precisa ser gerado. Esse método deve retornar um tipo válido ou null. Para os tipos válidos, o tipo retornado será ser usado como um tipo referenciado no código gerado. Se null for retornado, nenhum tipo será referenciado e deve ser criado um novo tipo. Se existirem vários substitutos, é possível realizar o mapeamento para cada tipo de substitutos volta ao seu tipo inicial.  
  
 O `customData` parâmetro é o objeto retornado originalmente da <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A>. Isso `customData` é usado quando os autores de substitutos insere extras/dicas de dados nos metadados para usar durante a importação para gerar código.  
  
### <a name="processimportedtype-method"></a>Método ProcessImportedType  
 O <xref:System.Runtime.Serialization.IDataContractSurrogate.ProcessImportedType%2A> método personaliza qualquer tipo criado a partir de importação de esquema. Esse método é opcional.  
  
 Quando importar um esquema, esse método permite que qualquer informação de tipo e a compilação importada para serem personalizados. Por exemplo:  
  
 [!code-csharp[C_IDataContractSurrogate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#7)]  
  
 Durante a importação, esse método é chamado para todos os tipos gerados. Alterar especificado <xref:System.CodeDom.CodeTypeDeclaration> ou modificar o <xref:System.CodeDom.CodeCompileUnit>. Isso inclui alterar o nome, membros, atributos e várias outras propriedades do `CodeTypeDeclaration`. Processando o `CodeCompileUnit`, é possível modificar as diretivas, namespaces, assemblies referenciados e vários outros aspectos.  
  
 O `CodeTypeDeclaration` parâmetro contém o código de declaração de tipo de DOM. O `CodeCompileUnit` parâmetro permite a modificação para o código de processamento.  Retornando `null` resulta na declaração de tipo que está sendo descartada. Por outro lado, ao retornar um `CodeTypeDeclaration`, as modificações são preservadas.  
  
 Se os dados personalizados são inseridos durante a exportação de metadados, ele precisa ser fornecida ao usuário durante a importação para que ele pode ser usado. Estes dados personalizados podem ser usados para dicas de modelo de programação ou outros comentários. Cada `CodeTypeDeclaration` e <xref:System.CodeDom.CodeTypeMember> instância inclui dados personalizados como o <xref:System.CodeDom.CodeObject.UserData%2A> propriedade, convertida para o `IDataContractSurrogate` tipo.  
  
 O exemplo acima executa algumas alterações no esquema importado. O código preserva membros privados do tipo original usando um substituto. O modificador de acesso padrão ao importar um esquema é `public`. Portanto, todos os membros do esquema alternativo será públicos, a menos que modificado, como neste exemplo. Durante a exportação, os dados personalizados são inseridos no metadados sobre quais membros são particulares. O exemplo procura os dados personalizados, verifica se o modificador de acesso é particular e, em seguida, modifica o membro apropriado para ser privados, definindo seus atributos. Sem essa personalização, o `numpens` membro seria definido como pública em vez de particulares.  
  
### <a name="getknowncustomdatatypes-method"></a>Método GetKnownCustomDataTypes  
 Esse método obtém os tipos de dados personalizados definidos no esquema. O método é opcional para a importação de esquema.  
  
 O método é chamado no início de importação e exportação de esquema. O método retorna os tipos de dados personalizados usados no esquema exportados ou importados. O método recebe um <xref:System.Collections.ObjectModel.Collection%601> (o `customDataTypes` parâmetro), que é uma coleção de tipos. O método deve adicionar tipos conhecidos adicionais a essa coleção. Os tipos de dados personalizados conhecidos são necessárias para habilitar a serialização e desserialização dos dados personalizados usando o <xref:System.Runtime.Serialization.DataContractSerializer>. Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="implementing-a-surrogate"></a>Implementando um substituto  
 Para usar o substituto de contrato de dados dentro do WCF, você deve seguir alguns procedimentos especiais.  
  
### <a name="to-use-a-surrogate-for-serialization-and-deserialization"></a>Para usar um substituto para serialização e desserialização  
 Use o <xref:System.Runtime.Serialization.DataContractSerializer> para realizar serialização e desserialização de dados com o substituto. O <xref:System.Runtime.Serialization.DataContractSerializer> é criado pelo <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. O substituto também deve ser especificado.  
  
##### <a name="to-implement-serialization-and-deserialization"></a>Para implementar a serialização e desserialização  
  
1. Criar uma instância do <xref:System.ServiceModel.ServiceHost> para seu serviço. Para obter instruções completas, consulte [programação WCF básica](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
2. Para cada <xref:System.ServiceModel.Description.ServiceEndpoint> do host do serviço especificado, encontre seu <xref:System.ServiceModel.Description.OperationDescription>.  
  
3. Pesquisa por meio dos comportamentos de operação para determinar se uma instância da <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> for encontrado.  
  
4. Se um <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> é encontrado, defina seu <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> propriedade para uma nova instância do substituto. Se nenhum <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> é encontrado, em seguida, crie uma nova instância e defina o <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> membro do novo comportamento para uma nova instância do substituto.  
  
5. Por fim, adicione esse novo comportamento para os comportamentos da operação atual, conforme mostrado no exemplo a seguir:  
  
     [!code-csharp[C_IDataContractSurrogate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#8)]  
  
### <a name="to-use-a-surrogate-for-metadata-import"></a>Para usar um substituto para importação de metadados  
 Durante a importação de metadados, como a WSDL e XSD para gerar o código do lado do cliente, o substituto precisa ser adicionada para o componente responsável por gerar o código de esquema XSD, <xref:System.Runtime.Serialization.XsdDataContractImporter>. Para fazer isso, modifique diretamente o <xref:System.ServiceModel.Description.WsdlImporter> usado para importar metadados.  
  
##### <a name="to-implement-a-surrogate-for-metadata-importation"></a>Para implementar um substituto para a importação de metadados  
  
1. Importe os metadados usando o <xref:System.ServiceModel.Description.WsdlImporter> classe.  
  
2. Use o <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> método para verificar se um <xref:System.Runtime.Serialization.XsdDataContractImporter> foi definido.  
  
3. Se o <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> método retorna `false`, crie uma nova <xref:System.Runtime.Serialization.XsdDataContractImporter> e defina seu <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> propriedade para uma nova instância do <xref:System.Runtime.Serialization.ImportOptions> classe. Caso contrário, use o importador retornado pela `out` parâmetro do <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> método.  
  
4. Se o <xref:System.Runtime.Serialization.XsdDataContractImporter> não tem nenhum <xref:System.Runtime.Serialization.ImportOptions> definido, então, defina a propriedade seja uma nova instância do <xref:System.Runtime.Serialization.ImportOptions> classe.  
  
5. Defina a <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> propriedade do <xref:System.Runtime.Serialization.ImportOptions> da <xref:System.Runtime.Serialization.XsdDataContractImporter> para uma nova instância do substituto.  
  
6. Adicionar o <xref:System.Runtime.Serialization.XsdDataContractImporter> à coleção retornada pela <xref:System.ServiceModel.Description.MetadataExporter.State%2A> propriedade da <xref:System.ServiceModel.Description.WsdlImporter> (herdado da <xref:System.ServiceModel.Description.MetadataExporter> classe.)  
  
7. Use o <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> método da <xref:System.ServiceModel.Description.WsdlImporter> para importar todos os contratos de dados dentro do esquema. Durante a última etapa, o código é gerado de esquemas carregados chamando o substituto.  
  
     [!code-csharp[C_IDataContractSurrogate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#9)]  
  
### <a name="to-use-a-surrogate-for-metadata-export"></a>Para usar um substituto para exportação de metadados  
 Por padrão, ao exportar metadados de WCF para um serviço, WSDL e XSD do esquema precisa ser gerado. O substituto precisa ser adicionada para o componente responsável por gerar esquema XSD para tipos de contrato de dados, <xref:System.Runtime.Serialization.XsdDataContractExporter>. Para fazer isso, use um comportamento que implementa <xref:System.ServiceModel.Description.IWsdlExportExtension> para modificar os <xref:System.ServiceModel.Description.WsdlExporter>, ou modificar diretamente o <xref:System.ServiceModel.Description.WsdlExporter> usado para exportar metadados.  
  
##### <a name="to-use-a-surrogate-for-metadata-export"></a>Para usar um substituto para exportação de metadados  
  
1. Criar um novo <xref:System.ServiceModel.Description.WsdlExporter> ou usar o `wsdlExporter` parâmetro passado para o <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> método.  
  
2. Use o <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> função para verificar se um <xref:System.Runtime.Serialization.XsdDataContractExporter> foi definido.  
  
3. Se <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> retorna `false`, crie uma nova <xref:System.Runtime.Serialization.XsdDataContractExporter> com os esquemas XML gerados da <xref:System.ServiceModel.Description.WsdlExporter>e adicioná-lo à coleção retornada pela <xref:System.ServiceModel.Description.MetadataExporter.State%2A> propriedade do <xref:System.ServiceModel.Description.WsdlExporter>. Caso contrário, use o exportador retornado pela `out` parâmetro do <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> método.  
  
4. Se o <xref:System.Runtime.Serialization.XsdDataContractExporter> não tem nenhum <xref:System.Runtime.Serialization.ExportOptions> definido, então, defina as <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> propriedade para uma nova instância do <xref:System.Runtime.Serialization.ExportOptions> classe.  
  
5. Defina a <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A> propriedade do <xref:System.Runtime.Serialization.ExportOptions> da <xref:System.Runtime.Serialization.XsdDataContractExporter> para uma nova instância do substituto. As etapas subsequentes para a exportação de metadados não requer alterações.  
  
     [!code-csharp[C_IDataContractSurrogate#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#10)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.IDataContractSurrogate>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.Runtime.Serialization.ImportOptions>
- <xref:System.Runtime.Serialization.ExportOptions>
- [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
