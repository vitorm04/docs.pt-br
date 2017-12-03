---
title: Importando esquema para gerar classes
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractImporter class
ms.assetid: b9170583-8c34-43bd-97bb-6c0c8dddeee0
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ae7ed7b1d01420c8e542d9ecce577995e927adc3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="importing-schema-to-generate-classes"></a>Importando esquema para gerar classes
Para gerar classes de esquemas que podem ser usados com [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], use o <xref:System.Runtime.Serialization.XsdDataContractImporter> classe. Este tópico descreve o processo e variações.  
  
## <a name="the-import-process"></a>O processo de importação  
 Inicia o processo de importação de esquema com um <xref:System.Xml.Schema.XmlSchemaSet> e produz um <xref:System.CodeDom.CodeCompileUnit>.  
  
 O `XmlSchemaSet` faz parte do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]do modelo de objeto de esquema (SOM) que representa um conjunto de documentos de esquema XML Schema definition language (XSD). Para criar um `XmlSchemaSet` de objeto de um conjunto de documentos XSD, desserializar cada documento em um <xref:System.Xml.Schema.XmlSchema> objeto (usando o <xref:System.Xml.Serialization.XmlSerializer>) e adicione esses objetos para um novo `XmlSchemaSet`.  
  
 O `CodeCompileUnit` faz parte do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]do código Document Object Model (CodeDOM) que representa [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] código de forma abstrata. Para gerar o código real de um `CodeCompileUnit`, use uma subclasse do <xref:System.CodeDom.Compiler.CodeDomProvider> classe, como o <xref:Microsoft.CSharp.CSharpCodeProvider> ou <xref:Microsoft.VisualBasic.VBCodeProvider> classe.  
  
#### <a name="to-import-a-schema"></a>Para importar um esquema  
  
1.  Criar uma instância do <xref:System.Runtime.Serialization.XsdDataContractImporter>.  
  
2.  Opcional. Passar um `CodeCompileUnit` no construtor. Os tipos gerados durante a importação de esquema são adicionados a este `CodeCompileUnit` instância em vez de começar com um espaço em branco `CodeCompileUnit`.  
  
3.  Opcional. Chame um do <xref:System.Runtime.Serialization.XsdDataContractImporter.CanImport%2A> métodos. O método determina se o esquema fornecido é um esquema de contrato de dados válido e pode ser importado. O `CanImport` método tem as mesmo sobrecargas como `Import` (a próxima etapa).  
  
4.  Chame um dos sobrecarregados `Import` métodos, por exemplo, o <xref:System.Runtime.Serialization.XsdDataContractImporter.Import%28System.Xml.Schema.XmlSchemaSet%29> método.  
  
     A sobrecarga mais simples tem um `XmlSchemaSet` e importa todos os tipos, incluindo tipos anônimos, encontrados no conjunto de esquema. Outras sobrecargas permitem que você especifique o tipo XSD ou uma lista de tipos para importar (na forma de um <xref:System.Xml.XmlQualifiedName> ou uma coleção de `XmlQualifiedName` objetos). Nesse caso, somente os tipos especificados são importados. Usa uma sobrecarga um <xref:System.Xml.Schema.XmlSchemaElement> que importa um determinado elemento do `XmlSchemaSet`, bem como seu tipo associado (se ela é anônima ou não). Essa sobrecarga retorna um `XmlQualifiedName`, que representa o nome do contrato de dados do tipo gerado para este elemento.  
  
     Diversas chamadas do `Import` método resultam em vários itens que estão sendo adicionadas à mesma `CodeCompileUnit`. Um tipo não é gerado para o `CodeCompileUnit` se ele já existe. Chamar `Import` várias vezes na mesma `XsdDataContractImporter` em vez de usar várias `XsdDataContractImporter` objetos. Essa é a maneira recomendada para evitar tipos duplicados que está sendo gerados.  
  
    > [!NOTE]
    >  Se houver uma falha durante a importação, o `CodeCompileUnit` estará em um estado imprevisível. Usando um `CodeCompileUnit` resultante de uma falha na importação pode expor você a vulnerabilidades de segurança.  
  
5.  Acesso a `CodeCompileUnit` por meio de <xref:System.Runtime.Serialization.XsdDataContractImporter.CodeCompileUnit%2A> propriedade.  
  
