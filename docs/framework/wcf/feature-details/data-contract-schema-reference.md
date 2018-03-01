---
title: "Referência de esquema de contrato de dados"
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
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 57ccc812aab5df0a9acd99bdcde327d56e4bad8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="data-contract-schema-reference"></a>Referência de esquema de contrato de dados
Este tópico descreve o subconjunto do esquema XML (XSD) usado pelo <xref:System.Runtime.Serialization.DataContractSerializer> para descrever o common language runtime (CLR) tipos de serialização de XML.  
  
## <a name="datacontractserializer-mappings"></a>Mapeamentos de DataContractSerializer  
 O `DataContractSerializer` mapeia tipos CLR para XSD quando metadados exportado de um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usando um ponto de extremidade de metadados de serviço ou o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).  
  
 O `DataContractSerializer` também mapeia XSD para tipos CLR quando Svcutil.exe é usada para acessar documentos WSDL Web Services Description Language () ou XSD e gerar contratos de dados para serviços ou clientes.  
  
 Somente as instâncias de esquema XML que atendem aos requisitos mencionados neste documento podem ser mapeadas para tipos CLR usando `DataContractSerializer`.  
  
### <a name="support-levels"></a>Níveis de suporte  
 O `DataContractSerializer` fornece os seguintes níveis de suporte para um determinado recurso de esquema XML:  
  
-   **Suporte para**. Não há mapeamento explícito de usar esse recurso CLR tipos ou atributos (ou ambos) `DataContractSerializer`.  
  
-   **Ignorado**. O recurso é permitido em esquemas importadas pela `DataContractSerializer`, mas não tem nenhum efeito na geração de código.  
  
-   **Proibido**. O `DataContractSerializer` não oferece suporte à importação de um esquema usando o recurso. Por exemplo, Svcutil.exe, ao acessar um WSDL com um esquema que usa o recurso, volte a usar o <xref:System.Xml.Serialization.XmlSerializer> em vez disso. Isso ocorre por padrão.  
  
## <a name="general-information"></a>Informações gerais  
  
