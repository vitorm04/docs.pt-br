---
title: Ferramenta Contract-First
ms.date: 03/30/2017
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
ms.openlocfilehash: 86ef109425a75e46e056447f4f40df36aa332293
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48261609"
---
# <a name="contract-first-tool"></a>Ferramenta Contract-First
Contratos de serviço geralmente precisam ser criados a partir de serviços existentes. No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], classes de contrato de dados podem ser criadas automaticamente, de serviços existentes usando a ferramenta de primeiro contrato. Para usar a ferramenta de primeiro contrato, o arquivo de definição de esquema XML (XSD) deve ser baixado localmente; a ferramenta não é possível importar os contratos de dados remotos por meio de HTTP.

 A ferramenta de primeiro contrato está integrada ao Visual Studio 2012 como uma tarefa de build. Os arquivos de código gerados pela tarefa de build são criados toda vez que o projeto é compilado, para que o projeto pode adotar, com facilidade as alterações no contrato de serviço subjacente.

 Tipos de esquema que a ferramenta de primeiro contrato pode importar incluem o seguinte:

```xml
<xsd:complexType>
<xsd:simpleType>
```

 Tipos simples não serão gerados se eles são primitivos, como `Int16` ou `String`; complexos tipos não serão gerados se eles forem do tipo `Collection`. Tipos também não serão gerados se fizerem parte de outro `xsd:complexType`. Nesses casos, os tipos serão referenciados para tipos existentes no projeto em vez disso.

## <a name="adding-a-data-contract-to-a-project"></a>Adicionando um contrato de dados a um projeto
 Antes de pode usar a ferramenta de primeiro contrato, o contrato de serviço (XSD) deve ser adicionado ao projeto. Para os fins desta visão geral, o seguinte contrato será usado para ilustrar as funções de primeiro contrato. Essa definição de serviço é um pequeno subconjunto de contrato de serviço usado pela API de pesquisa do Bing.

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema id="ServiceSchema"
    targetNamespace="http://tempuri.org/ServiceSchema.xsd"
    elementFormDefault="qualified"
    xmlns="http://tempuri.org/ServiceSchema.xsd"
    xmlns:mstns="http://tempuri.org/ServiceSchema.xsd"
    xmlns:xs="http://www.w3.org/2001/XMLSchema"
>
  <xs:complexType name="SearchRequest">
    <xs:sequence>
      <xs:element minOccurs="0" maxOccurs="1" name="Version" type="xs:string" default="2.2" />
      <xs:element minOccurs="0" maxOccurs="1" name="Market" type="xs:string" />
      <xs:element minOccurs="0" maxOccurs="1" name="UILanguage" type="xs:string" />
      <xs:element minOccurs="1" maxOccurs="1" name="Query" type="xs:string" />
      <xs:element minOccurs="1" maxOccurs="1" name="AppId" type="xs:string" />
      <xs:element minOccurs="0" maxOccurs="1" name="Latitude" type="xs:double" />
      <xs:element minOccurs="0" maxOccurs="1" name="Longitude" type="xs:double" />
      <xs:element minOccurs="0" maxOccurs="1" name="Radius" type="xs:double" />
    </xs:sequence>
  </xs:complexType>
  <xs:simpleType name="WebSearchOption">
    <xs:restriction base="xs:string">
      <xs:enumeration value="DisableHostCollapsing" />
      <xs:enumeration value="DisableQueryAlterations" />
    </xs:restriction>
  </xs:simpleType>