### <a name="import-options-customizing-the-generated-types"></a>Opções de importação: Personalizando os tipos gerados  
 Você pode definir o <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> propriedade o <xref:System.Runtime.Serialization.XsdDataContractImporter> a uma instância do <xref:System.Runtime.Serialization.ImportOptions> classe para controlar vários aspectos do processo de importação. Um número de opções influenciar diretamente os tipos que são gerados.  
  
#### <a name="controlling-the-access-level-generateinternal-or-the-internal-switch"></a>Controlar o nível de acesso (GenerateInternal ou / interno alternar)  
 Isso corresponde do **/ interno** alternar o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 Normalmente, os tipos públicos são gerados de esquema, com campos particulares e propriedades de membro de dados públicos correspondente. Para gerar tipos internos em vez disso, defina o <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> propriedade `true`.  
  
 O exemplo a seguir mostra um esquema transformado em interno quando o <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> estiver definida como`true.`  
  
 [!code-csharp[c_SchemaImportExport#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#2)]
 [!code-vb[c_SchemaImportExport#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#2)]  
  
#### <a name="controlling-namespaces-namespaces-or-the-namespace-switch"></a>Controlando Namespaces (espaços para nome ou o /namespace alternar)  
 Isso corresponde do **/namespace** alternar o `Svcutil.exe` ferramenta.  
  
 Normalmente, os tipos gerados a partir de esquema são gerados em [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] namespaces, com cada namespace XSD correspondente a um determinado [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] namespace de acordo com um mapeamento descrito na [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Você pode personalizar esse mapeamento, o <xref:System.Runtime.Serialization.ImportOptions.Namespaces%2A> propriedade para um <xref:System.Collections.Generic.Dictionary%602>. Se um namespace XSD específico for encontrado no dicionário, a correspondência [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] namespace também será removido do dicionário.  
  
 Por exemplo, considere o esquema a seguir.  
  
 [!code-xml[c_SchemaImportExport#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#10)]  
  
 O exemplo a seguir usa o `Namespaces` propriedade para mapear o namespace "http://schemas.contoso.com/carSchema" para "Contoso.Cars".  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
#### <a name="adding-the-serializableattribute-generateserializable-or-the-serializable-switch"></a>Adicionando o SerializableAttribute (GenerateSerializable ou / serializável alternar)  
 Isso corresponde do **/ serializável** alternar o `Svcutil.exe` ferramenta.  
  
 Às vezes, é importante para os tipos gerados a partir do esquema a ser usado com [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] mecanismos de serialização de tempo de execução (por exemplo, o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> e <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes). Isso é útil ao usar tipos de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] comunicação remota. Para habilitar isso, você deve aplicar o <xref:System.SerializableAttribute> atributo para os tipos gerados além normal <xref:System.Runtime.Serialization.DataContractAttribute> atributo. O atributo é gerado automaticamente se o `GenerateSerializable` opção de importação está definida como `true`.  
  
 A exemplo a seguir mostra o `Vehicle` classe gerada com o `GenerateSerializable` opção definida como importar `true`.  
  
 [!code-csharp[c_SchemaImportExport#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#4)]
 [!code-vb[c_SchemaImportExport#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#4)]  
  
#### <a name="adding-data-binding-support-enabledatabinding-or-the-enabledatabinding-switch"></a>Adicionando suporte a associação de dados (EnableDataBinding ou a opção /enableDataBinding)  
 Isso corresponde do **/enableDataBinding** ativar a ferramenta Svcutil.exe.  
  
 Às vezes, você talvez queira associar os tipos gerados do esquema de componentes da interface gráfica do usuário para que qualquer atualização instâncias desses tipos atualizará automaticamente a interface do usuário. O `XsdDataContractImporter` pode gerar tipos que implementam o <xref:System.ComponentModel.INotifyPropertyChanged> interface de forma que qualquer alteração de propriedade dispara um evento. Se você estiver gerando tipos para uso com um ambiente de programação de interface do usuário de cliente que dá suporte a essa interface (como [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)]), defina o <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> propriedade `true` para habilitar esse recurso.  
  
 A exemplo a seguir mostra o `Vehicle` classe gerada com o <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> definido como `true`.  
  
 [!code-csharp[C_SchemaImportExport#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#5)]
 [!code-vb[C_SchemaImportExport#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#5)]  
  
### <a name="import-options-choosing-collection-types"></a>Opções de importação: Escolher tipos de coleção  
 Dois padrões de especiais no XML representam coleções de itens: lista de itens e as associações entre um item e o outro. Este é um exemplo de uma lista de cadeias de caracteres.  
  
 [!code-xml[C_SchemaImportExport#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#11)]  
  
 A seguir está um exemplo de uma associação entre uma cadeia de caracteres e um número inteiro (`city name` e `population`).  
  
 [!code-xml[C_SchemaImportExport#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#12)]  
  
> [!NOTE]
>  Qualquer associação também pode ser considerada uma lista. Por exemplo, você pode exibir a associação anterior como uma lista de complexo `city` objetos que têm dois campos (um campo de cadeia de caracteres e um campo de número inteiro). Ambos os padrões são uma representação no esquema XSD. Não é possível diferenciar entre uma lista e uma associação para tais padrões sempre são tratados como listas, a menos que uma anotação especial específica para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] está presente no esquema. A anotação indica que um determinado padrão representa uma associação. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Contrato de dados de referência de esquema](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Normalmente, uma lista é importada como um contrato de dados de coleção que é derivada de uma lista genérica ou como um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] matriz, dependendo se o esquema segue o padrão de nomenclatura padrão para coleções. Isso é descrito mais detalhadamente na [tipos de coleção em contratos de dados](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). As associações são normalmente importadas como um <xref:System.Collections.Generic.Dictionary%602> ou um contrato de dados de coleção que é derivado do objeto de dicionário. Por exemplo, considere o esquema a seguir.  
  
 [!code-xml[c_SchemaImportExport#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#13)]  
  
 Isso poderia ser importado da seguinte maneira (os campos são exibidos em vez de propriedades para facilitar a leitura).  
  
 [!code-csharp[c_SchemaImportExport#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#6)]
 [!code-vb[c_SchemaImportExport#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#6)]  
  
 É possível personalizar os tipos de coleção são gerados para tais padrões de esquema. Por exemplo, é aconselhável gerar coleções derivam o <xref:System.ComponentModel.BindingList%601> em vez da <xref:System.Collections.Generic.List%601> classe para o tipo de associação para uma caixa de listagem e que ele seja atualizado automaticamente quando o conteúdo da coleção é alterado. Para fazer isso, defina o <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> propriedade o <xref:System.Runtime.Serialization.ImportOptions> classe para uma lista de tipos de coleção a ser usado (daqui por diante conhecidos como tipos referenciados). Ao importar qualquer coleção, esta lista de tipos de coleção referenciado é examinada e a coleção de melhor correspondência é usada caso seja encontrado. Associações são comparadas somente com tipos que implementam genérica ou não genérica <xref:System.Collections.IDictionary> interface, enquanto as listas são comparadas com qualquer tipo de coleção com suporte.  
  
 Por exemplo, se o <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> está definida como um <xref:System.ComponentModel.BindingList%601>, o `people` tipo no exemplo anterior é gerado da seguinte maneira.  
  
 [!code-csharp[C_SchemaImportExport#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#7)]
 [!code-vb[C_SchemaImportExport#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#7)]  
  
 Um genérico fechado é considerado a melhor correspondência. Por exemplo, se os tipos de `BindingList(Of Integer)` e <xref:System.Collections.ArrayList> são passados para a coleção de tipos referenciados, qualquer lista de inteiros encontrados no esquema é importada como um `BindingList(Of Integer)`. Qualquer outra lista, por exemplo, um `List(Of String)`, são importadas como um `ArrayList`.  
  
 Se um tipo que implementa o genérico `IDictionary` interface é adicionada à coleção de tipos referenciados, seus parâmetros de tipo devem ser totalmente abertos ou fechados totalmente.  
  
 Não são permitidas duplicatas. Por exemplo, você não pode adicionar ambos um `List(Of Integer)` e um `Collection(Of Integer)` para tipos referenciados. Seria mais possível determinar qual deve ser usado quando uma lista de inteiros é encontrada no esquema. Duplicatas serão detectadas somente se houver um tipo no esquema que expõe o problema de duplicatas. Por exemplo, se o esquema importado não contém listas de números inteiros, ele é permitido ter ambos o `List(Of Integer)` e `Collection(Of Integer)` em tipos referenciados coleção, mas não terá nenhum efeito.  
  
 Os tipos de coleção referenciado mecanismo funciona igualmente bem para coleções de tipos complexos (incluindo a coleções de outras coleções) e não apenas para coleções de tipos primitivos.  
  
 O `ReferencedCollectionTypes` propriedade corresponde do **/collectionType** ativar a ferramenta SvcUtil.exe. Observe que para fazer referência a vários tipos de coleção, o **/collectionType** opção deve ser especificada várias vezes. Se o tipo não é em de mscorlib. dll, seu assembly deve também ser referenciado usando a **/Reference** alternar.  
  
#### <a name="import-options-referencing-existing-types"></a>Opções de importação: Referenciar tipos existentes  
 Ocasionalmente, os tipos no esquema correspondem existente [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos, e não é necessário para gerar esses tipos a partir do zero. (Esta seção se aplica somente aos tipos de noncollection. Para tipos de coleção, consulte a seção anterior.)  
  
 Por exemplo, você pode ter um padrão em toda a empresa "Pessoa" tipo de contrato que você deseja sempre usado ao representar uma pessoa. Sempre que algum serviço faz uso desse tipo e seu esquema é exibida nos metadados do serviço, talvez você queira reutilizar existente `Person` digite ao importar esse esquema em vez de gerar um novo para cada serviço.  
  
 Para fazer isso, passar uma lista de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos que você deseja reutilizar na coleção de <xref:System.Runtime.Serialization.ImportOptions.ReferencedTypes%2A> propriedade retorna o <xref:System.Runtime.Serialization.ImportOptions> classe. Se qualquer um desses tipos tem um nome de contrato de dados e o namespace que corresponde ao nome e namespace de um tipo de esquema, é executada uma comparação estrutural. Se for determinado que os tipos têm nomes correspondentes e estruturas de correspondência, existente [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipo é reutilizado em vez de gerar um novo. Se apenas o nome corresponde mas não a estrutura, uma exceção será lançada. Observe que não há nenhum limite para controle de versão ao referenciar tipos (por exemplo, adicionando novos dados opcionais membros). As estruturas devem corresponder exatamente.  
  
 É válido para adicionar vários tipos com o mesmo nome de contrato de dados e o namespace para a coleção de tipos referenciados, desde que nenhum tipo de esquema é importado com esse nome e namespace. Isso permite que você adicione facilmente todos os tipos em um assembly para a coleção sem se preocupar duplicatas para tipos que ocorrem no esquema.  
  
 O `ReferencedTypes` propriedade corresponde do **/Reference** alternar em certos modos de operação da ferramenta Svcutil.exe.  
  
> [!NOTE]
>  Ao usar o Svcutil.exe ou (no [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]) o **adicionar referência de serviço** ferramentas, todos os tipos de mscorlib. dll serão automaticamente referenciadas.  
  
#### <a name="import-options-importing-non-datacontract-schema-as-ixmlserializable-types"></a>Opções de importação: Importando esquema não DataContract como IXmlSerializable tipos  
 O <xref:System.Runtime.Serialization.XsdDataContractImporter> oferece suporte a um subconjunto limitado do esquema. Se houver construções de esquema sem suporte (por exemplo, os atributos XML), a tentativa de importação falhará com uma exceção. No entanto, definindo o <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> propriedade `true` estende o intervalo de esquema com suporte. Quando definido como `true`, o <xref:System.Runtime.Serialization.XsdDataContractImporter> gera tipos que implementam o <xref:System.Xml.Serialization.IXmlSerializable> interface. Isso permite o acesso direto a representação XML desses tipos.  
  
##### <a name="design-considerations"></a>Considerações de design  
  
-   Pode ser difícil trabalhar diretamente com a representação XML sem rigidez de tipos. Considere o uso de um mecanismo de serialização alternativo, como o <xref:System.Xml.Serialization.XmlSerializer>, para trabalhar com o esquema não é compatível com dados contratos de maneira fortemente tipada. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Usando a classe XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).  
  
-   Algumas construções de esquema não podem ser importadas pelo <xref:System.Runtime.Serialization.XsdDataContractImporter> mesmo quando o <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> está definida como `true`. Novamente, considere usar o <xref:System.Xml.Serialization.XmlSerializer> para esses casos.  
  
-   Suporte para as construções de esquema exatos que são ambos quando <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> é `true` ou `false` são descritos na [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
-   Gerar esquema para <xref:System.Xml.Serialization.IXmlSerializable> tipos não mantém a fidelidade quando importados e exportados. Ou seja, exportar o esquema dos tipos gerados e importar classes não retornam o esquema original.  
  
 É possível combinar o <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> opção com o <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> opção descrita anteriormente. Para tipos que devem ser gerados como <xref:System.Xml.Serialization.IXmlSerializable> implementações, a verificação estrutural é ignorada ao usar o <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> recurso.  
  
 O <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> opção corresponde do **/importXmlTypes** ativar a ferramenta Svcutil.exe.  
  
##### <a name="working-with-generated-ixmlserializable-types"></a>Trabalhando com tipos de IXmlSerializable gerado  
 Gerado `IXmlSerializable` tipos contêm um campo particular, denominado "nodesField", que retorna uma matriz de <xref:System.Xml.XmlNode> objetos. Ao desserializar uma instância de um tipo como esse, você pode acessar os dados XML diretamente por meio do campo usando o modelo de objeto de documento XML. Ao serializar uma instância desse tipo, você pode definir este campo para os dados XML desejados e ela será serializada.  
  
 Isso é feito por meio de `IXmlSerializable` implementação. Em gerado `IXmlSerializable` tipo, o <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> chamadas de implementação de <xref:System.Runtime.Serialization.XmlSerializableServices.ReadNodes%2A> método do <xref:System.Runtime.Serialization.XmlSerializableServices> classe. O método é um método auxiliar que converte XML fornecido por meio de um <xref:System.Xml.XmlReader> para uma matriz de <xref:System.Xml.XmlNode> objetos. O <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> implementação não o oposto e converte a matriz de `XmlNode` objetos em uma sequência de <xref:System.Xml.XmlWriter> chamadas. Isso é feito usando o <xref:System.Runtime.Serialization.XmlSerializableServices.WriteNodes%2A> método.  
  
 É possível executar o processo de exportação de esquema no gerado `IXmlSerializable` classes. Como foi mencionado anteriormente, você não obterá o esquema original novamente. Em vez disso, você obterá o "anyType" padrão tipo XSD, que é um caractere curinga para qualquer tipo XSD.  
  
 Isso é feito aplicando o <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atributo gerado `IXmlSerializable` classes e especificar um método que chama o <xref:System.Runtime.Serialization.XmlSerializableServices.AddDefaultSchema%2A> método para gerar o tipo "anyType".  
  
> [!NOTE]
>  O <xref:System.Runtime.Serialization.XmlSerializableServices> tipo existe somente para dar suporte a esse recurso em particular. Não é recomendável para uso para qualquer outra finalidade.  
  
#### <a name="import-options-advanced-options"></a>Opções de importação: Opções avançadas  
 A seguir é opções avançado de importação:  
  
-   <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A>propriedade. Especifique o <xref:System.CodeDom.Compiler.CodeDomProvider> a ser usado para gerar o código para as classes geradas. O mecanismo de importação tenta evitar recursos que o <xref:System.CodeDom.Compiler.CodeDomProvider> não oferece suporte. Se o <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> não estiver definida, o conjunto completo de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] recursos é usado sem restrições.  
  
-   <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A>propriedade. Um <xref:System.Runtime.Serialization.IDataContractSurrogate> implementação pode ser especificada com essa propriedade. O <xref:System.Runtime.Serialization.IDataContractSurrogate> personaliza o processo de importação. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Substitutos de contrato de dados](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Por padrão, não há substituto é usado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 <xref:System.Runtime.Serialization.XsdDataContractExporter>  
 <xref:System.Runtime.Serialization.ImportOptions>  
 [Referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 [Substitutos de contrato de dados](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)  
 [Exportação e importação de esquema](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)  
 [Exportando esquemas de Classes](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)  
 [Referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)