-   O namespace do esquema é descrito em [esquema XML](http://go.microsoft.com/fwlink/?LinkId=95475). O prefixo "xs" é usado neste documento.  
  
-   Todos os atributos com um namespace do esquema não são ignorados.  
  
-   Quaisquer anotações (exceto as descritas neste documento) são ignoradas.  
  
### <a name="xsschema-attributes"></a>\<xs: schema >: atributos  
  
|Atributo|DataContract|  
|---------------|------------------|  
|`attributeFormDefault`|Ignorado.|  
|`blockDefault`|Ignorado.|  
|`elementFormDefault`|Deve ser qualificado. Todos os elementos devem ser qualificados para um esquema para serem suportados por `DataContractSerializer`. Isso pode ser feito configurando xs:schema/@elementFormDefault "qualified" ou definindo xs:element/@form como "qualified" na declaração de cada elemento individual.|  
|`finalDefault`|Ignorado.|  
|`Id`|Ignorado.|  
|`targetNamespace`|Suporte e mapeado para o namespace de contrato de dados. Se esse atributo não for especificado, o namespace em branco será usado. Não é possível http://schemas.microsoft.com/2003/10/Serialization/ o namespace reservado.|  
|`version`|Ignorado.|  
  
### <a name="xsschema-contents"></a>\<xs: schema >: conteúdo  
  
|Conteúdo|Esquema|  
|--------------|------------|  
|`include`|Com suporte. `DataContractSerializer`dá suporte a xs: incluir e xs:import. No entanto, o Svcutil.exe restringe seguir `xs:include/@schemaLocation` e `xs:import/@location` referencia quando metadados é carregado de um arquivo local. A lista de arquivos de esquema deve ser passada por meio de um mecanismo fora de banda e não por `include` nesse caso; `include`documentos de esquema d são ignorados.|  
|`redefine`|Negado. O uso de `xs:redefine` é proibida pelo `DataContractSerializer` por motivos de segurança: `x:redefine` requer `schemaLocation` ser seguidas. Em determinadas circunstâncias, Svcutil.exe usando DataContract restringe o uso de `schemaLocation`.|  
|`import`|Com suporte. `DataContractSerializer`dá suporte a `xs:include` e `xs:import`. No entanto, o Svcutil.exe restringe seguir `xs:include/@schemaLocation` e `xs:import/@location` referencia quando metadados é carregado de um arquivo local. A lista de arquivos de esquema deve ser passada por meio de um mecanismo fora de banda e não por `include` nesse caso; `include`documentos de esquema d são ignorados.|  
|`simpleType`|Com suporte. Consulte o `xs:simpleType` seção.|  
|`complexType`|Suporte de mapas para contratos de dados. Consulte o `xs:complexType` seção.|  
|`group`|Ignorado. `DataContractSerializer`não suporta o uso de `xs:group`, `xs:attributeGroup`, e `xs:attribute`. Essas declarações são ignoradas como filhos do `xs:schema`, mas não pode ser referenciado no `complexType` ou outras construções com suporte.|  
|`attributeGroup`|Ignorado. `DataContractSerializer`não suporta o uso de `xs:group`, `xs:attributeGroup`, e `xs:attribute`. Essas declarações são ignoradas como filhos do `xs:schema`, mas não pode ser referenciado no `complexType` ou outras construções com suporte.|  
|`element`|Com suporte. Consulte a declaração de elemento Global (Buições).|  
|`attribute`|Ignorado. `DataContractSerializer`não suporta o uso de `xs:group`, `xs:attributeGroup`, e `xs:attribute`. Essas declarações são ignoradas como filhos do `xs:schema`, mas não pode ser referenciado no `complexType` ou outras construções com suporte.|  
|`notation`|Ignorado.|  
  
## <a name="complex-types--xscomplextype"></a>Tipos complexos – \<xs:complexType >  
  
### <a name="general-information"></a>Informações gerais  
 Cada tipo complexo \<xs:complexType > é mapeado para um contrato de dados.  
  
### <a name="xscomplextype-attributes"></a>\<xs:complexType >: atributos  
  
|Atributo|Esquema|  
|---------------|------------|  
|`abstract`|Deve ser false (padrão).|  
|`block`|Negado.|  
|`final`|Ignorado.|  
|`id`|Ignorado.|  
|`mixed`|Deve ser false (padrão).|  
|`name`|Suporte e mapeado para o nome do contrato de dados. Se houver pontos no nome, é feita uma tentativa para mapear o tipo para um tipo interno. Por exemplo, um tipo complexo chamado `A.B` é mapeado para um contrato de dados tipo que é um tipo interno de um tipo com o nome de contrato de dados `A`, mas somente se o tipo de contrato de tal um tipo de dados existe. Mais de um nível de aninhamento é possível: por exemplo, `A.B.C` pode ser um tipo interno, mas somente se `A` e `A.B` existem.|  
  
### <a name="xscomplextype-contents"></a>\<xs:complexType >: conteúdo  
  
|Conteúdo|Esquema|  
|--------------|------------|  
|`simpleContent`|As extensões são proibidas.<br /><br /> Restrição só é permitida em `anySimpleType`.|  
|`complexContent`|Com suporte. Consulte "Herança".|  
|`group`|Negado.|  
|`all`|Negado.|  
|`choice`|Proibido|  
|`sequence`|Suporte de mapas para os membros de dados de um contrato de dados.|  
|`attribute`|Proibido, mesmo que use = "prohibited" (com uma exceção). Há suporte para apenas os atributos opcionais do namespace do esquema padrão de serialização. Eles não são mapeados para os membros de dados no modelo de programação de contrato de dados. Atualmente, apenas um desses atributos tem um significado e é discutido na seção de ISerializable. Todos os outros são ignorados.|  
|`attributeGroup`|Negado. No [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] versão v1, `DataContractSerializer` ignora a presença de `attributeGroup` em `xs:complexType`.|  
|`anyAttribute`|Negado.|  
|(vazio)|Mapeia para um contrato de dados com nenhum membro de dados.|  
  
### <a name="xssequence-in-a-complex-type-attributes"></a>\<xs: sequence > em um tipo complexo: atributos  
  
|Atributo|Esquema|  
|---------------|------------|  
|`id`|Ignorado.|  
|`maxOccurs`|Deve ser 1 (padrão).|  
|`minOccurs`|Deve ser 1 (padrão).|  
  
### <a name="xssequence-in-a-complex-type-contents"></a>\<xs: sequence > em um tipo complexo: conteúdo  
  
|Conteúdo|Esquema|  
|--------------|------------|  
|`element`|Cada instância é mapeado para um membro de dados.|  
|`group`|Negado.|  
|`choice`|Negado.|  
|`sequence`|Negado.|  
|`any`|Negado.|  
|(vazio)|Mapeia para um contrato de dados com nenhum membro de dados.|  
  
## <a name="elements--xselement"></a>Elementos – \<xs: element >  
  
### <a name="general-information"></a>Informações gerais  
 `<xs:element>`pode ocorrer nos seguintes contextos:  
  
-   Pode ocorrer dentro de um `<xs:sequence>`, que descreve um membro de dados de um contrato de dados (não coleta) regular. Nesse caso, o `maxOccurs` atributo deve ser 1. (Um valor de 0 não é permitido).  
  
-   Pode ocorrer dentro de um `<xs:sequence>`, que descreve um membro de dados de um contrato de dados da coleção. Nesse caso, o `maxOccurs` atributo deve ser maior que 1 ou "unbounded".  
  
-   Pode ocorrer dentro de um `<xs:schema>` como uma declaração de elemento Global (Buições).  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a>\<xs: element > com maxOccurs = 1 dentro de um \<xs: sequence > (membros de dados)  
  
|Atributo|Esquema|  
|---------------|------------|  
|`ref`|Negado.|  
|`name`|Suporte, é mapeado para o nome do membro de dados.|  
|`type`|Mapeia para o membro de dados com suporte, digite. Para obter mais informações, consulte o mapeamento de tipo/primitivo. Se não especificado (e o elemento não contém um tipo anônimo), `xs:anyType` será assumido.|  
|`block`|Ignorado.|  
|`default`|Negado.|  
|`fixed`|Negado.|  
|`form`|Deve ser qualificado. Esse atributo pode ser definido por meio de `elementFormDefault` em `xs:schema`.|  
|`id`|Ignorado.|  
|`maxOccurs`|1|  
|`minOccurs`|Mapeia para o <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> propriedade de um membro de dados (`IsRequired` é verdadeiro quando `minOccurs` é 1).|  
|`nillable`|Mapeamento de tipo afeta. Consulte o mapeamento de tipo/primitivo.|  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a>\<xs: element > com maxOccurs > 1 dentro de um \<xs: sequence > (coleções)  
  
-   Mapeia para um <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.  
  
-   Em tipos de coleção, xs: element somente uma é permitida dentro de um xs: sequence.  
  
 Coleções podem ser dos seguintes tipos:  
  
-   Coleções regulares (por exemplo, matrizes).  
  
-   Coleções de dicionário (um valor de mapeamento; por exemplo, um <xref:System.Collections.Hashtable>).  
  
-   É a única diferença entre um dicionário e uma matriz de um tipo de par chave/valor no modelo de programação gerado. Há um mecanismo de anotação de esquema que pode ser usado para indicar que um determinado tipo é uma coleção de dicionário.  
  
 As regras para o `ref`, `block`, `default`, `fixed`, `form`, e `id` atributos são as mesmas para o caso de não coleção. Outros atributos incluem aqueles na tabela a seguir.  
  
|Atributo|Esquema|  
|---------------|------------|  
|`name`|Com suporte, é mapeado para o <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> propriedade o `CollectionDataContractAttribute` atributo.|  
|`type`|Suporte, mapeia para o tipo armazenado na coleção.|  
|`maxOccurs`|Maior que 1 ou "unbounded". O esquema do controlador de domínio deve usar "unbounded".|  
|`minOccurs`|Ignorado.|  
|`nillable`|Mapeamento de tipo afeta. Esse atributo é ignorado para coleções de dicionário.|  
  
### <a name="xselement-within-an-xsschema-global-element-declaration"></a>\<xs: element > dentro de um \<xs: schema > declaração de elemento Global  
  
-   Um Global elemento declaração (Buições) que tem o mesmo nome e namespace como um tipo no esquema, ou que define um tipo anônimo dentro do próprio, deve ser associado ao tipo.  
  
-   Exportação de esquema: GEDs associados são gerados para cada tipo gerado, simple e complexo.  
  
-   Serialização/desserialização: GEDs associados são usados como elementos raiz para o tipo.  
  
-   Importação de esquema: GEDs associados não são necessários e são ignorados se elas seguirão as regras a seguir (a menos que definem tipos).  
  
|Atributo|Esquema|  
|---------------|------------|  
|`abstract`|Deve ser falsa para GEDs associados.|  
|`block`|Proibido no GEDs associados.|  
|`default`|Proibido no GEDs associados.|  
|`final`|Deve ser falsa para GEDs associados.|  
|`fixed`|Proibido no GEDs associados.|  
|`id`|Ignorado.|  
|`name`|Com suporte. Consulte a definição de GEDs associados.|  
|`nillable`|Deve ser verdadeiro para GEDs associados.|  
|`substitutionGroup`|Proibido no GEDs associados.|  
|`type`|Suporte e devem corresponder o tipo associado para GEDs associados (a menos que o elemento contém um tipo anônimo).|  
  
### <a name="xselement-contents"></a>\<xs: element >: conteúdo  
  
|Conteúdo|Esquema|  
|--------------|------------|  
|`simpleType`|Supported.*|  
|`complexType`|Supported.*|  
|`unique`|Ignorado.|  
|`key`|Ignorado.|  
|`keyref`|Ignorado.|  
|(blank)|Com suporte.|  
  
 \*Ao usar o `simpleType` e `complexType,` mapeamento para tipos anônimos é o mesmo para tipos não anônimo, exceto que não há nenhum contrato de dados anônimos e, portanto, um contrato de dados nomeado é criado, com um nome gerado derivado do nome do elemento. As regras para tipos anônimos estão na lista a seguir:  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]detalhes de implementação: se o `xs:element` nome não contém pontos, o tipo anônimo é mapeado para um tipo interno do tipo de contrato de dados externa. Se o nome contiver períodos, o tipo de contrato de dados resultante é independente (não um tipo interno).  
  
