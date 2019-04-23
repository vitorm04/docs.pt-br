---
title: Importando esquema para gerar classes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractImporter class
ms.assetid: b9170583-8c34-43bd-97bb-6c0c8dddeee0
ms.openlocfilehash: 68890a5d86d2781e3c8079c86e941144e3796ea6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228582"
---
# <a name="importing-schema-to-generate-classes"></a>Importando esquema para gerar classes
Para gerar classes de esquemas que podem ser usadas com o Windows Communication Foundation (WCF), use o <xref:System.Runtime.Serialization.XsdDataContractImporter> classe. Este tópico descreve o processo e variações.  
  
## <a name="the-import-process"></a>O processo de importação
 O processo de importação de esquema começa com um <xref:System.Xml.Schema.XmlSchemaSet> e produz um <xref:System.CodeDom.CodeCompileUnit>.  
  
 O `XmlSchemaSet` é uma parte do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]do modelo de objeto de esquema (SOM) que representa um conjunto de documentos de esquema XSD (linguagem) de definição de esquema XML. Para criar uma `XmlSchemaSet` do objeto de um conjunto de documentos XSD, desserializar cada documento em um <xref:System.Xml.Schema.XmlSchema> objeto (usando o <xref:System.Xml.Serialization.XmlSerializer>) e adicione esses objetos para um novo `XmlSchemaSet`.  
  
 O `CodeCompileUnit` faz parte do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]do Code Document Object Model (CodeDOM) que representa [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] código de uma maneira abstrata. Para gerar o código real de um `CodeCompileUnit`, use uma subclasse do <xref:System.CodeDom.Compiler.CodeDomProvider> classe, como o <xref:Microsoft.CSharp.CSharpCodeProvider> ou <xref:Microsoft.VisualBasic.VBCodeProvider> classe.  
  
### <a name="to-import-a-schema"></a>Para importar um esquema  
  
1. Criar uma instância da <xref:System.Runtime.Serialization.XsdDataContractImporter>.  
  
2. Opcional. Passar um `CodeCompileUnit` no construtor. Os tipos gerados durante a importação de esquema são adicionados a este `CodeCompileUnit` instância em vez de começar com um espaço em branco `CodeCompileUnit`.  
  
3. Opcional. Chame um do <xref:System.Runtime.Serialization.XsdDataContractImporter.CanImport%2A> métodos. O método determina se o esquema fornecido é um esquema de contrato de dados válido e pode ser importado. O `CanImport` método tem as mesmas sobrecargas como `Import` (a próxima etapa).  
  
4. Chame um dos sobrecarregado `Import` métodos, por exemplo, o <xref:System.Runtime.Serialization.XsdDataContractImporter.Import%28System.Xml.Schema.XmlSchemaSet%29> método.  
  
     A sobrecarga mais simples aceita um `XmlSchemaSet` e importa todos os tipos, incluindo tipos anônimos, encontrados no conjunto de esquema. Outras sobrecargas permitem que você especifique o tipo XSD ou uma lista de tipos para importar (na forma de um <xref:System.Xml.XmlQualifiedName> ou uma coleção de `XmlQualifiedName` objetos). Nesse caso, apenas os tipos especificados são importados. Uma sobrecarga toma um <xref:System.Xml.Schema.XmlSchemaElement> que importa um elemento específico do `XmlSchemaSet`, bem como seu tipo associado (se ele é anônimo ou não). Essa sobrecarga retorna um `XmlQualifiedName`, que representa o nome do contrato de dados do tipo gerado para esse elemento.  
  
     Diversas chamadas do `Import` resultado do método em vários itens que estão sendo adicionadas à mesma `CodeCompileUnit`. Um tipo não é gerado para o `CodeCompileUnit` se ele já existe. Chame `Import` várias vezes na mesma `XsdDataContractImporter` em vez de usar vários `XsdDataContractImporter` objetos. Isso é a maneira recomendada para evitar tipos duplicados que está sendo gerados.  
  
    > [!NOTE]
    > Se houver uma falha durante a importação, o `CodeCompileUnit` estará em um estado imprevisível. Usando um `CodeCompileUnit` resultante de uma importação com falha pode expô-lo às vulnerabilidades de segurança.  
  
