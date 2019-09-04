---
title: Especificação do manifesto do provedor
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: 6b924f484e6635760d08d0eba9fb9436bdd8bc88
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248582"
---
# <a name="provider-manifest-specification"></a>Especificação do manifesto do provedor
Esta seção discute como um provedor de armazenamento de dados pode suportar os tipos e funções no armazenamento de dados.  
  
 Os serviços de entidade operam independentemente de um provedor específico de armazenamento de dados ainda permitir que que um provedor de dados defina explicitamente como modelos, os mapeamentos, e as consultas interagem com um armazenamento de dados subjacentes. Sem uma camada de abstração, os serviços de entidade podiam ser direcionados em um armazenamento de dados ou em um provedor de dados específico.  
  
 Tipos que suporta do provedor são suportados direta ou indiretamente por base de dados subjacente. Esses tipos não são necessariamente os tipos exatos de armazenamento, mas os tipos que o provedor usa para oferecer suporte [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Os tipos de provedor/armazenamento são descritos em termos de Modelo de Dados de Entidade (EDM).  
  
 O parâmetro e tipos de retorno para as funções suportados pelo armazenamento de dados são especificados em termos de EDM.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] e a necessidade de armazenamento de dados pode passar para frente e para trás dados em tipos conhecidos sem qualquer perda de dados ou truncamento.  
  
 O manifesto do provedor deve ser loadable por ferramentas em tempo de design sem ter que abrir uma conexão para o armazenamento de dados.  
  
 O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] diferencia maiúsculas de minúsculas, mas o armazenamento de dados subjacente pode não ser. Quando os artefatos de EDM (identificadores e nomes de tipo, por exemplo) são definidos e usados no manifesto, devem usar a maiúsculas de minúsculas [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] . Se os elementos do armazenamento de dados que podem ser maiúsculas de minúsculas aparecem no manifesto do provedor, essa caixa precisa ser mantidas no manifesto do provedor.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] requer um manifesto de provedor para todos os provedores de dados. Se você tentar usar um provedor que não tem um manifesto de provedor com o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], receberá um erro.  
  
 A tabela a seguir descreve os tipos de exceções que [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] jogaria quando ocorrerem exceções com a interação de provedor:  
  
|Problema|Exceção|  
|-----------|---------------|  
|O provedor não oferece suporte GetProviderManifest em DbProviderServices.|ProviderIncompatibleException|  
|Manifesto ausente do provedor: o provedor retorna `null` ao tentar recuperar o provedor de manifesto.|ProviderIncompatibleException|  
|Manifesto inválido do provedor: o provedor retorna XML válido para tentar recuperar o provedor de manifesto.|ProviderIncompatibleException|  
  
## <a name="scenarios"></a>Cenários  
 Um provedor deve oferecer suporte aos seguintes situações:  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a>Escrevendo um provedor com mapeamento simétrico de tipo  
 Você pode escrever um provedor para o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] local em que cada tipo de loja é mapeado para um único tipo EDM, independentemente da direção do mapeamento. Para um tipo de provedor que tenha o mapeamento muito simples que corresponde com um tipo de EDM, você pode usar uma solução simétrica porque o sistema de tipos é simples ou corresponde tipos de EDM.  
  
 Você pode usar a simplicidade do domínio e gerar um manifesto declarativo estática do provedor.  
  
 Você escreve um arquivo XML que tem duas seções:  
  
- Uma lista de tipos de provedor expressos em termos de “de EDM contrapartes” de um tipo ou uma função de armazenamento. Os tipos de Store têm tipos de EDM de correspondentes. Funções de Store têm correspondentes funções de EDM. Por exemplo, varchar é um tipo SQL Server mas o tipo correspondente de EDM é cadeia de caracteres.  
  