-   O nome do contrato de dados gerados de tipo interno é o nome do contrato de dados do tipo externo seguido por um período, o nome do elemento e a cadeia de caracteres "Type".  
  
-   Se um dado contrato com esse nome já existir, o nome é feito exclusivo, acrescentando "1", "2", "3", e assim por diante, até que um nome exclusivo é criado.  
  
## <a name="simple-types---xssimpletype"></a>Tipos simples - \<xs:simpleType >  
  
### <a name="xssimpletype-attributes"></a>\<xs:simpleType >: atributos  
  
|Atributo|Esquema|  
|---------------|------------|  
|`final`|Ignorado.|  
|`id`|Ignorado.|  
|`name`|Com suporte, mapeia para os dados de nome do contrato.|  
  
### <a name="xssimpletype-contents"></a>\<xs:simpleType >: conteúdo  
  
|Conteúdo|Esquema|  
|--------------|------------|  
|`restriction`|Com suporte. Mapeia para contratos de dados de enumeração. Esse atributo é ignorado se ele não corresponder ao padrão de enumeração. Consulte o `xs:simpleType` seção de restrições.|  
|`list`|Com suporte. Mapeia para contratos de dados de enumeração do sinalizador. Consulte o `xs:simpleType` listas de seção.|  
|`union`|Negado.|  
  