</xs:schema>
```

 Para adicionar o contrato de serviço acima para o projeto, clique com botão direito no projeto e selecione **adicionar novo...** . Selecione a definição de esquema no painel WCF da caixa de diálogo modelos e nomeie o novo arquivo SampleContract.xsd. Copie e cole o código acima para o modo de exibição de código do novo arquivo.

## <a name="configuring-contract-first-options"></a>Configurando as opções de primeiro contrato
 Opções de primeiro contrato podem ser configuradas no menu de propriedades de um projeto do WCF. Para habilitar o desenvolvimento contratar primeiro, selecione a **habilitar XSD como linguagem de definição de tipo** caixa de seleção na página de WCF da janela Propriedades do projeto.

 ![Contrato mostrando opções de projeto do WCF&#45;primeira](../../../docs/framework/wcf/media/contractfirstoptions.png "ContractFirstOptions")

 Para configurar propriedades avançadas, clique no botão Avançado.

 ![Advanced contrato&#45;propriedades do primeiro](../../../docs/framework/wcf/media/contractfirstadvanced.png "ContractFirstAdvanced")

 As seguintes configurações avançadas podem ser configuradas para a geração de código de contratos. As configurações só podem ser configuradas para todos os arquivos no projeto; as configurações não podem ser configuradas para arquivos individuais no momento.

-   **Modo de serializador**: essa configuração determina qual serializador é usado para ler arquivos de contrato de serviço. Quando **XML Serializer** for selecionada, o **tipos de coleção** e **reutilizar tipos** opções serão desabilitadas. Essas opções se aplicam somente para o **serializador de contrato de dados**.

-   **Reutilizar os tipos**: essa configuração especifica quais bibliotecas são usadas para reutilização de tipo. Essa configuração se aplica somente se **modo de serializador** é definido como **serializador de contrato de dados**.

-   **Tipo de coleção**: essa configuração especifica o tipo totalmente qualificado ou qualificado do assembly a ser usado para o tipo de dados da coleção. Essa configuração se aplica somente se **modo de serializador** é definido como **serializador de contrato de dados**.

-   **Tipo de dicionário**: essa configuração especifica o tipo totalmente qualificado ou qualificado do assembly a ser usado para o tipo de dados do dicionário.

-   **EnableDataBinding**: essa configuração especifica se deve implementar o <xref:System.ComponentModel.INotifyPropertyChanged> interface em todos os tipos de dados para implementar a vinculação de dados.

-   **ExcludedTypes**: essa configuração especifica a lista de tipos totalmente qualificado ou qualificado do assembly a ser excluído dos assemblies referenciados. Essa configuração se aplica somente se **modo de serializador** é definido como **serializador de contrato de dados**.

-   **GenerateInternalTypes**: essa configuração especifica se deve gerar classes que são marcadas como internas. Essa configuração se aplica somente se **modo de serializador** é definido como **serializador de contrato de dados**.

-   **GenerateSerializableTypes**: essa configuração especifica se deve gerar classes com o <xref:System.SerializableAttribute> atributo. Essa configuração se aplica somente se **modo de serializador** é definido como **serializador de contrato de dados**.

-   **ImportXMLTypes**: essa configuração especifica se deve configurar o serializador de contrato de dados para aplicar a <xref:System.SerializableAttribute> atributo às classes sem o <xref:System.Runtime.Serialization.DataContractAttribute> atributo.  Essa configuração se aplica somente se **modo de serializador** é definido como **serializador de contrato de dados**.

-   **SupportFx35TypedDataSets**: essa configuração especifica se fornecer funcionalidade adicional para conjuntos de dados tipados criados para o .net Framework 3.5. Quando **modo de serializador** é definido como **serializador XML**, o <xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35> extensão será adicionada para o importador de esquema XML quando esse valor é definido como True. Quando **modo serializador** é definido como **serializador de contrato de dados**, o tipo <xref:System.DateTimeOffset> serão excluídos das referências quando esse valor é definido como False, para que um <xref:System.DateTimeOffset> é gerado sempre para versões mais antigas do framework.

-   **InputXsdFiles**: essa configuração especifica a lista de arquivos de entrada. Cada arquivo deve conter um esquema XML válido.

-   **Linguagem**: essa configuração especifica a linguagem do código de contrato gerado. A configuração deve ser reconhecível por <xref:System.CodeDom.Compiler.CodeDomProvider>.

-   **NamespaceMappings**: essa configuração especifica os mapeamentos de Namespaces de destino de XSD para namespaces de CLR. Cada mapeamento deve usar o seguinte formato:

    ```xml
    "<Schema Namespace>, <CLR Namespace>"
    ```

     O serializador XML aceita apenas um mapeamento no formato a seguir:

    ```xml
    "*, <CLR Namespace>"
    ```

-   **OutputDirectory**: essa configuração especifica o diretório onde os arquivos de código serão gerados.

 As configurações serão usadas para gerar tipos de contrato de serviço de arquivos de contrato de serviço quando o projeto é compilado.

## <a name="using-contract-first-development"></a>Usando o desenvolvimento de primeiro contrato
 Depois de adicionar o contrato de serviço ao projeto e confirmando as configurações de compilação, compile o projeto pressionando **F6**. Os tipos definidos no contrato de serviço estará disponíveis para uso no projeto.

 Para usar os tipos definidos no contrato de serviço, adicione uma referência ao `ContractTypes` sob o namespace atual:

```csharp
using MyProjectNamespace.ContractTypes;
```

 Os tipos definidos no contrato de serviço, em seguida, poderá ser resolvidos no projeto, conforme mostrado abaixo.

 ![Usando tipos derivados de um contrato de serviço](../../../docs/framework/wcf/media/contractfirsttypes.png "ContractFirstTypes")

 Os tipos gerados pela ferramenta são criados no arquivo GeneratedXSDTypes.cs. O arquivo é criado na \<diretório do projeto > /obj/\<configuração de compilação > diretório /XSDGeneratedCode/ por padrão. O esquema de exemplo no início deste tópico é convertido da seguinte maneira:

```csharp
//------------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by a tool.
//     Runtime Version:4.0.30319.17330
//
//     Changes to this file may cause incorrect behavior and will be lost if
//     the code is regenerated.
// </auto-generated>
//------------------------------------------------------------------------------