- Uma lista de funções suportadas pelo provedor onde o parâmetro e tipos de retorno são expressos em termos de EDM.  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a>Escrevendo um provedor com mapeamento assimétrico de tipo  
 Ao escrever um provedor de armazenamento de dados para [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], o mapeamento de tipo de EDM-à- provedor para qualquer tipo pode ser diferente de mapeamento de tipo de provedor-à- EDM. Por exemplo, EDM ilimitado PrimitiveTypeKind.String pode mapear a nvarchar (4000) no provedor, quando (4000) mapas nvarchar a EDM PrimitiveTypeKind.String (MaxLength=4000).  
  
 Você escreve um arquivo XML que tem duas seções:  
  
- Uma lista de tipos de provedor expressa em termos de EDM e define o mapeamento para ambas as direções: EDM para provedor e provedor-para-EDM.  
  
- Uma lista de funções suportadas pelo provedor onde o parâmetro e tipos de retorno são expressos em termos de EDM.  
  
## <a name="provider-manifest-discoverability"></a>Descoberta manifesto provedor  
 O manifesto é usado por vários serviços indiretamente componentes de entidade dos tipos (por exemplo ferramentas ou consulta) mas aproveitado mais diretamente por metadados com o uso do carregador de metadados do armazenamento de dados.  
  
 ![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")  
  
 No entanto, um provedor determinado pode suportar armazenamentos diferentes ou versões diferentes do mesmo armazenamento. Portanto, um provedor deve relatar um manifesto diferente para cada armazenamento de dados suportado.  
  
### <a name="provider-manifest-token"></a>Símbolo manifesto do provedor  
 Quando uma conexão de armazenamento de dados é aberta, o provedor pode consultar informações que retorna o manifesto direito. Isso pode não ser possível em situações onde off-line informações de conexão não está disponível ou quando não é possível conectar-se ao armazenamento. Identifica o manifesto usando o atributo `ProviderManifestToken` do elemento de `Schema` no arquivo de .ssdl. Não há nenhum formato exigido para este atributo; o provedor escolher informações mínima necessária identificar um manifesto sem abrir uma conexão para o armazenamento.  
  
 Por exemplo:  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a>Manifesto modelo de programação do provedor  
 Os provedores derivam de <xref:System.Data.Common.DbXmlEnabledProviderManifest>, que permite que especifiquem seus manifestos declarativamente. A ilustração a seguir mostra a hierarquia de classe de um provedor:  
  
 ![None](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")  
  
### <a name="discoverability-api"></a>Descoberta API  
 O manifesto do provedor é carregado pelo carregador de metadados de Store (StoreItemCollection), usando uma conexão de armazenamento de dados ou um token de manifesto do provedor.  
  
#### <a name="using-a-data-store-connection"></a>Usando uma conexão do armazenamento de dados  
 Quando a conexão do repositório de dados estiver disponível <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> , chame para retornar o token que é passado <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> para o método, <xref:System.Data.Common.DbProviderManifest>que retorna. Esse método delega para a implementação do provedor do `GetDbProviderManifestToken`.  
  
```csharp
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a>Usando um token de manifesto de provedor  
 Para o cenário off-line, o símbolo é escolhido da representação de SSDL. O SSDL permite que você especifique um ProviderManifestToken (consulte o [elemento de esquema (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) para obter mais informações). Por exemplo, se uma conexão não pode ser aberta, SSDL tem um token de manifesto de provedor que especifica informações sobre o manifesto.  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a>Esquema manifesto do provedor  
 O esquema de informações definido para cada provedor contém informações estáticas a ser consumida por metadados:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema elementFormDefault="qualified"  
   xmlns:xs="http://www.w3.org/2001/XMLSchema"  
   targetNamespace="http://schemas.microsoft.com/ado/2006/04/edm/providermanifest"  
   xmlns:pm="http://schemas.microsoft.com/ado/2006/04/edm/providermanifest">  
  
  <xs:element name="ProviderManifest">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Types" type="pm:TTypes" minOccurs="1" maxOccurs="1" />  
        <xs:element name="Functions" type="pm:TFunctions" minOccurs="0" maxOccurs="1"/>  
      </xs:sequence>  
      <xs:attribute name="Namespace" type="xs:string" use="required"/>  
    </xs:complexType>  
  </xs:element>  
  <xs:complexType name="TVersion">  
    <xs:attribute name="Major" type="xs:int" use="required" />  
    <xs:attribute name="Minor" type="xs:int" use="required" />  
    <xs:attribute name="Build" type="xs:int" use="required" />  
    <xs:attribute name="Revision" type="xs:int" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TIntegerFacetDescription">  
    <xs:attribute name="Minimum" type="xs:int" use="optional" />  
    <xs:attribute name="Maximum" type="xs:int" use="optional" />  
    <xs:attribute name="DefaultValue" type="xs:int" use="optional" />  
    <xs:attribute name="Constant" type="xs:boolean" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="TBooleanFacetDescription">  
    <xs:attribute name="DefaultValue" type="xs:boolean" use="optional" />  
    <xs:attribute name="Constant" type="xs:boolean" default="true" />  
  </xs:complexType>  
  
  <xs:complexType name="TDateTimeFacetDescription">  
    <xs:attribute name="Constant" type="xs:boolean" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="TFacetDescriptions">  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="Precision" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="Scale" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="MaxLength" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="Unicode" minOccurs="0" maxOccurs="1" type="pm:TBooleanFacetDescription"/>  
      <xs:element name="FixedLength" minOccurs="0" maxOccurs="1" type="pm:TBooleanFacetDescription"/>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:complexType name="TType">  
    <xs:sequence>  
      <xs:element name="FacetDescriptions" type="pm:TFacetDescriptions" minOccurs="0" maxOccurs="1"/>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required"/>  
    <xs:attribute name="PrimitiveTypeKind" type="pm:TPrimitiveTypeKind" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TTypes">  
    <xs:sequence>  
      <xs:element name="Type" type="pm:TType" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:attributeGroup name="TFacetAttribute">  
    <xs:attribute name="Precision" type="xs:int" use="optional"/>  
    <xs:attribute name="Scale" type="xs:int" use="optional"/>  
    <xs:attribute name="MaxLength" type="xs:int" use="optional"/>  
    <xs:attribute name="Unicode" type="xs:boolean" use="optional"/>  
    <xs:attribute name="FixedLength" type="xs:boolean" use="optional"/>  
  </xs:attributeGroup>  
  
  <xs:complexType name="TFunctionParameter">  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attributeGroup ref="pm:TFacetAttribute" />  
    <xs:attribute name="Mode" type="pm:TParameterDirection" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TReturnType">  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attributeGroup ref="pm:TFacetAttribute" />  
  </xs:complexType>  
  
  <xs:complexType name="TFunction">  
    <xs:choice minOccurs="0" maxOccurs ="unbounded">  
      <xs:element name ="ReturnType" type="pm:TReturnType" minOccurs="0" maxOccurs="1" />  
      <xs:element name="Parameter" type="pm:TFunctionParameter" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:choice>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Aggregate" type="xs:boolean" use="optional" />  
    <xs:attribute name="BuiltIn" type="xs:boolean" use="optional" />  
    <xs:attribute name="StoreFunctionName" type="xs:string" use="optional" />  
    <xs:attribute name="NiladicFunction" type="xs:boolean" use="optional" />  
    <xs:attribute name="ParameterTypeSemantics" type="pm:TParameterTypeSemantics" use="optional" default="AllowImplicitConversion" />  
  </xs:complexType>  
  
  <xs:complexType name="TFunctions">  
    <xs:sequence>  
      <xs:element name="Function" type="pm:TFunction" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:simpleType name="TPrimitiveTypeKind">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Binary"/>  
      <xs:enumeration value="Boolean"/>  
      <xs:enumeration value="Byte"/>  
      <xs:enumeration value="Decimal"/>  
      <xs:enumeration value="DateTime"/>  
      <xs:enumeration value="Time"/>  
      <xs:enumeration value="DateTimeOffset"/>          
      <xs:enumeration value="Double"/>  
      <xs:enumeration value="Guid"/>  
      <xs:enumeration value="Single"/>  
      <xs:enumeration value="SByte"/>  
      <xs:enumeration value="Int16"/>  
      <xs:enumeration value="Int32"/>  
      <xs:enumeration value="Int64"/>  
      <xs:enumeration value="String"/>  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In"/>  
      <xs:enumeration value="Out"/>  
      <xs:enumeration value="InOut"/>  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TParameterTypeSemantics">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="ExactMatchOnly" />  
      <xs:enumeration value="AllowImplicitPromotion" />  
      <xs:enumeration value="AllowImplicitConversion" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
#### <a name="types-node"></a>Nó de tipos  
 O nó de tipos no manifesto do provedor contém informações sobre os tipos que são suportados originalmente pelo armazenamento de dados ou do provedor.  
  
##### <a name="type-node"></a>Nó de tipo  
 Cada nó do tipo define um tipo de provedor em termos de EDM. O nó do tipo descrevem o nome do tipo do provedor, e informações acrescentadas ao tipo que mapeia o modelo e facetas para descrever o mapeamento de tipo.  
  
 Para expressar essas informações de tipo no manifesto do provedor, cada declaração de TypeInformation deve definir várias descrições de aspecto para cada tipo:  
  
|Nome do atributo|Tipo de dados|Necessária|Valor padrão|Descrição|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Nome|Cadeia de Caracteres|Sim|N/D|Nome do provedor específico de tipo de dados|  
|PrimitiveTypeKind|PrimitiveTypeKind|Sim|N/D|Nome do tipo de EDM|  
  
###### <a name="function-node"></a>Nó de função  
 Cada função define uma única função disponível através do provedor.  
  
|Nome do atributo|Tipo de dados|Necessária|Valor padrão|Descrição|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Nome|Cadeia de Caracteres|Sim|N/D|Identificador/nome de função|  
|Tipoderetorno|Cadeia de Caracteres|Não|Void|O tipo de retorno de EDM de função|  
|Agregado|Boolean|Não|False|Retifique se a função é uma função agregada|  
|Internos|Boolean|Não|verdadeiro|Retifique se a função é compilada no armazenamento de dados|  
|StoreFunctionName|Cadeia de Caracteres|Não|\<Nome >|Nome de função no armazenamento de dados.  Permite um nível de redirecionamento de nomes de função.|  
|NiladicFunction|Boolean|Não|False|Retifique se a função não requer parâmetros e é chamado sem nenhum parâmetro|  
|ParameterType<br /><br /> Semântica|ParameterSemantics|Não|AllowImplicit<br /><br /> Conversão|Escolha de como o pipeline de consulta deve manipular a substituição do tipo de parâmetro:<br /><br /> - ExactMatchOnly<br />-AllowImplicitPromotion<br />-AllowImplicitConversion|  
  
 **Nó de parâmetros**  
  
 Cada função tem uma coleção de um ou mais nós de parâmetro.  
  
|Nome do atributo|Tipo de dados|Necessária|Valor padrão|Descrição|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Nome|Cadeia de Caracteres|Sim|N/D|Identificador/nome do parâmetro.|  
|Tipo|Cadeia de Caracteres|Sim|N/D|O tipo de EDM de parâmetro.|  
|Modo|Parâmetro<br /><br /> Direction|Sim|N/D|Direção do parâmetro:<br /><br /> -in<br />-out<br />-InOut|  
  
##### <a name="namespace-attribute"></a>Atributo do namespace  
 Cada provedor de armazenamento de dados deve definir um namespace ou um grupo de namespaces para informações definida no manifesto. Este namespace pode ser usada em consultas Entity SQL para resolver nomes das funções e tipos. Por exemplo: SqlServer. O namespace deve ser diferente de namespace canônica, EDM, definido por serviços de entidade para que as funções padrão são suportadas por Entity consultas SQL.  
  
## <a name="see-also"></a>Consulte também

- [Escrevendo um Provedor de Dados do Entity Framework](writing-an-ef-data-provider.md)