### <a name="xsrestriction"></a>\<xs: Restriction >  
  
-   Restrições de tipo complexo têm suporte apenas para base = "`xs:anyType`".  
  
-   Restrições de tipo simples de `xs:string` que não têm qualquer facetas de restrição que `xs:enumeration` são mapeados para os contratos de dados de enumeração.  
  
-   Todas as outras restrições de tipo simples são mapeadas para os tipos que eles restringem o. Por exemplo, uma restrição de `xs:int` é mapeado para um número inteiro, assim como `xs:int` does por si mesmo. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]tipo primitivo mapeamento, consulte o mapeamento de tipo/primitivo.  
  
### <a name="xsrestriction-attributes"></a>\<xs: Restriction >: atributos  
  
|Atributo|Esquema|  
|---------------|------------|  
|`base`|Deve ser um tipo simple com suporte ou `xs:anyType`.|  
|`id`|Ignorado.|  
  
### <a name="xsrestriction-for-all-other-cases-contents"></a>\<xs: Restriction > para todos os outros casos: conteúdo  
  
|Conteúdo|Esquema|  
|--------------|------------|  
|`simpleType`|Se estiver presente, deve ser derivado de um tipo primitivo com suporte.|  
|`minExclusive`|Ignorado.|  
|`minInclusive`|Ignorado.|  
|`maxExclusive`|Ignorado.|  
|`maxInclusive`|Ignorado.|  
|`totalDigits`|Ignorado.|  
|`fractionDigits`|Ignorado.|  
|`length`|Ignorado.|  
|`minLength`|Ignorado.|  
|`maxLength`|Ignorado.|  
|`enumeration`|Ignorado.|  
|`whiteSpace`|Ignorado.|  
|`pattern`|Ignorado.|  
|(blank)|Com suporte.|  
  
## <a name="enumeration"></a>Enumeração  
  
### <a name="xsrestriction-for-enumerations-attributes"></a>\<xs: Restriction > para enumerações: atributos  
  
|Atributo|Esquema|  
|---------------|------------|  
|`base`|Se estiver presente, deve ser `xs:string`.|  
|`id`|Ignorado.|  
  
### <a name="xsrestriction-for-enumerations-contents"></a>\<xs: Restriction > para enumerações: conteúdo  
  