5. Acesso a `CodeCompileUnit` por meio de <xref:System.Runtime.Serialization.XsdDataContractImporter.CodeCompileUnit%2A> propriedade.  
  
### <a name="import-options-customizing-the-generated-types"></a>Opções de importação: Personalizando os tipos gerados  
 Você pode definir as <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> propriedade do <xref:System.Runtime.Serialization.XsdDataContractImporter> a uma instância da <xref:System.Runtime.Serialization.ImportOptions> classe para controlar vários aspectos do processo de importação. Várias opções de influenciam diretamente os tipos que são gerados.  
  
#### <a name="controlling-the-access-level-generateinternal-or-the-internal-switch"></a>Controlar o nível de acesso (GenerateInternal ou / interno alternar)  
 Isso corresponde à **/ interno** ligar a [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 Normalmente, os tipos públicos são gerados de esquema, com campos particulares e propriedades de membro de dados públicos correspondentes. Para gerar tipos internos em vez disso, defina as <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> propriedade para `true`.  
  
 O exemplo a seguir mostra um esquema transformado em interna quando o <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> estiver definida como `true.`  
  
 [!code-csharp[c_SchemaImportExport#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#2)]
 [!code-vb[c_SchemaImportExport#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#2)]  
  
#### <a name="controlling-namespaces-namespaces-or-the-namespace-switch"></a>Controlando Namespaces (Namespaces ou u parametru /namespace alternar)  
 Isso corresponde à **/namespace** ative o `Svcutil.exe` ferramenta.  
  
 Normalmente, os tipos gerados de esquema são gerados em [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] namespaces, sendo que cada namespace XSD correspondente a um determinado [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] namespace de acordo com um mapeamento descrito em [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Você pode personalizar esse mapeamento, o <xref:System.Runtime.Serialization.ImportOptions.Namespaces%2A> propriedade para um <xref:System.Collections.Generic.Dictionary%602>. Se um determinado namespace XSD for encontrado no dicionário, a correspondência [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] namespace também é obtido do seu dicionário.  
  
 Por exemplo, considere o esquema a seguir.  
  
 [!code-xml[c_SchemaImportExport#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#10)]  
  
 O exemplo a seguir usa o `Namespaces` propriedade para mapear o `http://schemas.contoso.com/carSchema` namespace para "Contoso.Cars".  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
#### <a name="adding-the-serializableattribute-generateserializable-or-the-serializable-switch"></a>Adicionando o SerializableAttribute (GenerateSerializable ou / serializável alternar)  
 Isso corresponde à **/ serializável** ative o `Svcutil.exe` ferramenta.  
  
 Às vezes, é importante para os tipos gerados a partir do esquema a ser usado com [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] mecanismos de serialização de tempo de execução (por exemplo, o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> e o <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes). Isso é útil ao usar tipos para [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] comunicação remota. Para habilitar isso, você deve aplicar a <xref:System.SerializableAttribute> de atributo para os tipos gerados, além de regulares <xref:System.Runtime.Serialization.DataContractAttribute> atributo. O atributo é gerado automaticamente se o `GenerateSerializable` opção de importação é definida como `true`.  
  
 A exemplo a seguir mostra a `Vehicle` classe gerada com o `GenerateSerializable` importar opção definida como `true`.  
  
 [!code-csharp[c_SchemaImportExport#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#4)]
 [!code-vb[c_SchemaImportExport#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#4)]  
  
#### <a name="adding-data-binding-support-enabledatabinding-or-the-enabledatabinding-switch"></a>Adicionando suporte a associação de dados (EnableDataBinding ou a opção /enableDataBinding)  
 Isso corresponde do **/enableDataBinding** alternar da ferramenta Svcutil.exe.  
  
 Às vezes, você talvez queira associar os tipos gerados do esquema de componentes da interface gráfica do usuário para que qualquer atualização às instâncias desses tipos atualizará automaticamente a interface do usuário. O `XsdDataContractImporter` pode gerar os tipos que implementam o <xref:System.ComponentModel.INotifyPropertyChanged> interface de tal forma que qualquer alteração de propriedade dispara um evento. Se você estiver gerando tipos para uso com um ambiente de programação de interface do usuário de cliente que dá suporte a essa interface (como Windows Presentation Foundation (WPF)), defina as <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> propriedade para `true` para habilitar esse recurso.  
  
 A exemplo a seguir mostra a `Vehicle` classe gerada com o <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> definido como `true`.  
  
 [!code-csharp[C_SchemaImportExport#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#5)]
 [!code-vb[C_SchemaImportExport#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#5)]  
  
### <a name="import-options-choosing-collection-types"></a>Opções de importação: Escolher tipos de coleção  
 Dois padrões especiais em XML representam coleções de itens: listas de itens e as associações entre um item e outro. O exemplo a seguir é um exemplo de uma lista de cadeias de caracteres.  
  
 [!code-xml[C_SchemaImportExport#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#11)]  
  
 A seguir está um exemplo de uma associação entre uma cadeia de caracteres e um número inteiro (`city name` e `population`).  
  
 [!code-xml[C_SchemaImportExport#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#12)]  
  
> [!NOTE]
>  Qualquer associação também poderia ser considerada uma lista. Por exemplo, você pode exibir a associação anterior como uma lista de complexo `city` objetos que têm dois campos (um campo de cadeia de caracteres e um campo de inteiro). Ambos os padrões têm uma representação no esquema XSD. Não há nenhuma maneira de diferenciar entre uma lista e uma associação, portanto, esses padrões são tratados sempre como listas, a menos que uma anotação especial específica para o WCF está presente no esquema. A anotação indica que um determinado padrão representa uma associação. Para obter mais informações, consulte [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Normalmente, uma lista é importada como um contrato de dados de coleção que é derivada de uma lista genérica ou como um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] array, dependendo se o esquema segue o padrão de nomenclatura padrão para coleções. Isso é descrito mais detalhadamente [tipos de coleção em contratos de dados](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). Associações são normalmente importadas como um <xref:System.Collections.Generic.Dictionary%602> ou um contrato de dados de coleção que é derivada do objeto de dicionário. Por exemplo, considere o esquema a seguir.  
  
 [!code-xml[c_SchemaImportExport#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#13)]  
  
 Isso seria importado da seguinte maneira (os campos são exibidos em vez de propriedades para facilitar a leitura).  
  
 [!code-csharp[c_SchemaImportExport#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#6)]
 [!code-vb[c_SchemaImportExport#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#6)]  
  
 É possível personalizar os tipos de coleção que são gerados para tais padrões de esquema. Por exemplo, você talvez queira gerar coleções derivam de <xref:System.ComponentModel.BindingList%601> em vez do <xref:System.Collections.Generic.List%601> classe para associar o tipo a uma caixa de listagem e que ele seja atualizado automaticamente quando o conteúdo da coleção é alterado. Para fazer isso, defina as <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> propriedade do <xref:System.Runtime.Serialization.ImportOptions> classe a uma lista dos tipos de coleção a ser usado (daqui em diante conhecidos como tipos referenciados). Ao importar qualquer coleção, essa lista de tipos de coleção referenciado é examinada e a coleção de fallback de melhor correspondência é usada se um for encontrado. Associações são comparadas somente com tipos que implementam o genérico ou não genérica <xref:System.Collections.IDictionary> interface, enquanto as listas são comparadas com qualquer tipo de coleção com suporte.  
  
 Por exemplo, se o <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> estiver definida como uma <xref:System.ComponentModel.BindingList%601>, o `people` tipo no exemplo anterior é gerado da seguinte maneira.  
  
 [!code-csharp[C_SchemaImportExport#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#7)]
 [!code-vb[C_SchemaImportExport#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#7)]  
  
 Um genérico fechado é considerado a melhor correspondência. Por exemplo, se os tipos `BindingList(Of Integer)` e <xref:System.Collections.ArrayList> são passados para a coleção de tipos referenciados, qualquer lista de inteiros encontrados no esquema é importada como um `BindingList(Of Integer)`. Quaisquer outras listas, por exemplo, uma `List(Of String)`, são importados como um `ArrayList`.  
  
 Se um tipo que implementa o genérico `IDictionary` interface é adicionada à coleção de tipos referenciados, seus parâmetros de tipo devem ser totalmente aberto ou totalmente fechada.  
  
 Não são permitidas duplicatas. Por exemplo, você não pode adicionar tanto uma `List(Of Integer)` e um `Collection(Of Integer)` para os tipos referenciados. Isso tornaria impossível determinar qual deve ser usado quando uma lista de inteiros é encontrada no esquema. As duplicatas serão detectadas somente se houver um tipo no esquema que expõe o problema de duplicatas. Por exemplo, se o esquema importado não contém listas de números inteiros, ele tem permissão para ter ambas as `List(Of Integer)` e o `Collection(Of Integer)` em tipos referenciados coleção, mas não terá qualquer efeito.  
  
 Os tipos de coleção referenciada mecanismo funciona igualmente bem para coleções de tipos complexos (incluindo coleções de outras coleções) e não apenas para coleções de primitivos.  
  
 O `ReferencedCollectionTypes` propriedade corresponde à **/collectionType** alternar da ferramenta SvcUtil.exe. Observe que, para fazer referência a vários tipos de coleção, o **/collectionType** switch deve ser especificado várias vezes. Se o tipo não estiver no mscorlib. dll, seu assembly também deve ser referenciado usando a **/Reference** alternar.  
  
#### <a name="import-options-referencing-existing-types"></a>Opções de importação: Fazendo referência a tipos existentes  
 Ocasionalmente, os tipos no esquema correspondem a existente [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos, e não é necessário para gerar esses tipos a partir do zero. (Esta seção se aplica somente aos tipos de noncollection. Para tipos de coleção, consulte a seção anterior.)  
  
 Por exemplo, você pode ter um padrão em toda a empresa "Person" tipo de contrato que você deseja sempre usado ao representar uma pessoa. Sempre que algum serviço faz uso desse tipo e seu esquema é exibida nos metadados de serviço, talvez você queira reutilizar existente `Person` digite ao importar esse esquema em vez de gerar um novo para cada serviço.  
  
 Para fazer isso, passe uma lista de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos que você deseja reutilizar na coleção de <xref:System.Runtime.Serialization.ImportOptions.ReferencedTypes%2A> propriedade retorna o <xref:System.Runtime.Serialization.ImportOptions> classe. Se qualquer um desses tipos tem um nome de contrato de dados e o namespace que corresponde ao nome e namespace de um tipo de esquema, é executada uma comparação estrutural. Se for determinado que os tipos têm nomes correspondentes e estruturas de correspondência, existente [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipo é reutilizado em vez de gerar um novo. Se apenas o nome corresponder, mas não a estrutura, uma exceção é lançada. Observe que não há nenhuma provisão para controle de versão ao referenciar tipos (por exemplo, adicionando novos dados opcionais membros). As estruturas devem corresponder exatamente.  
  
 É válido para adicionar vários tipos com o mesmo nome de contrato de dados e o namespace para a coleção de tipos referenciados, desde que nenhum tipo de esquema é importado com esse nome e namespace. Isso permite que você adicione facilmente todos os tipos em um assembly para a coleção sem se preocupar com as duplicatas para tipos que não ocorram, na verdade, no esquema.  
  
 O `ReferencedTypes` propriedade corresponde à **/Reference** alternar em determinados modos de operação da ferramenta Svcutil.exe.  
  
> [!NOTE]
>  Ao usar o Svcutil.exe ou (no Visual Studio) a **adicionar referência de serviço** ferramentas, todos os tipos em mscorlib. dll são referenciadas automaticamente.  
  
#### <a name="import-options-importing-non-datacontract-schema-as-ixmlserializable-types"></a>Opções de importação: Importando o esquema de não DataContract como IXmlSerializable tipos  
 O <xref:System.Runtime.Serialization.XsdDataContractImporter> dá suporte a um subconjunto limitado do esquema. Se houver construções de esquema sem suporte (por exemplo, os atributos XML), a tentativa de importação falhará com uma exceção. No entanto, definir a <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> propriedade para `true` estenderá o intervalo de esquema com suporte. Quando definido como `true`, o <xref:System.Runtime.Serialization.XsdDataContractImporter> gera tipos que implementam o <xref:System.Xml.Serialization.IXmlSerializable> interface. Isso permite acesso direto a representação XML desses tipos.  
  
##### <a name="design-considerations"></a>Considerações de design  
  
-   Pode ser difícil trabalhar diretamente com a representação XML sem rigidez de tipos. Considere o uso de um mecanismo de serialização alternativo, como o <xref:System.Xml.Serialization.XmlSerializer>, para trabalhar com o esquema não é compatível com dados contratos de uma forma fortemente tipada. Para obter mais informações, consulte [usando a classe XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).  
  
-   Algumas construções de esquema não podem ser importadas pela <xref:System.Runtime.Serialization.XsdDataContractImporter> mesmo quando o <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> estiver definida como `true`. Novamente, considere usar o <xref:System.Xml.Serialization.XmlSerializer> para esses casos.  
  
-   Suporte para as construções de esquema exatos que são ambos quando <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> está `true` ou `false` descritos nos [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
-   Para o esquema gerado <xref:System.Xml.Serialization.IXmlSerializable> tipos não mantém a fidelidade quando importados e exportados. Ou seja, exportando o esquema dos tipos gerados e importando como classes não retornam o esquema original.  
  
 É possível combinar as <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> a opção com o <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> opção descrita anteriormente. Para tipos que devem ser gerados como <xref:System.Xml.Serialization.IXmlSerializable> implementações, a verificação estrutural é ignorada ao usar o <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> recurso.  
  
 O <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> opção corresponde à **/importXmlTypes** alternar da ferramenta Svcutil.exe.  
  
##### <a name="working-with-generated-ixmlserializable-types"></a>Trabalhando com tipos IXmlSerializable gerado  
 Gerado `IXmlSerializable` tipos contêm um campo privado, denominado "nodesField", que retorna uma matriz de <xref:System.Xml.XmlNode> objetos. Ao desserializar uma instância desse tipo, você pode acessar os dados XML diretamente por meio desse campo usando o modelo de objeto do documento XML. Ao serializar uma instância desse tipo, você pode definir esse campo para os dados XML desejados e ela será serializada.  
  
 Isso é feito por meio de `IXmlSerializable` implementação. No gerado `IXmlSerializable` tipo, o <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> implementação chama o <xref:System.Runtime.Serialization.XmlSerializableServices.ReadNodes%2A> método da <xref:System.Runtime.Serialization.XmlSerializableServices> classe. O método é um método auxiliar que converte o XML fornecido por meio de um <xref:System.Xml.XmlReader> para uma matriz de <xref:System.Xml.XmlNode> objetos. O <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> faz o oposto de implementação e converte a matriz de `XmlNode` objetos em uma sequência de <xref:System.Xml.XmlWriter> chamadas. Isso é feito usando o <xref:System.Runtime.Serialization.XmlSerializableServices.WriteNodes%2A> método.  
  
 É possível executar o processo de exportação de esquema no gerado `IXmlSerializable` classes. Como mencionado anteriormente, você não obterá o esquema original. Em vez disso, você obterá o "anyType" standard tipo XSD, que é um caractere curinga para qualquer tipo XSD.  
  
 Isso é feito por meio da aplicação do <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atributo gerado `IXmlSerializable` classes e especificando um método que chama o <xref:System.Runtime.Serialization.XmlSerializableServices.AddDefaultSchema%2A> método para gerar o tipo de "anyType".  
  
> [!NOTE]
>  O <xref:System.Runtime.Serialization.XmlSerializableServices> tipo existe somente para dar suporte a esse recurso em particular. Ele não é recomendado para uso para qualquer outra finalidade.  
  
#### <a name="import-options-advanced-options"></a>Opções de importação: Opções avançadas  
 A seguir é opções avançadas de importação:  
  
-   Propriedade <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A>. Especifique o <xref:System.CodeDom.Compiler.CodeDomProvider> usar para gerar o código para as classes geradas. O mecanismo de importação tenta evitar recursos que o <xref:System.CodeDom.Compiler.CodeDomProvider> não oferece suporte. Se o <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> não for definido, o conjunto completo de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] recursos é usado sem restrições.  
  
-   Propriedade <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A>. Um <xref:System.Runtime.Serialization.IDataContractSurrogate> implementação pode ser especificada com essa propriedade. O <xref:System.Runtime.Serialization.IDataContractSurrogate> personaliza o processo de importação. Para obter mais informações, consulte [substitutos de contrato de dados](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Por padrão, não há substituto é usado.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- <xref:System.Runtime.Serialization.ImportOptions>
- [Referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)
- [Alternativas de contrato de dados](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)
- [Exportação e importação de esquema](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)
- [Exportando esquemas de Classes](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)
- [Referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)