namespace TestXSD3.ContractTypes
{
    using System.Xml.Serialization;

    /// <remarks/>
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]
    [System.SerializableAttribute()]
    [System.Diagnostics.DebuggerStepThroughAttribute()]
    [System.ComponentModel.DesignerCategoryAttribute("code")]
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=true)]
    public partial class SearchRequest
    {

        private string versionField;

        private string marketField;

        private string uILanguageField;

        private string queryField;

        private string appIdField;

        private double latitudeField;

        private bool latitudeFieldSpecified;

        private double longitudeField;

        private bool longitudeFieldSpecified;

        private double radiusField;

        private bool radiusFieldSpecified;

        public SearchRequest()
        {
            this.versionField = "2.2";
        }

        /// <remarks/>
        [System.ComponentModel.DefaultValueAttribute("2.2")]
        public string Version
        {
            get
            {
                return this.versionField;
            }
            set
            {
                this.versionField = value;
            }
        }

        /// <remarks/>
        public string Market
        {
            get
            {
                return this.marketField;
            }
            set
            {
                this.marketField = value;
            }
        }

        /// <remarks/>
        public string UILanguage
        {
            get
            {
                return this.uILanguageField;
            }
            set
            {
                this.uILanguageField = value;
            }
        }

        /// <remarks/>
        public string Query
        {
            get
            {
                return this.queryField;
            }
            set
            {
                this.queryField = value;
            }
        }

        /// <remarks/>
        public string AppId
        {
            get
            {
                return this.appIdField;
            }
            set
            {
                this.appIdField = value;
            }
        }

        /// <remarks/>
        public double Latitude
        {
            get
            {
                return this.latitudeField;
            }
            set
            {
                this.latitudeField = value;
            }
        }

        /// <remarks/>
        [System.Xml.Serialization.XmlIgnoreAttribute()]
        public bool LatitudeSpecified
        {
            get
            {
                return this.latitudeFieldSpecified;
            }
            set
            {
                this.latitudeFieldSpecified = value;
            }
        }

        /// <remarks/>
        public double Longitude
        {
            get
            {
                return this.longitudeField;
            }
            set
            {
                this.longitudeField = value;
            }
        }

        /// <remarks/>
        [System.Xml.Serialization.XmlIgnoreAttribute()]
        public bool LongitudeSpecified
        {
            get
            {
                return this.longitudeFieldSpecified;
            }
            set
            {
                this.longitudeFieldSpecified = value;
            }
        }

        /// <remarks/>
        public double Radius
        {
            get
            {
                return this.radiusField;
            }
            set
            {
                this.radiusField = value;
            }
        }

        /// <remarks/>
        [System.Xml.Serialization.XmlIgnoreAttribute()]
        public bool RadiusSpecified
        {
            get
            {
                return this.radiusFieldSpecified;
            }
            set
            {
                this.radiusFieldSpecified = value;
            }
        }
    }

    /// <remarks/>
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]
    [System.SerializableAttribute()]
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=false)]
    public enum WebSearchOption
    {

        /// <remarks/>
        DisableHostCollapsing,

        /// <remarks/>
        DisableQueryAlterations,
    }
}
```

## <a name="errors-and-warnings"></a>Erros e avisos
 Erros e avisos encontrados ao analisar o esquema XSD serão exibido como erros e avisos de compilação.

## <a name="interface-inheritance"></a>Herança da interface
 Não é possível usar a herança de interface com o desenvolvimento contratar primeiro; Isso é consistente com a maneira como as interfaces se comportam em outras operações. Para usar uma interface que herda de uma interface de base, use dois pontos de extremidade separados. O primeiro ponto de extremidade usa o contrato herdado e o segundo ponto de extremidade implementa a interface base.