|Conteúdo|Esquema|  
|--------------|------------|  
|`simpleType`|Se estiver presente, deve ser uma restrição de enumeração suportada pelo contrato de dados (Esta seção).|  
|`minExclusive`|Ignorado.|  
|`minInclusive`|Ignorado.|  
|`maxExclusive`|Ignorado.|  
|`maxInclusive`|Ignorado.|  
|`totalDigits`|Ignorado.|  
|`fractionDigits`|Ignorado.|  
|`length`|Negado.|  
|`minLength`|Negado.|  
|`maxLength`|Negado.|  
|`enumeration`|Com suporte. Enumeração "id" será ignorada e "valor" é mapeado para o nome do valor no contrato de dados de enumeração.|  
|`whiteSpace`|Negado.|  
|`pattern`|Negado.|  
|(vazio)|Suporte, mapeia para o tipo de enumeração vazia.|  
  
 O código a seguir mostra uma classe de enumeração do c#.  
  
```  
public enum MyEnum  
{  
   first = 3,  
   second = 4,  
   third =5  
```  
  
 }  
  
 Essa classe é mapeado para o esquema a seguir, o `DataContractSerializer`. Se os valores de enumeração iniciarem 1 `xs:annotation` blocos não são gerados.  
  
```xml  
<xs:simpleType name="MyEnum">  
<xs:restriction base="xs:string">  
 <xs:enumeration value="first">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     3  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
 <xs:enumeration value="second">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     4  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
</xs:restriction>  
</xs:simpleType>  
```  
  
### <a name="xslist"></a>\<Xs >  
 `DataContractSerializer`tipos de enumeração de mapas marcado com `System.FlagsAttribute` para `xs:list` derivado de `xs:string`. Nenhum outro `xs:list` variações têm suporte.  
  
### <a name="xslist-attributes"></a>\<Xs >: atributos  
  
|Atributo|Esquema|  
|---------------|------------|  
|`itemType`|Negado.|  
|`id`|Ignorado.|  
  
### <a name="xslist-contents"></a>\<Xs >: conteúdo  
  
|Conteúdo|Esquema|  
|--------------|------------|  
|`simpleType`|Deve ser a restrição de `xs:string` usando `xs:enumeration` faceta.|  
  
 Se o valor de enumeração não segue uma potência de 2 progressão (padrão para sinalizadores), o valor é armazenado no `xs:annotation/xs:appInfo/ser:EnumerationValue` elemento.  
  
 Por exemplo, o código a seguir indica um tipo de enumeração.  
  
```  
[Flags]  
public enum AuthFlags  
{    
  AuthAnonymous = 1,  
  AuthBasic = 2,  
  AuthNTLM = 4,  
  AuthMD5 = 16,  
  AuthWindowsLiveID = 64,  
}  
```  
  
 Esse tipo é mapeado para o esquema a seguir.  
  
```xml  
<xs:simpleType name="AuthFlags">  
    <xs:list>  
      <xs:simpleType>  
        <xs:restriction base="xs:string">  
          <xs:enumeration value="AuthAnonymous" />  
          <xs:enumeration value="AuthBasic" />  
          <xs:enumeration value="AuthNTLM" />  
          <xs:enumeration value="AuthMD5">  
            <xs:annotation>  
              <xs:appinfo>  
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">16</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
          <xs:enumeration value="AuthWindowsLiveID">  
            <xs:annotation>  
              <xs:appinfo>  
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">64</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:list>  
  </xs:simpleType>  
```  
  
## <a name="inheritance"></a>Herança  
  
### <a name="general-rules"></a>Regras gerais  
 Um contrato de dados pode herdar de outro contrato de dados. Esses contratos de dados mapear para uma base e são derivados por tipos de extensão usando o `<xs:extension>` construção de esquema XML.  
  
 Um contrato de dados não pode herdar de um contrato de dados da coleção.  
  
 Por exemplo, o código a seguir é um contrato de dados.  
  
```  
[DataContract]  
public class Person  
{  
  [DataMember]  
  public string Name;  
}  
[DataContract]  
public class Employee : Person   
{      
  [DataMember]  
  public int ID;  
}  
```  
  
 Este contrato de dados é mapeado para a declaração de tipo de esquema XML a seguir.  
  
```xml  
<xs:complexType name="Employee">  
 <xs:complexContent mixed="false">  
  <xs:extension base="tns:Person">  
   <xs:sequence>  
    <xs:element minOccurs="0" name="ID" type="xs:int"/>  
   </xs:sequence>  
  </xs:extension>  
 </xs:complexContent>  
</xs:complexType>  
<xs:complexType name="Person">  
 <xs:sequence>  
  <xs:element minOccurs="0" name="Name"   
    nillable="true" type="xs:string"/>  
 </xs:sequence>  
</xs:complexType>  
```  
  
### <a name="xscomplexcontent-attributes"></a>\<xs:complexContent >: atributos  
  
|Atributo|Esquema|  
|---------------|------------|  
|`id`|Ignorado.|  
|`mixed`|Deve ser false.|  
  
### <a name="xscomplexcontent-contents"></a>\<xs:complexContent >: conteúdo  
  
|Conteúdo|Esquema|  
|--------------|------------|  
|`restriction`|Proibido, exceto quando base = "`xs:anyType`". O segundo é equivalente a colocar o conteúdo do `xs:restriction` diretamente sob o contêiner do `xs:complexContent`.|  
|`extension`|Com suporte. Mapeia a herança de contrato de dados.|  
  
### <a name="xsextension-in-xscomplexcontent-attributes"></a>\<xs: Extension > em \<xs:complexContent >: atributos  
  
|Atributo|Esquema|  
|---------------|------------|  
|`id`|Ignorado.|  
|`base`|Com suporte. Mapeia para o contrato de dados base de tipo que esse tipo herda do.|  
  
### <a name="xsextension-in-xscomplexcontent-contents"></a>\<xs: Extension > em \<xs:complexContent >: conteúdo  
 As regras são os mesmos para `<xs:complexType>` conteúdo.  
  
 Se um `<xs:sequence>` for fornecido, o membro de elementos são mapeados para os membros de dados adicionais que estão presentes no contrato de dados derivado.  
  
 Se um tipo derivado contém um elemento com o mesmo nome que um elemento em um tipo base, a declaração de elemento duplicado mapeado para um membro de dados com um nome que é gerado para serem exclusivos. Números inteiros positivos são adicionados para o nome do membro de dados ("membro1", "membro2" e assim por diante) até encontra um nome exclusivo. Por outro lado:  
  
-   Se um contrato de dados derivado tem um membro com o mesmo nome e tipo de dados como um membro de dados em um contrato de dados base, `DataContractSerializer` gera este elemento correspondente no tipo derivado.  
  
-   Se um contrato de dados derivado tem um membro de dados com o mesmo nome como um membro de dados em um contrato de dados base, mas um tipo diferente, o `DataContractSerializer` importa um esquema com um elemento do tipo `xs:anyType` no tipo base e declarações de tipo derivado. O nome do tipo original é preservado na `xs:annotations/xs:appInfo/ser:ActualType/@Name`.  
  
 Ambas as variações podem levar a um esquema com um modelo de conteúdo ambíguo, depende da ordem de membros do respectivos dados.  
  
## <a name="typeprimitive-mapping"></a>Mapeamento de tipo/primitivo  
 O `DataContractSerializer` usa o seguinte mapeamento para tipos primitivos do esquema XML.  
  
|Tipo XSD|Tipo .NET|  
|--------------|---------------|  
|`anyType`|<xref:System.Object>.|  
|`anySimpleType`|<xref:System.String>.|  
|`duration`|<xref:System.TimeSpan>.|  
|`dateTime`|<xref:System.DateTime>.|  
|`dateTimeOffset`|<xref:System.DateTime>e <xref:System.TimeSpan> para o deslocamento. Consulte abaixo de serialização de DateTimeOffset.|  
|`time`|<xref:System.String>.|  
|`date`|<xref:System.String>.|  
|`gYearMonth`|<xref:System.String>.|  
|`gYear`|<xref:System.String>.|  
|`gMonthDay`|<xref:System.String>.|  
|`gDay`|<xref:System.String>.|  
|`gMonth`|<xref:System.String>.|  
|`boolean`|<xref:System.Boolean>|  
|`base64Binary`|Matriz <xref:System.Byte>.|  
|`hexBinary`|<xref:System.String>.|  
|`float`|<xref:System.Single>.|  
|`double`|<xref:System.Double>.|  
|`anyURI`|<xref:System.Uri>.|  
|`QName`|<xref:System.Xml.XmlQualifiedName>.|  
|`string`|<xref:System.String>.|  
|`normalizedString`|<xref:System.String>.|  
|`token`|<xref:System.String>.|  
|`language`|<xref:System.String>.|  
|`Name`|<xref:System.String>.|  
|`NCName`|<xref:System.String>.|  
|`ID`|<xref:System.String>.|  
|`IDREF`|<xref:System.String>.|  
|`IDREFS`|<xref:System.String>.|  
|`ENTITY`|<xref:System.String>.|  
|`ENTITIES`|<xref:System.String>.|  
|`NMTOKEN`|<xref:System.String>.|  
|`NMTOKENS`|<xref:System.String>.|  
|`decimal`|<xref:System.Decimal>.|  
|`integer`|<xref:System.Int64>.|  
|`nonPositiveInteger`|<xref:System.Int64>.|  
|`negativeInteger`|<xref:System.Int64>.|  
|`long`|<xref:System.Int64>.|  
|`int`|<xref:System.Int32>.|  
|`short`|<xref:System.Int16>.|  
|`Byte`|<xref:System.SByte>.|  
|`nonNegativeInteger`|<xref:System.Int64>.|  
|`unsignedLong`|<xref:System.UInt64>.|  
|`unsignedInt`|<xref:System.UInt32>.|  
|`unsignedShort`|<xref:System.UInt16>.|  
|`unsignedByte`|<xref:System.Byte>.|  
|`positiveInteger`|<xref:System.Int64>.|  
  
## <a name="iserializable-types-mapping"></a>Mapeamento de tipos iSerializable  
 Em [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0, `ISerializable` foi introduzida como um mecanismo geral para serializar objetos para transferência de dados ou de persistência. Existem várias [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos que implementam `ISerializable` e que podem ser transmitidos entre aplicativos. `DataContractSerializer`Naturalmente, fornece suporte para `ISerializable` classes. O `DataContractSerializer` mapeia `ISerializable` tipos de esquema de implementação que diferem somente por QName (nome qualificado) do tipo e efetivamente são coleções de propriedade. Por exemplo, o `DataContractSerializer` mapeia <xref:System.Exception> para o seguinte tipo XSD no namespace http://schemas.datacontract.org/2004/07/System.  
  
```xml  
<xs:complexType name="Exception">  
 <xs:sequence>  
  <xs:any minOccurs="0" maxOccurs="unbounded"   
      namespace="##local" processContents="skip"/>  
 </xs:sequence>  
 <xs:attribute ref="ser:FactoryType"/>  
</xs:complexType>  
```  
  
 O atributo opcional `ser:FactoryType` declarado na serialização de contrato de dados de esquema faz referência a uma classe de fábrica que pode desserializar o tipo. A classe de fábrica deve ser parte da coleção de tipos conhecidos a `DataContractSerializer` instância que está sendo usado. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="datacontract-serialization-schema"></a>Esquema de serialização de DataContract  
 Um número de esquemas exportados pelo `DataContractSerializer` usar tipos de elementos e atributos de um namespace de serialização de contrato de dados especial:  
  
 http://schemas.microsoft.com/2003/10/Serialization  
  
 A seguir está uma declaração de esquema de serialização de contrato de dados completa.  
  
```xml  
<xs:schema attributeFormDefault="qualified"          
   elementFormDefault="qualified"        
   targetNamespace =   
    "http://schemas.microsoft.com/2003/10/Serialization/"   
   xmlns:xs="http://www.w3.org/2001/XMLSchema"        
   xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/">  
  
 <!-- Top-level elements for primitive types. -->  
 <xs:element name="anyType" nillable="true" type="xs:anyType"/>  
 <xs:element name="anyURI" nillable="true" type="xs:anyURI"/>  
 <xs:element name="base64Binary"  
       nillable="true" type="xs:base64Binary"/>  
 <xs:element name="boolean" nillable="true" type="xs:boolean"/>  
 <xs:element name="byte" nillable="true" type="xs:byte"/>  
 <xs:element name="dateTime" nillable="true" type="xs:dateTime"/>  
 <xs:element name="decimal" nillable="true" type="xs:decimal"/>  
 <xs:element name="double" nillable="true" type="xs:double"/>  
 <xs:element name="float" nillable="true" type="xs:float"/>  
 <xs:element name="int" nillable="true" type="xs:int"/>  
 <xs:element name="long" nillable="true" type="xs:long"/>  
 <xs:element name="QName" nillable="true" type="xs:QName"/>  
 <xs:element name="short" nillable="true" type="xs:short"/>  
 <xs:element name="string" nillable="true" type="xs:string"/>  
 <xs:element name="unsignedByte"  
       nillable="true" type="xs:unsignedByte"/>  
 <xs:element name="unsignedInt"  
       nillable="true" type="xs:unsignedInt"/>  
 <xs:element name="unsignedLong"  
       nillable="true" type="xs:unsignedLong"/>  
 <xs:element name="unsignedShort"  
       nillable="true" type="xs:unsignedShort"/>  
  
 <!-- Primitive types introduced for certain .NET simple types. -->  
 <xs:element name="char" nillable="true" type="tns:char"/>  
 <xs:simpleType name="char">  
  <xs:restriction base="xs:int"/>  
 </xs:simpleType>  
  
 <!-- xs:duration is restricted to an ordered value space,  
    to map to System.TimeSpan -->  
 <xs:element name="duration" nillable="true" type="tns:duration"/>  
 <xs:simpleType name="duration">  
  <xs:restriction base="xs:duration">  
   <xs:pattern   
     value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?"/>  
   <xs:minInclusive value="-P10675199DT2H48M5.4775808S"/>  
   <xs:maxInclusive value="P10675199DT2H48M5.4775807S"/>  
  </xs:restriction>  
 </xs:simpleType>  
  
 <xs:element name="guid" nillable="true" type="tns:guid"/>  
 <xs:simpleType name="guid">  
  <xs:restriction base="xs:string">  
   <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}"/>  
  </xs:restriction>  
 </xs:simpleType>  
  
 <!-- This is used for schemas exported from ISerializable type. -->  
 <xs:attribute name="FactoryType" type="xs:QName"/>  
</xs:schema>  
```  
  
 O exemplo a seguir deve ser observados:  
  
-   `ser:char`é introduzido para representar caracteres Unicode do tipo <xref:System.Char>.  
  
-   O `valuespace` de `xs:duration` é reduzida a um conjunto ordenado para que ele pode ser mapeado para um <xref:System.TimeSpan>.  
  
-   `FactoryType`é usado em esquemas exportadas de tipos que são derivados de <xref:System.Runtime.Serialization.ISerializable>.  
  
## <a name="importing-non-datacontract-schemas"></a>Importando esquemas não DataContract  
 `DataContractSerializer`tem o `ImportXmlTypes` opção para permitir que a importação de esquemas que não está de acordo com o `DataContractSerializer` perfil XSD (consulte o <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> propriedade). Definir essa opção como `true` habilita a aceitação dos tipos de esquema não conformes e mapeando-os para a implementação a seguir, <xref:System.Xml.Serialization.IXmlSerializable> quebra automática de uma matriz de <xref:System.Xml.XmlNode> (somente o nome da classe difere).  
  
```  
[GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
[System.Xml.Serialization.XmlSchemaProviderAttribute("ExportSchema")]  
[System.Xml.Serialization.XmlRootAttribute(IsNullable=false)]  
public partial class Person : object, IXmlSerializable  
{    
  private XmlNode[] nodesField;    
  private static XmlQualifiedName typeName =   
new XmlQualifiedName("Person","http://Microsoft.ServiceModel.Samples");    
  public XmlNode[] Nodes  
  {  
    get {return this.nodesField;}  
    set {this.nodesField = value;}  
  }    
  public void ReadXml(XmlReader reader)  
  {  
    this.nodesField = XmlSerializableServices.ReadNodes(reader);  
  }    
  public void WriteXml(XmlWriter writer)  
  {  
    XmlSerializableServices.WriteNodes(writer, this.Nodes);  
  }    
  public System.Xml.Schema.XmlSchema GetSchema()  
  {  
    return null;  
  }    
  public static XmlQualifiedName ExportSchema(XmlSchemaSet schemas)  
  {  
    XmlSerializableServices.AddDefaultSchema(schemas, typeName);  
    return typeName;  
  }  
}  
```  
  
## <a name="datetimeoffset-serialization"></a>Serialização de DateTimeOffset  
 O <xref:System.DateTimeOffset> não é tratado como um tipo primitivo. Em vez disso, ele é serializado como um elemento complexo com duas partes. A primeira parte representa a data, hora e a segunda parte representa o deslocamento de data hora. Um exemplo de um valor DateTimeOffset serializado é mostrado no código a seguir.  
  
```xml  
<OffSet xmlns:a="http://schemas.datacontract.org/2004/07/System">  
  <DateTime i:type="b:dateTime" xmlns=""   
    xmlns:b="http://www.w3.org/2001/XMLSchema">2008-08-28T08:00:00    
  </DateTime>   
  <OffsetMinutes i:type="b:short" xmlns=""   
   xmlns:b="http://www.w3.org/2001/XMLSchema">-480  
   </OffsetMinutes>   
</OffSet>  
```  
  
 O esquema é da seguinte maneira.  
  
```xml  
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">  
   <xs:complexType name="DateTimeOffset">  
      <xs:sequence minOccurs="1" maxOccurs="1">  
         <xs:element name="DateTime" type="xs:dateTime"  
         minOccurs="1" maxOccurs="1" />  
         <xs:elementname="OffsetMinutes" type="xs:short"  
         minOccurs="1" maxOccurs="1" />  
      </xs:sequence>  
   </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
